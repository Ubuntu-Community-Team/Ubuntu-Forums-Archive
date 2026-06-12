---
title: "Toshiba T110/00D woes :'("
date: 2009-12-14
forum: Hardware
---

### Post by Vignesh S on 2009-12-14
The Toshiba T110/00D doesn't like Ubuntu very much at all. Here are the problems Ubuntu has on it:

1. Wifi doesn't want to work. Its a RealTek RTL8191SE, and no matter what I do (I did all that was on this [site ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126")and I'm still trying the suggestions on it). I don't know if the driver for the RTL8192SE will work as well, though hopefully Ubuntu 10.04 *finally* releases a fix for this very annoying problem. Until then, anyone with a RTL8191SE enjoying wireless freedom on Ubuntu 9.10 64-bit, or even better, Ubuntu 10.04 Alpha 1 (via LiveUSB)?

2. Screen brightness won't change. Even in the Alpha, it won't change, even after I use the buttons to get it to do so. Funny thing is, notify-OSD comes up with the notifications saying that the screen brightnesses changed. No idea what's happening there :o. Anyone know how to get this working as well?

3. The webcam doesn't work. And I have no idea how to find out which model it is so I can finally try searching for a fix for it. How would I search to find what the model of the webcam is?

4. I don't think the microphone works either, and its the same situation with the webcam. How do I get it working?

