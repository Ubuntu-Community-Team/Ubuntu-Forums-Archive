---
title: "Lenovo IdeaPad Y530 with Ubuntu 8.10: Help needed."
date: 2008-12-24
forum: Hardware
---

### Post by devrim on 2008-12-24
Hi, I'm a brand new linux user who has been using all versions of Windows until yesterday. Today, I just purchased my new laptop (Lenovo IdeaPad Y530) and decided to go wild and format the entire hard drive with live Ubuntu 8.10 64bit disk. Now I have Ubuntu running almost perfectly. I have a few concerns and would like advanced users to help me out. 

1. I don't know how to find the correct drivers for my microphone and webcam (my apologies if the language is wrong). My laptop has a built in microphone and a 1.3 Mpixel webcam. They don't seem to work.

2. Screen brightness is reversed. Function UP Arrow seems to decrease brightness while Function Down arrow increases it. This is not too much of a problem but my monitor keeps dimming automatically after boot up. Also, after certain period of inactivity (or battery use), it seems to increase brightness instead of decreasing. Is there a fix for this (for a Linux novice)?

3. I love open source programs such as Firefox, Open Office but I don't know if there is a better photo editing alternative to Gimp. I'm just too used to Photoshop and gimp seems a little unfriendly/unfamiliar.

Any help is greatly appreciated.

HD:  320 GB
RAM: 4 GB
Processor: Intel Centrino Core 2 Duo (2 GB)

---

### Post by logos34 on 2008-12-25
> **devrim said:**
> 
3. I love open source programs such as Firefox, Open Office but I don't know if there is a better photo editing alternative to Gimp. I'm just too used to Photoshop and gimp seems a little unfriendly/unfamiliar.


