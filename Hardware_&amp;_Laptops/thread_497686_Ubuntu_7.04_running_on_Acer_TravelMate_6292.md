---
title: "Ubuntu 7.04 running on Acer TravelMate 6292"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by talava on 2007-07-10
The Santa Rosa technology that 6292 is based on is quite poorly supported at the moment so getting ubuntu working perfectly without extra effort is not very likely, Most of the problems should be history when a stable release of Gutsy arrives but for the time being one has to cope with Feisty. I'm not claiming to be an expert, but maybe a newbie or two can find here a handy short-cut to get the OS installed properly. So this post merely summarizes the solutions found elsewhere aiming to get the laptops hardware working with Linux. But let me begin:



**Installing Ubuntu 6292:**
The live cd didn't work at all (at least a month ago), so Ubuntu had to be installed using the Alternate installer. This shouldn't be a problem and there's no reason for me to go on about installing ubuntu since there are loads of tutorials for newbies.




**Getting the graphic settings right:**
Your laptop is running on Intel x3100 graphics driver using the mobile GMA965 chipset. At first ubuntu is running only  with 1024x768 resolution. To get the native resolution (1280x800) you have to replace the default Vesa driver with the Intel driver. I did this manually but thanks to our fellow Ubuntuforums user that should be very easy with hes instructions and patch. Follow [his tutorial ]("http://ubuntuforums.org/showthread.php?t=494943")to get your graphics functioning.

note: to change your driver from vesa to intel use command: sudo dpkg-reconfigure xserver-xorg and make the corrections needed.
On my laptop compiz isn't working nor are other 3d-features. Even certain screen savers can crash the system. But at leat getting the correct resolution is fairly satisfying.




**Getting the sound working:**
The realtek sound card was a serious problem for me until just recently I found a cure. You need the Alsa 1.10.14rc4 driver which at least yet isn't listed in the Feisty repositories so you have to compile it manually.

Here's a fairly simple Howto:
Download the described alsa driver and realtek12.tar.gz from [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104)

- Unpack the alsa driver (home folder's good)
- Unpack the realtek12.tar.gz and put files patch_realtek.c and hda_codec.c into alsa folder alsa-driver-1.0.14/pci/hda
- type ./configure
- type make
- type sudo make install
- type sudo gedit /etc/modprobe.d/alsa-base and add this line to the file: options snd-hda-intel model=toshiba I also put in line snd-hda-intel model=acer alltough it might not make a difference in this case :)
After reboot sound is working.

If you get a message saying that a file or a folder doesn't exist and therefore you can't execute make or make install, read blobbe's post: [http://ubuntuforums.org/showthread.php?t=489603&page=2#15](http://ubuntuforums.org/showthread.php?t=489603&page=2#15)




**Wlan:**
- Install ndiswrapper from the repositories and now you can install windows wireless drivers and get the 4965AGN wifi module working.
- Get the suitable driver [here]("http://downloadcenter.intel.com/download.aspx?url=/13000/eng/V11.1.1.0_XP_DRIVERS.ZIP&agr=N&ProductID=2753&DwnldId=13000&strOSs=All&OSFullName=All+Operating+Systems&lang=eng") and unpack it
- type sudo ndiswrapper -i netw4x32.inf
- type sudo ndiswrapper -m
- ndiswrapper -l (console should now state driver being installed)
- sudo gedit /etc/modules and add line "ndiswrapper" save and close.
After reboot you should be able to use you're wlan.




**Other hardware:**
I'm quite happy after getting the real important features working, but here's something i've gathered about other hardware in 6292.
Webcam: The Easycam2 doesn't support the Acer Crystal Eye and my system fails to even recognize the camera so I haven't gotten that working yet.
Bluetooth: Should work right out the box there are blue tooth programs available in the repositories so use one of those to enable using it.
The memory card reader has a good chance of functioning and I'll be reporting soon about that one.





