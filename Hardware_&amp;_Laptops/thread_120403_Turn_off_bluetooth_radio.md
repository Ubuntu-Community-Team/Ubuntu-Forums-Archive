---
title: "Turn off bluetooth radio"
date: 2006-01-21
forum: Hardware &amp; Laptops
---

### Post by akniss on 2006-01-21
Is there a way in Ubuntu that I can turn the bluetooth radio off on my Dell 600m laptop?  Using the Fn+F2 will turn off both the BT and WiFi, which is good when I don't need to be online.  However, I don't see any reason why I should have to have the BT eating up battery while I'm using my Wireless card.  Can this be done?

---

### Post by PMO6022 on 2006-01-21
Try ```
sudo /etc/init.d/bluez-utils stop
```

---

### Post by akniss on 2006-01-21
[QUOTE=PMO6022]Try ```
sudo /etc/init.d/bluez-utils stop
```[/QUOTE]

That command gives me the following output:

```
akniss@Dell_Laptop:~$ sudo /etc/init.d/bluez-utils stop
Password:
 * Stopping Bluetooth services...  sdpd hcid                                                               [ ok ]
akniss@Dell_Laptop:~$

```

but the BT light on my laptop is still on.  I assume that we shut off the BT software utilities, but not the hardware radio.  Is there a utility that anyone knows of that will allow me to do this?

---

### Post by akniss on 2006-01-22
Thought I'd give this a BUMP now that the site is back up...

---

### Post by akniss on 2006-01-24
any ideas? anyone?

---

### Post by Horndog on 2006-01-24
A wild guess would be to turn BT off in the bios.

---

### Post by akniss on 2006-01-24
[QUOTE=Horndog]A wild guess would be to turn BT off in the bios.[/QUOTE]

I would like to be able to turn it on/off in Ubuntu.  If I turn it off in the bios, I can't use it to exchange files without booting into the bios, turning it back on, then booting back into ubuntu.  Not very practical.  I'm hoping for something like I have in Windows: right-click on the system tray icon, choose turn off radio.  I realize it probably won't be that easy, but i would be happy to enter a command at the terminal to turn it on/off if it will save me battery while i'm not plugged in.

---

### Post by akniss on 2006-01-26
could anyone point me to another forum where I might be able to get this info?

---

### Post by tom.lil.macca on 2006-01-27
Hey same laptop.. And same question that light is driving me crazy. I have tried to disable is in terminal with 

sudo /etc/init.d/bluez-utils stop

and got

maczor@ubuntu:~$ sudo /etc/init.d/bluez-utils stop
Password:
 * Stopping Bluetooth services...  sdpd hcid                                                               [ ok ]
maczor@ubuntu:~$

which is the same that you got.. Have you found an answer yet.. And if not do you know any forums that have good knowlege of Ubuntu + Dell Hardware [Inspiron 600m]

Thanks.

tEEjAY

---

### Post by akniss on 2006-01-27
[QUOTE=tom.lil.macca]Hey same laptop.. And same question that light is driving me crazy. I have tried to disable is in terminal with 

sudo /etc/init.d/bluez-utils stop

and got

maczor@ubuntu:~$ sudo /etc/init.d/bluez-utils stop
Password:
 * Stopping Bluetooth services...  sdpd hcid                                                               [ ok ]
maczor@ubuntu:~$

which is the same that you got.. Have you found an answer yet.. And if not do you know any forums that have good knowlege of Ubuntu + Dell Hardware [Inspiron 600m]

Thanks.

tEEjAY[/QUOTE]

I'm still looking... I can use the commands
```
sudo hciconfig hciX down
```
and
```
sudo hciconfig hciX noscan
```
which in theory should deactivate and turn off scanning by the radio, respectively.  After doing so, just typing 
```
hciconfig
```
gives me the following output:
hci0:   Type: USB
        BD Address: 00:10:C6:C8:08:24 ACL MTU: 192:8 SCO MTU: 64:8
        DOWN
        RX bytes:123 acl:0 sco:0 events:16 errors:0
        TX bytes:313 acl:0 sco:0 commands:15 errors:0

Which to me says that the radio should be DOWN, but that damn blue light is still on and I can't tell if I'm saving any battery life or not.

---

### Post by Tulsapoke on 2007-10-27
Did anyone ever figure out how to deactivate the Bluetooth on Dell laptops by now?  That blue light on my laptop is about the only thing left that Ubuntu can't control that Windows can.

---

### Post by luistorresmx on 2007-10-27
hi pal, same problem here...

I dont know why nobody has an answer to this when it is so simple to do in windows.

By the way, I want it turned on. I have it enabled on my bios, but it is kinda in sleep mode or something (the status you want to get) but ubuntu can't wake it up!


If you find a solution please post it. Ill do the same

---

### Post by #Reistlehr- on 2007-10-27
i turned my bluetooth off since i never used it. It was kind of a pain.

lsmod |grep bluetooth

blacklist the listed modules

System -> Administration -> Services, uncheck the bluetooth box.

Restart. Worked for me, although it still freaking loads part of the layer, which is no offense to anyone, retarted.

---

### Post by Sevmpe on 2007-10-27
Hi,

As suggested in lesswatts.org the way to turn bluetooth off is to use these two commands:
```

sudo hciconfig hci0 down
sudo rmmod hci_usb
```
[Link to source]("http://www.lesswatts.org/tips/wireless.php#bt")

---

### Post by mra122 on 2007-11-10
Thanks!!!!
It worked!!!!!!!!!!!!!!! You made my day    :)

> **Sevmpe said:**
> Hi,

As suggested in lesswatts.org the way to turn bluetooth off is to use these two commands:
```

sudo hciconfig hci0 down
sudo rmmod hci_usb
```
[Link to source]("http://www.lesswatts.org/tips/wireless.php#bt")

---

### Post by steven0451 on 2007-11-17
> **Sevmpe said:**
> Hi,

As suggested in lesswatts.org the way to turn bluetooth off is to use these two commands:
```

sudo hciconfig hci0 down
sudo rmmod hci_usb
```
[Link to source]("http://www.lesswatts.org/tips/wireless.php#bt")

This is my first post on the forum so I figured I'd make it helpful. :)

Turning off bluetooth worked for my Compaq tc4200 tablet too, then I wanted to turn bluetooth back on so I found this command after a while of searching:

```
sudo modprobe hci_usb reset=1
```

Hope this helps.

---

### Post by sayantandas on 2008-06-30
> **steven0451 said:**
> This is my first post on the forum so I figured I'd make it helpful. :)

Turning off bluetooth worked for my Compaq tc4200 tablet too, then I wanted to turn bluetooth back on so I found this command after a while of searching:

```
sudo modprobe hci_usb reset=1
```

Hope this helps.

hi all,

thanks for the lovely codes to turn-off/turn-on the bluetooth radio.
well, i've collected a few codes and made a small bash script which will help u guys to turn on/off bluetooth on the laptop with the help of just a double click.

here's the code:
```

#!/bin/bash
if ps -A | grep -c bluetoothd-serv
then 
gksudo /etc/init.d/bluetooth stop 
sudo hciconfig hci0 down
sudo rmmod hci_usb
else
sudo modprobe hci_usb reset=1
gksudo /etc/init.d/bluetooth start 
fi

```


copy and paste this code by making a shell script. give it executable permission. name it something like '*bluetooth_toggle.sh*' put it in the /bin folder, make a shortcut to ur desktop .  Double click on it, select run, and thats it. u can toggle the bluetooth.:guitar:

PS: i have tested it on my Dell I6400

---