Not sure what version PS you're running, but Wine might be an option:
[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

---

### Post by 00chilli00 on 2009-01-01
Hey ive got the same laptop as you 
And im looking for the same things as you, but no luck,
You can install Wine update it to the newst version 
then after that you can install Photoshop cs2 , if u find out how to get the mic 
and webcam working pm me thanks

---

### Post by 00chilli00 on 2009-01-01
I just found something odd, 
if u open ekiga softphone 
the webcam works so its weird i had a look in the dmesg and i got this
[   12.782397] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (04f2:b105)
[   12.786024] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:1d.7/usb8/8-5/8-5:1.0/input/input8
[   12.809253] usbcore: registered new interface driver uvcvideo
[   12.809291] USB Video Class driver (v0.1.0)
so it knows its there but im not sure how to get it working in anyother programs

---

### Post by lun on 2009-01-02
This thread is updated regularly.  It is about the y510, but much of it applies to the y530 (there is discussion about it there):

[http://ubuntuforums.org/showthread.php?t=870681](http://ubuntuforums.org/showthread.php?t=870681)

> 2. Screen brightness is reversed. Function UP Arrow seems to decrease brightness while Function Down arrow increases it. This is not too much of a problem but my monitor keeps dimming automatically after boot up. Also, after certain period of inactivity (or battery use), it seems to increase brightness instead of decreasing. Is there a fix for this (for a Linux novice)?

The first two questions are addressed in this thread.  For the third one, i am unsure how well PS runs in wine, if at all.  The link logos34 posted seems to cover it pretty well.

nick

---

### Post by 00chilli00 on 2009-01-03
good news 
i found out why the mics didnt work
in terminal do this ,
gnome-volume-control 
then change the mic to max and then go into system>prefrences>sound
and test the sound input
hehe

---

### Post by arashiko28 on 2009-01-03
> **devrim said:**
> Hi, I'm a brand new linux user who has been using all versions of Windows until yesterday. Today, I just purchased my new laptop (Lenovo IdeaPad Y530) and decided to go wild and format the entire hard drive with live Ubuntu 8.10 64bit disk. Now I have Ubuntu running almost perfectly. I have a few concerns and would like advanced users to help me out. 

1. I don't know how to find the correct drivers for my microphone and webcam (my apologies if the language is wrong). My laptop has a built in microphone and a 1.3 Mpixel webcam. They don't seem to work.

2. Screen brightness is reversed. Function UP Arrow seems to decrease brightness while Function Down arrow increases it. This is not too much of a problem but my monitor keeps dimming automatically after boot up. Also, after certain period of inactivity (or battery use), it seems to increase brightness instead of decreasing. Is there a fix for this (for a Linux novice)?

3. I love open source programs such as Firefox, Open Office but I don't know if there is a better photo editing alternative to Gimp. I'm just too used to Photoshop and gimp seems a little unfriendly/unfamiliar.

Any help is greatly appreciated.

HD:  320 GB
RAM: 4 GB
Processor: Intel Centrino Core 2 Duo (2 GB)
 
Hello, I have the exact same computer model, been using Ubuntu in it since day 2. The camera works, if you want veriface, you won't have it, veriface is a windows program. Just install cheese 
> sudo apt-get install cheese 
and you can test it.
The microphone works as well, if you have already solved the sound problem, go to the sound manager and raise up the bars for front mic and front mic boost, also, on recording, raise the bars and in device, choose the capture device that best fit's you, for testing go to applications> sound and video> sound recorder.
About the screen brightness I have come to get used, just lower the default brightness, so that won't strain your eyes when changes, and get used to the reversed buttons, though, if you come to think about it, they are not reversed because any number to the right is higher and it goes accordingly to that rule, check the bar when you press the button.:P

About gimp don't know much, it does what I need.
Just left to say, enjoy it :D

---

### Post by 00chilli00 on 2009-01-07
hey ive installed chese but its not working
ekoi soft phone does thoe

---

### Post by 00chilli00 on 2009-01-07
ok den
its working now
some thing els was using the video driver
evil

---

### Post by arashiko28 on 2009-01-07
Great, then. Don't be afraid of asking. I also had a few bumps in the road, but mine is working at 100% :D I'm in love with it.

---

### Post by 00chilli00 on 2009-01-17
Today i wanted to use my cam
But it doesnt work anymore, Whats going on lol
The device is there i did
ls /dev/video*

and it showed me that it was there , and soft phone 
says that it cant pick up the channel of the webcam
whats that mean> what is it meant to be set to
and cheese just shows lots of lines and a fuzzy box in the bottom right corner

---

### Post by dissection on 2009-02-15
I have a Lenovo U330 and I am having the same problem with the webcam. Has anybody found a solution.

---

### Post by jprovostla on 2009-02-28
> **devrim said:**
> Hi, I'm a brand new linux user who has been using all versions of Windows until yesterday. Today, I just purchased my new laptop (Lenovo IdeaPad Y530) and decided to go wild and format the entire hard drive with live Ubuntu 8.10 64bit disk. Now I have Ubuntu running almost perfectly. I have a few concerns and would like advanced users to help me out. 

1. I don't know how to find the correct drivers for my microphone and webcam (my apologies if the language is wrong). My laptop has a built in microphone and a 1.3 Mpixel webcam. They don't seem to work.

2. Screen brightness is reversed. Function UP Arrow seems to decrease brightness while Function Down arrow increases it. This is not too much of a problem but my monitor keeps dimming automatically after boot up. Also, after certain period of inactivity (or battery use), it seems to increase brightness instead of decreasing. Is there a fix for this (for a Linux novice)?

3. I love open source programs such as Firefox, Open Office but I don't know if there is a better photo editing alternative to Gimp. I'm just too used to Photoshop and gimp seems a little unfriendly/unfamiliar.

Any help is greatly appreciated.

HD:  320 GB
RAM: 4 GB
Processor: Intel Centrino Core 2 Duo (2 GB)


Try Picasa [free] from Google

---

### Post by bernie9998 on 2009-03-26
Hey, I am also a recent Y530 owner (model 405166U, specifically).

I was wondering if any of you guys had trouble with suspend and if so how you managed to resolve it?

I posted my issue in more detail here: [http://ubuntuforums.org/showthread.php?t=1106927](http://ubuntuforums.org/showthread.php?t=1106927), but had not had any replies.

Whenever I try to sleep or hibernate, the machine goes into an unresponsive state that must be reset by holding down the power button to force it off.

Any assistance with this issue would be greatly appreciated.

---

### Post by Coburn Roar on 2010-01-17
After installing some new updates, my screen brightness at boot-up dropped to about 25%.  Once Ubuntu fully loads, the brightness returns to 100%.  Has anyone experienced similar problems?  I read some similar post that linked to problem to the BIOS.

---

