---
title: "HOW TO: ADS Technologies &quot;InstantFM&quot; (a.k.a. RDX-155)"
date: 2012-05-30
forum: Hardware
---

### Post by s4brains on 2012-05-30
Greetings: 
 
I spend a significant amount of time using Windoze computers at work.  It was at work that I grew fond of a USB FM radio device manufactured by ADS Technologies called InstantFM (or RDX-155). 
 
Since the device is about the size of two packs of chewing gum placed side-by-side it is very portable.  It is also very inexpensive.  These devices can be purchased new on eBay for less than $10 (U.S.).  That $10 price also includes shipping and handling charges. 
 
I wanted to incorporate this device into my home linux environment also.  Alas, I could only find fragments of information about using this device in linux on multiple internet sites.  However, I found numerous references to the existence of a si470x kernel module driver for the si470x chips upon which this device is based. 
 
I collected and pieced the information together to form a script for what I believe is a complete solution to using the InstantFM radio in linux, which I provide below. 
 
Requirements to use this device are: 
 
1) Installation of the "gnomeradio" package. 
2) The following kernel object modules compiled for one's active kernel 
     radio-usb-si470x 
     snd_usb_audio 
     usbhid 
3) An ADS Technologies InstantFM device. 
 
The presence of the kernel object modules can be confirmed by executing the following commands one by one: 
```

modprobe -l radio-usb-si470x 
modprobe -l snd_usb_audio 
modprobe -l usbhid

```If one or more of the object modules are missing it is doubtful that you will be able to to use the device unless you are willing to obtain the driver source files and compile them yourself for your running kernel. 
 
Assuming that you have met the requirements and wish to use this device, the first step is to add the following lines to your /etc/modules file by opening a terminal and executing "sudo gedit /etc/modules" 

```

#hotplug for ADS Technologies Instant FM Radio (USB) 
radio-usb-si470x band=0 space=0 de=0 
snd_usb_audio 
usbhid

```Save the file and reboot so that the modules will be loaded. 
 
(Note: The radio-usb-si470x assignment values are "zeros".) 
 
Now right click on an empty space on your desktop and select to create an empty file.  You can name this file whatever you like but I chose "InstantFM" so that I would always know what the file pertained to.  Right click on your newly created file and choose to open it with gedit. 
 
Now copy and paste to add the following lines into the file:
```

#!/bin/bash 
echo 
echo 
 
if  radio=$(ls /dev | grep --color=never radio*) ; then  
    echo 
    echo "RADIO DEVICE FOUND -- Set gnomeradio preferences to show:" 
    echo 
    echo "Radio Device: /dev/$radio" 
    echo 
    echo 
else 
    echo 
    echo 'RADIO DEVICE NOT FOUND -- EXITING' 
    echo 
    echo 'Check driver and device installations.' 
    echo 
exit 1 
fi 
 
arecord -q -c 2 -D hw:1,0 -r 96000 -f s16_LE | aplay -q -B - & 
 
/usr/bin/gnomeradio & 
 
while ps -A | grep gnomeradio 2>&1 > /dev/null 
do sleep 5 
done 
echo 
echo 'KILLING ARECORD PROCESS.' 
killall -9 arecord 
echo 
 
exit

```and save the file. 
 
Next cut the file from your desktop and paste it into the /usr/bin folder with your file manager. 
 
Open a terminal and execute "sudo chmod 755 /usr/bin/InstantFM" 
 
The script which you just created is now suitable to be executed from the command line in a terminal window by typing its name and I encourage executing it at least the first time in a terminal window because it provides useful information about configuring gnomeradio.  From a terminal you will also gain a better understanding of what the script does and if your setup is working properly. 
 
Setting the preferences in gnomeradio should only be required once.  After that you will probably wish to add an entry for the "InstantFM" command to your menu for ease of use. 
 
Notes: 
 
1)  The script assumes that you have only one sound card installed.  If you have more that one sound card change the "arecord" command in the script accordingly to accommodate the additional sound card(s). 
 
2)  Exercise caution attempting to use the device in a virtual machine.  My experience with VirtualBox was not good.  I suspect that VirtualBox's USB pass through function is not sophisticated enough for USB audio devices.  A process on the host machine went berserk and locked up both the host machine and the virtual machine. 
 
3)  Although in an MS Windows environment this device displays the title of the currently playing song using "RDS" technology, I do not believe that RDS support is provided by the linux driver for this card.  Even if the driver does provide RDS support, gnomeradio does not support this functionality. 
 
4)  Although it can be done, it is nearly as difficult (or more so) to get this device to function with MS Windows Vista or MS Windows 7 as it is in linux.  The MS software supplied with the device is purportedly for WinXP or older operating systems. 
 
 
Best Regards, 
 
s4

---

### Post by tom3p on 2012-08-15
S4Brains,
Thanks very much for the 1st useful info about the si470x. I had to edit your script tho: changing 'radio*' to just 'radio'. I played with it in a terminal to see why the device was failing. 'radio0' was ok, and 'radio' is more generic. I'm using Ubuntu 10.04 LTS   linux 2.6.32-122-rtai ( the linuxcnc distro ). really, i've spent a lot of hours trying to get this thing running. Thanks!

---

### Post by s4brains on 2012-08-20
tom3p,

I'm pleased that it worked for you.  I'm not certain that I understand the need to edit the script,  but then I don't really need to understand.  I would have thought that 'radio*' would match radio, radio0, radio1, etc.

The important thing is that you were able to get it to work for you.

Regards,

s4

---

### Post by IndyDXer on 2013-01-09
S4Brains,
Thanks for sharing your hard work. I followed your clear instructions but have failed! I am a rookie to Ubuntu and Linux, so there is a lot I do not know. I am using Ubuntu 10.10 on an HP Pavilion. The InstantFM dongle is plugged in. I run InstantFM and this is what happens:

indydxer@HP-Pavilion:~$ InstantFM



RADIO DEVICE FOUND -- Set gnomeradio preferences to show:

Radio Device: /dev/radio0


Initializing v4l1 failed
Initializing v4l2 failed
gnomeradio-Message: Could not scan. Radio is not initialized.
lirc_init: No such file or directory
gnomeradio-Message: Could not start lirc!

KILLING ARECORD PROCESS.

indydxer@HP-Pavilion:~$ 


Can you give me some suggestions?

Thanks,

IndyDXer

---

### Post by IndyDXer on 2013-01-09
I was too quick to give up. As it turns out I had to edit "radio device" in the Gnomeradio General Settings. It had "/dev/radio" and I just had to add a "0" to radio and it started to scan.
Anyone know about source code for auto scanning and recording RDS? I do this with the HDHomerun tuners and want the same capability for FM radio.

IndyDXer

---

### Post by s4brains on 2013-01-23
IndyDXer,
 
It appears that initially you failed to follow the "Set gnomeradio preferences to show: Radio Device: /dev/radio0" message from the script.  I'm glad that you didn't give up.
 
Was the instruction from the script not clear or did you not notice the message from the script when you executed it?
 
I too, would like it if RDS output could be made available from the device under linux but I suspect that RDS is not a high priority in the linux community.
 
Best Regards,
 
s4

---

### Post by Whoopie on 2013-01-24
What about [http://rdsd.berlios.de](http://rdsd.berlios.de)? Just googled it, but I don't own a device with RDS support to test.

BTW, it also mentioned in the kernel documentation under Documentation/video4linux/si470x.txt.

---

### Post by ramboton on 2013-01-25
This worked for me in Ubuntu 12.04, however I do get an error, can't find /dev/mixer, but it still works.

Thanks

---

