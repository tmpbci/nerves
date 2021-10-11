# Nerves

A termeal version with neopixel led strip on raspberry pi (Raspberry Pi 1 is fine).

Color depends on port number of sniffed packets.

Available modes :

* 'scapy'   : listen to local network interface
* 'rainbow' : rainbow animation
* 'remote'	: use sudo termspy.py to listen on a remote computer and send to nerves for display

Default port websocket server : 8081

# Hardware

Neopixel strip (3 wires : 5V,GND,IN). 
Raspberry pi connections :

* Neopixel GPIO D18 #(-> pin 12)
* GND     pin 9
* 5 V     pin 4

Physical buttons :

* Func button : GPIO 23 (-> pin 16) / GND (-> pin 14)
* Down button : GPIO 24 (-> pin 18) / GND (-> pin 20)


# Control

2 physical buttons and a webpage : browse to pi address.

Webserver is NOT included : choose your webserver, edit config.js (to your pi webadress) and copy www directory. 



# Install

sudo apt install python3-pip

sudo pip3 install rpi_ws281x adafruit-circuitpython-neopixel

sudo python3 -m pip install --force-reinstall adafruit-blinka

sudo pip3 install scapy

To allow automatic shutdown :

sudo nano /etc/sudoers

add : 

pi raspberrypi =NOPASSWD: /usr/bin/systemctl poweroff


# Autorun

To autorun nerves at boot time, i.e a supervisor conf is given. After sudo apt install supervisor


sudo cp /home/pi/nerves/autorun.conf /etc/supervisor/conf.d/

sudo supervisorctl reload



# Based on :

* https://www.instructables.com/Fiber-Optic-LED-Lamp/
* https://github.com/loloster/termeal
* https://github.com/s0r00t/sniffeal
