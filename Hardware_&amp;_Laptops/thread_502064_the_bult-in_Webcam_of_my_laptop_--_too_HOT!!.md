---
title: "the bult-in Webcam of my laptop -- too HOT!!"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by tenderflesh on 2007-07-16
welll, I have a dell m1210 with a built-in Webcam...from the output of 'lsusb', Ubuntu Feisty detects the webcam out of box but has no driver for it...After installing linux-uvc, the webcam works (at least with Ekiga).
 
The annoying problem now is that the webcam gets heated up if i am using Ubuntu...The temperature gets so high after a short period of time, so i am afraid that the webcam might get fried one day...

So, here is my question: **Is that possible to completely disable the webcam if i don't use it?? or blind the Ubuntu temporarily so it won't see the webcam?? **
Thanks!!!

---

### Post by Soybean on 2007-07-16
So, to make sure I understand: the webcam wasn't heating up until you installed linux-uvc, and now it gets hot even if you're not specifically using it?

That should definitely be fixable. I've never used linux-uvc, though, so I can't say exactly HOW to fix it. Lots of help, eh? ;) Do you know if it installed a kernel module? If it did, you could unload it using "modprobe -r <module_name>" when you weren't using it, and that should do the trick. If it does something else, though, you might have to talk to the people who make linux-uvc to find out how to turn it on and off.

Since it sounds like the camera is connected using USB internally, there might also be some way to shut it off at the USB interface. Again, it's not something I know how to do, but it's another angle I'd probably explore if I were experiencing the same problem.

---

### Post by tenderflesh on 2007-07-16
hi, Soybean, thanks for the replay...
the webcam got heated up even before i installed that linux-uvc...so I indeed wanna know how to shut down the USB interface...

---

### Post by Soybean on 2007-07-16
Ah, sorry, I misunderstood. Well, in that case... it's one of those things where it seems like something you ought to be able to do, but I have no idea how to do it. There may be some sort of USB-related trick, or maybe something related to power management... but aside from vague categories, I'm not much help. :( Good luck!

---

### Post by geraldm on 2007-07-16
The place to check for shutting down the device is in the driver manpage.
It may also be possible to manipulate the hub port that the device is connected to.
The information may be available in the file /proc/bus/usb/devices for the hub and camera.

Gerald

---

### Post by AndrewMc on 2007-08-19
> **tenderflesh said:**
> welll, I have a dell m1210 with a built-in Webcam...from the output of 'lsusb', Ubuntu Feisty detects the webcam out of box but has no driver for it...After installing linux-uvc, the webcam works (at least with Ekiga).
 
The annoying problem now is that the webcam gets heated up if i am using Ubuntu...The temperature gets so high after a short period of time, so i am afraid that the webcam might get fried one day...

So, here is my question: **Is that possible to completely disable the webcam if i don't use it?? or blind the Ubuntu temporarily so it won't see the webcam?? **
Thanks!!!

I have the same laptop, and finally discovered a (rather ugly) way to turn it off:

```
sudo sh -c "echo 0 > /sys/devices/pci0000:00/0000:00:1d.7/usb5/5-5/bConfigurationValue"
sudo sh -c "echo 0 > /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/bConfigurationValue"
```

Only one line of this is necessary at any one time, but it switches randomly between the two, so it's safe (on my laptop, anyway) to run both. Change "echo 0" to "echo 1" to switch it back on.

If you want this to be the default, automatically on bootup, install the "sysfsutils" package (from the universe repository), and add the following lines to /etc/sysfs.conf :

```
devices/pci0000:00/0000:00:1d.7/usb5/5-5/bConfigurationValue = 0
devices/pci0000:00/0000:00:1d.7/usb1/1-5/bConfigurationValue = 0
```

Hopefully this works for you as well as it does for me. Do post back with any results. It has fantastically improved battery life for me, from about 4 hours to nearly 6!

---

### Post by tenderflesh on 2007-08-20
woot, tyvm, AndrewMc! Your discovery solved my problem at once :)
may i know how you figure that out??? 
if you don't mind, share other secrets of xps M1210 with me ;)

---