More info:
[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)
[http://ubuntuforums.org/showthread.php?t=471794&highlight=4965agn](http://ubuntuforums.org/showthread.php?t=471794&highlight=4965agn)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165)

---

### Post by pyknite on 2007-08-19
hi there... I sent you a pm but you don't answered me :( so i try here ;)

all is working except the sound :( it work only with headphones and it is very very weak :(

Do you have a solution?

ps: for the wifi, i used ndisgtk, in console mode it didn't work :(

thx

---

### Post by talava on 2007-08-20
Hi there,

I read your PM yesterday, but didn't find myself the time to answer :) sorry mate.

Do you now have two channels instead of one used to control sound levels? The first one should be for the 3.5mm jack and second for speakers. If there's only one control in gnome try typing 'alsamixer' in console and see if you'll see them. And of course unmute everything.

If your kernel is something other than 2.20-15, it might also make the difference between sound working and not working with the instructions given.

If this isn't any help, not being an expert I can't give you any better advice, but I'm sure someone else can!

good luck!

---

### Post by pyknite on 2007-08-20
hi...

thx for answer ;)

my kernel is 2.20.16 (last update)

i made you a screenshot of alsamixer result in console...

thx ;)

---

### Post by pyknite on 2007-08-21
ok, i resolve the problem ;)

i have installed alsa-lib and utils, i take realtek15 instead of realtek12 and instead of putting the realtek file in pci/hda, i put them in alsa-kernel/pci/hda

next i make a sudo alsaconf then reboot

and now my sound is working :D

thx for help ;)

---

### Post by trastornau on 2007-09-02
Hi,

I have the same 6292, and tried following the thread about getting the new intel  video card working but no luck. Could you post exactly what you did? That would be of great help. Thanks.

---

### Post by pyknite on 2007-09-08
hi...

I will post you the detail if i have the time... but since yesterday my soundcard doesn't work anymore :( i think it's append just after the update...

---

### Post by pyknite on 2007-09-08
ok, try this:

go to alsa-project website and download the new package 1.0.15rc1 driver / lib and utils...

install lib and utils (using ./configure, make, sudo make install)
after install asla driver without apliing the realtek patch (now its include) 

for me, it work great and i already have the sound working ;)

---

### Post by trastornau on 2007-09-14
I gave up on Feisty, and gave a try the tribe 5 of Gutsy. Incredibly, almost everything works out of the box:  Video with acceleration, webcam, ethernet, wireless, acpid, suspend, hibernation, bluetooth (it sees the driver, but did not test with a peripheral). Everything... but the sound. Sorted with alsa 1.0.15r1, but the controls are all weird: there's no master in the mixer, only headphone and   PCM, Mic doesnt work, etc. 
A bit off-topic since this is about Feisty. But it is just to show how far Ubuntu is going. It took me a week to battle with gentoo in the same laptop to get there.

---

### Post by pyknite on 2007-09-15
for the sound with 1.0.15rc1 you also need to put this line:
options snd-hda-intel model=acer
in your /etc/modprobe.d/alsa-base

---

### Post by pyknite on 2007-09-15
wich software do you use to use your webcam? because i tried to install gutsy and my webcam doesn't work :(

---

### Post by longman on 2007-10-15
Hi there,
look, Acer 6291 webcam ("Crystal Eye") does work in Ubuntu Gutsy, here are the [hints of an owner of Acer 6292 with Fedora 7]("http://www.fishpool.org/").
They do work for me flawlessly.
I have gstreamer-0.10-good installed and this command:
```

gst-launch-0.10 v4l2src queue-size=2 !  ffmpegcolorspace ! ximagesink

```
gives me a window with realtime picture.
My 0.02$ :)

---

### Post by kay_rus on 2007-11-12
for some reason the suspend mode doesn't work on ubuntu gutsy.
it is strange, because if I suspend laptop and power it on after few minutes - everythink went fine. but if I suspend it for a couple of hours - power on doesn't work. only cooling fan is on, but display is off and everything too.

how can I solve it?

---

### Post by Vadimir on 2007-12-30
brigthness doesn' t change with keys fn+left, fn+right

indicator shows that brightness changes but no effect 

```
echo 50 /proc/acpi/video/GFX0/LCD/brightness
```

works correctly

---

### Post by meowdin on 2008-02-05
[http://gezhi.org/node/713](http://gezhi.org/node/713) 

Specially for Mic and sound

---

