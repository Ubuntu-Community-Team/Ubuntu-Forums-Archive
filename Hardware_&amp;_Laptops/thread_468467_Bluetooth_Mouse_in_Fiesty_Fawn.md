---
title: "Bluetooth Mouse in Fiesty Fawn"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by gotmonkey on 2007-06-08
I just bought a Logitech V270 Bluetooth mouse for my IBM T42 Laptop with bluetooth.  I installed all of the bluetooth applications that I saw listed on other threads

bluez-gnome
bluez-pin
bluez-utils
gnome-bluetooth
python-blue

Using a guide on [[COLOR="Blue"]linuxquestions: [/COLOR]]("http://http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu") I was able to get my mouse connected to the laptop. 

set mouse in discovery mode
$hcitool scan
Scanning ...
        00:07:61:67:B8:2C       Bluetooth Travel Mouse
$sudo hidd --connect 00:07:61:67:B8:2C 

Now that my new bluetooth mouse is connected, I started looking at the guide to make this a permanent thing. The guide said to do this: 

$gksu gedit /etc/default/bluetooth

find the lines: 
HIDD_ENABLED=0
change to 
HIDD_ENABLED=1

and just below it:
HIDD_OPTIONS="-i 00:07:61:67:B8:2C --server"

***EDITED***
[COLOR="Red"]HIDD_OPTIONS="--connect 00:07:61:67:B8:2C --server"

This worked, my mouse now runs at start
[/COLOR]
***END EDIT***

Save and Close
Reboot system

Here is where it gets interesting. My lappy uses FN+F5 to enable both the wireless connection and the bluetooth. When I have both wireless and bluetooth enabled, on boot the network manager asks for my password for the wireless connection, yet doesn't connect. I have to select my wireless to connect. The other thing is that the bluetooth mouse doesn't connect. I have to run the command for $sudo hidd --connect 00:07:61:67:B8:2C to connect my mouse. 

Anybody have any thoughts on this? I am liking the bt mouse and I like the fact that it doesn't take up a usb ports.

---

### Post by gotmonkey on 2007-06-10
so far, I haven't been able to get the mouse to run at boot. So I decided to make a on-demand launcher. 

I created a launcher on the desktop. Set to open with terminal, gave it the command of
sudo hidd --connect 00:07:61:67:B8:2C

push the connect button on the mouse, open up the launcher, insert password, mouse connected.

It is seeming to work fine as an click on-demand device. Not the perfect solution to my desires, but will work until I find a better solution. I still need to find a way to control the speed, it is a little fast moving at the moment.

---

### Post by IntuitiveNipple on 2007-06-18
A note of thanks for this HowTo. As a result of reading it I bought the same model on ebay and have just installed it with Feisty. It is working after 2 commands and one edit - left, right, and middle buttons and scroll-wheel:)

---

### Post by gotmonkey on 2008-07-01
> **gotmonkey said:**
> I just bought a Logitech V270 Bluetooth mouse for my IBM T42 Laptop with bluetooth.  I installed all of the bluetooth applications that I saw listed on other threads

bluez-gnome
bluez-pin
bluez-utils
gnome-bluetooth
python-blue

Using a guide on [[COLOR="Blue"]linuxquestions: [/COLOR]]("http://http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu") I was able to get my mouse connected to the laptop. 

set mouse in discovery mode
$hcitool scan
Scanning ...
        00:07:61:67:B8:2C       Bluetooth Travel Mouse
$sudo hidd --connect 00:07:61:67:B8:2C 

Now that my new bluetooth mouse is connected, I started looking at the guide to make this a permanent thing. The guide said to do this: 

$gksu gedit /etc/default/bluetooth

find the lines: 
HIDD_ENABLED=0
change to 
HIDD_ENABLED=1

and just below it:
HIDD_OPTIONS="-i 00:07:61:67:B8:2C --server"

***EDITED***
[COLOR="Red"]HIDD_OPTIONS="--connect 00:07:61:67:B8:2C --server"

This worked, my mouse now runs at start
[/COLOR]
***END EDIT***

Save and Close
Reboot system

Here is where it gets interesting. My lappy uses FN+F5 to enable both the wireless connection and the bluetooth. When I have both wireless and bluetooth enabled, on boot the network manager asks for my password for the wireless connection, yet doesn't connect. I have to select my wireless to connect. The other thing is that the bluetooth mouse doesn't connect. I have to run the command for $sudo hidd --connect 00:07:61:67:B8:2C to connect my mouse. 

Anybody have any thoughts on this? I am liking the bt mouse and I like the fact that it doesn't take up a usb ports.

For those that may be interested, this works on Linux Mint 5 (Elyssa) which is based on hardy heron.

---

### Post by TRAFFICBLOWS on 2008-07-22
wow i couldn't get my Bluetooth Microsoft Mouse Laser Mouse 8000 working at all until reading this thread!  Thank you thank you!

(Yes it does work on Linux Mint 5! ;))

---