### Post by AndrewMc on 2007-08-20
> **tenderflesh said:**
> woot, tyvm, AndrewMc! Your discovery solved my problem at once :)
may i know how you figure that out???

Guesswork, to be honest. I hunted through /sys for anything related to usb, and found several files. I eventually found the above directories, and confirmed they were they camera by looking at the idVendor and idProduct files, checking the numbers matched those given by lsusb. Then, "ls -l" shows which files are writable, suggesting they can be used to control or configure it. Putting 0 in was a complete guess :)

[QUOTE=tenderflesh]if you don't mind, share other secrets of xps M1210 with me ;)[/QUOTE]

That's about the only particularly interesting detail I've found that's specific to this machine. Most of the rest works just fine. Haven't figured out how to make both headphone sockets work at the same time, though...

---

### Post by lusankya23 on 2007-08-28
Hello, I am having the same issue on my Asus A8 laptop.

My webcam is on /sys/devices/pci0000:00/0000:00:1d.7/usb5/5-4

When I cat it's bConfigurationValue, it replies with a 1 (as expected).

When I try to set it to 0:

sudo sh -c "echo 0 > /sys/devices/pci0000:00/0000:00:1d.7/usb5/5-4/bConfigurationValue"

the value I get from its bConfigurationValue is now a blank "" instead of 0. The webcam does not cool down / turn off. It will not accept a 0 as a value.

However, when I set the entire usb5 hub's bConfigurationValue to 0:

sudo sh -c "echo 0 > /sys/devices/pci0000:00/0000:00:1d.7/usb5/bConfigurationValue"

the webcam turns off and cools down. Unfortunately, when I do this, any USB device I plug into my laptop does not work since I turned that whole hub off.

Is there any other way I can get this web cam turned off? The thing is so hot it nearly burns my fingers ](*,)

Thanks in advanced :-)

-Lusankya23

---

### Post by lusankya23 on 2007-08-28
Well, never mind I guess! I saw in another post to unload the webcam module and the webcam is now off and cool:

sudo modprobe -r gspca

to reload the module:

sudo modprobe gspca


No more burnt fingers when I try to open / close my laptop lid :-P

-Lusankya23

---

### Post by Alfdog on 2007-09-05
Thanks for the work you put in with this, I had to use the terminal commands to shut mine off.  The gspca thing didn't seem to work for me since I'm using kubuntu.

alf

---

### Post by trigoman05 on 2008-04-03
Hello, 

I am having this same problem and have not been able to fix it using your solutions. When I was using Feisty I was able to use the modprobe and it disabled the camera and instantly got cooler, but since I have upgraded to Gutsy that command seems not to work. Also when I try to edit do the other terminal command it doesn't allow me to edit the files. I am using 'sudo' and all but it still doesn't let me.

So I would like to ask if anyone has any other fix that might be able to help me, thanks!
I am running an ASUS A8JS

---

### Post by lusankya23 on 2008-04-04
Yeah, ever since I upgraded to 7.10 it stopped working for me as well. Anyone with any tips on this would be appreciated :-)!

Thanks in advanced,

-Lusankya23

---

### Post by trigoman05 on 2008-04-05
Hi everyone, 
the 
sudo modprobe -r gspca 
does not work on my computer
neither does the
sudo sh -c ... 
stuff

However when I do lsusb I get this:
```

Bus 005 Device 004: ID 0ac8:0321 Z-Star Microelectronics Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c019 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 002 Device 001: ID 0000:0000  

```
My webcam is the on Bus 005 Device 004
since I used lsusb then the camera must be usb 
So I tried to using :

sudo rmmod uhci_hcd

to remove all the usb devices so I used lsusb again
```

Bus 005 Device 004: ID 0ac8:0321 Z-Star Microelectronics Corp. 
Bus 005 Device 001: ID 0000:0000 

```

and the webcam is still ON!!! 

I am extremely new to linux so I don't know how to disconnect specific usb internal devices. All I know is that it seems that the webcam is connected to different module or something else. So is there any way to disconnect that certain Bus Device?
This would be really helpful since it drains my batter life because the power to the webcam is always on.

Thanks

---