NOTE: I am using an Ubuntu 10.04 64-bit Alpha 1 (fully updated) because its the only Ubuntu I know that has ethernet working (wouldn't work in 9.10). When I eventually install 10.04 onto an SD card, then I'll let you know if there is any progress on any of the above.

EDIT: After a fiasco that almost saw me not being able to access the recovery mode (it didn't come with recovery cd's), I decided to stick with the LiveUSB (until 10.04 is released).

EDIT (again): After realising that I could easily go into recovery mode via the GRUB, I've decided to install Ubuntu onto the lappy sometime soon :-D)

---

### Post by Vignesh S on 2009-12-15
Anyone out there that has a Toshiba T110 with Ubuntu on it?

---

### Post by lisati on 2009-12-15
> **Vignesh S said:**
> Anyone out there that has a Toshib T110 with Ubuntu on it?

Mine's an M200 with a different chipset that I haven't a problem with. Can't help, sorry. Maybe someone else can.

---

### Post by Vignesh S on 2009-12-21
So I'm taking this to be that I'm the only one out there that's actually running Ubuntu Linux on this laptop? :???:

EDIT: Got wifi working in Ubuntu 10.04. Trying to get it to work in 9.10 32-bit

---

### Post by Vignesh S on 2009-12-21
YAY!! Wifi works :-D Now to fix up that screen brightness issue...

---

### Post by cajual on 2009-12-22
> **Vignesh S said:**
> YAY!! Wifi works :-D Now to fix up that screen brightness issue...

My function keys brightness settings save for only that single session.  To globally affect the laptop, I had to "sudo nvidia-settings" and modify the brightness/gamma to my liking from there.  Sorry it isn't more user friendly.

---

### Post by Vignesh S on 2009-12-22
> **cajual said:**
> My function keys brightness settings save for only that single session.  To globally affect the laptop, I had to "sudo nvidia-settings" and modify the brightness/gamma to my liking from there.  Sorry it isn't more user friendly.

Don't worry, I'm quite used to things that aren't quite as user friendly that I'd otherwise be used to.

Problem is, I'm not using a Nvidia card, and there isn't even a way to get the screen brightness to decrease, which is really strange, because:
1. When I hit the keyboard hotkey, notify-osd comes up with the notification, but nothing happens
2. There doesn't seem to be a problem with it fading to darkness when the display is blacking out

I really need this fixed up because the increased screen brightness not only sucks the juice out of the batteries, it also burns my eyes out whenever I'm using the laptop in dark places.

I guess this calls for a new thread to finally get this fixed, considering that up to this point, only 90 people have seen this thread...

---

### Post by Vignesh S on 2009-12-23
The screen brightness is now (almost) fixed. I say almost because it doesn't really physically change the screen brightness. Rather, it actually reduces the brightness of *each *window. Oh well, at least I can also change the brightness of the desktop background so that's almost a full fix anyway :-D

Now for the webcam and microphone. I need these two because I'd like to use Skype in Ubuntu without having to switch over to Windows whenever I'd like to use that.

---

### Post by MyR on 2009-12-23
If "everything works flawlessly" in windows, why don't you use it instead?

---

### Post by Vignesh S on 2009-12-24
> **MyR said:**
> If "everything works flawlessly" in windows, why don't you use it instead?

Because:

1. Ubuntu is my preferred OS (don't get me wrong, Windows 7 definitely better than XP or Vista) and it takes like 2 minutes to load while Ubuntu only takes 30 seconds from GRUB to fully loaded desktop :-O

2. Because Windows doesn't give me the freedom to do the things I do in Ubuntu, especially customising the looks of it

3. As my signature says, I enjoy the challenges of getting hardware to work in Ubuntu. My year so far with Ubuntu has taught me that it can be fun getting things to work.

Far out, the last two problems don't even matter. Besides, I've got all my software I use in Ubuntu (save for OpenShot and probably a few others) in Windows anyway. My major quibbles with Ubuntu on this laptop are now solved :-)

---

### Post by okercho on 2009-12-24
Hi! I buy this week a Toshiba T110-10N and I can't get wifi works :(

How do yo get wifi working?

Thanks!!

---

### Post by Vignesh S on 2009-12-25
Right, provided you have an RealTek RTL8191/2SE or RTL8171, this fix will work. By the way, make sure your system is fully updated, for it wouldn't work unless I did so.

Before you do this, **check the version of Ubuntu you have. If it is 9.10, then do this**, **otherwise skip this and go to the instructions:**

If you are running Ubuntu 9.10, then the kernel versions installed in Ubuntu, even when updated  don't exactly like the driver, and won't work. You have to install kernel version 2.6.32 from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/") and downlaod:

[linux-headers-2.6.32-020632_2.6.32-020632_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/linux-headers-2.6.32-020632_2.6.32-020632_all.deb")
This is the linux headers, that has to be installed with the below kernel versions

Now depending on whether you have installed 32-bit or 64-bit Ubuntu

[linux-image-2.6.32-020632-generic_2.6.32-020632_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/linux-image-2.6.32-020632-generic_2.6.32-020632_amd64.deb") for 64-bit
[linux-image-2.6.32-020632-generic_2.6.32-020632_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/linux-image-2.6.32-020632-generic_2.6.32-020632_i386.deb") for 32-bit

The above are linux kernel (version 2.6.32), and hopefully one day, this driver will also be included in it. They are architecture dependant, so if one doesn't work, just install the other one.

If you are running 9.04 or older, then skip the above

**Here's what you do:**

1. Download this file [rtl8192se_linux_2.6.0010.1211.2009.tar.gz]("http://launchpadlibrarian.net/36688638/rtl8192se_linux_2.6.0010.1211.2009.tar.gz")                    . It is a tar.gz and you need to extract it to the Desktop. To do this, you just open with "Archive Manager" and there will be an extract option in that dialog box in the extracting utility. This is the driver for the above wifi card.

2. Go to Applications ----> Accessories ----> Terminal and type in ```
cd ~/Desktop/rtl8192se_linux_2.6.0010.1116.2009
```This will take you into the directory of the file.

3. Type in ```
sudo su
```and type in your password. This will give you root permissions to the computer. 

4. Type in ```
make
```This will compile the source code for the driver

Then:
```
make install 
```This installs the source code onto your computer. Restart and it should work :-D

If there are any problems, let me know, and put whatever comes up in the terminal here.

---

### Post by Vignesh S on 2010-01-03
YAY, webcam works out of the box in Ubuntu 9.10 Netbook Remix, which is really strange, but anyways, it WORKS :-D. Noew that I got that working, now to test if the microphone works too :-)...

---

### Post by Vignesh S on 2010-01-12
OMG!! Thanks to this thread [here]("http://ubuntuforums.org/showthread.php?t=1321403"), I got the screen brightness issue fixed up, and it doesn't require using Compiz :-D. AWESOMENESS. I seriously should make a HowTo about getting all this stuff to work :-)

EDIT: By the way, the screen, when it is on the lowest brightness, isn't black. It is actually still useable, though I presume the backlight is off on that setting. Very useful for bright situations i.e. daylight while using outside :-D

Also, my panel has gone crazy. System monitor won't quite work. I'll fix that up in no time though...

EDIT: It fixed itself up on the next reboot

---

### Post by fishyf on 2010-06-30
I have Ubuntu (Current version of Lucid Lynx) working on a TT110 13H.

The wireless worked on a recent update. In fact, almost everything that I've tested works properly on the current update with no twiddling.

Things that I note that aren't working
1. The function key (Fn F8) won't switch off the wireless
2. Headphone socket
3. Touchpad sometimes behaves bizarrely, e.g. it might be locked in the horizontal - only moving vertically.
4. Internal Mic (haven't tested an external mic)

---

### Post by fishyf on 2010-06-30
Microphone works now.

Solution is hinted at here: [http://zongosaiba.blogspot.com/2010/02/audio-on-toshiba-t110.html](http://zongosaiba.blogspot.com/2010/02/audio-on-toshiba-t110.html)

sudo apt-get install gnome-alsamixer

Then run it.
There are a number of Mics shown. Mic B was selected. Turns out that Mic F works.

---

### Post by fishyf on 2010-06-30
Headphone socket now works. Solution is here: [http://osdir.com/ml/ubuntu-users/2010-05/msg00611.html](http://osdir.com/ml/ubuntu-users/2010-05/msg00611.html)

---

