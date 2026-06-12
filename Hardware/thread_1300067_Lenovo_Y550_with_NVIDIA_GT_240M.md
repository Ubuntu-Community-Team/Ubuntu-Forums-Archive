---
title: "Lenovo Y550 with NVIDIA GT 240M"
date: 2009-10-24
forum: Hardware
---

### Post by lian1238 on 2009-10-24
I'm having trouble with my display, as it is very shaky and showing a lot of "static". There's no easy way to explain this. it looks like tiny bar-visualization for a rock song, but they are 90 degrees rotated. It gets worse on the right side of the screen.

Someone with the exact same problem:
[http://www.nvnews.net/vbulletin/showthread.php?t=138205](http://www.nvnews.net/vbulletin/showthread.php?t=138205)

---

### Post by epi 1:10,000 on 2009-10-26
I was thinking of buying this exact laptop.  Let me know if you find a fix.....

---

### Post by lian1238 on 2009-10-27
Note that this occurs after a suspend or after you go to a terminal (e.g. by Ctrl+Alt+F1). Everything is good after a restart.

---

### Post by lian1238 on 2009-10-31
I went ahead and installed the latest greatest version, Karmic, anyway..
and what can I tell you? I'm loving it! .. well, this is after hours of tweaking and finding workarounds and fixes.

[B]Here's the story:
[/B]You may skip down to the actual instructions below..
if you want..

After I installed Karmic and rebooted, I was greeted with a black screen (on tty1) with a login prompt. What's worse, the screen was blinking/flashing. And I couldn't log in because most of what I typed was getting lost. I had to pound the same key several times until the letter popped up. But I could enter the correct password because I couldn't see what had actually been typed.

So then, I rebooted. Chose the recovery mode and logged in. I have another laptop, so I downloaded the NVidia drivers and put it on a flashdrive. Plugged it in my Lenovo and mounted. Installed the driver and rebooted. Only then did I get into X. Now, there's *another* problem. There were 6 screen on my... well, screen! I don't have a screenshot but you'll see.. *evil laugh*

I googled and found the fix.
[http://www.nvnews.net/vbulletin/showthread.php?t=138205](http://www.nvnews.net/vbulletin/showthread.php?t=138205)

Now, for the shaky screen problem.. I haven't found a cure for that yet. Just need to restart, when that happens.

I'm quite happy with this laptop now. I also had a webcam problem with skype, but that's fixed.

**_Here are the things you need to do:_**

**1) Install Ubuntu 9.10**
Or whatever your flavor is.

**2) Download the NVidia drivers**
Go there: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Download it and save it on a flashdrive. I'm sure you have one. ;)

You can use the livecd if you don't have another useless computer lying around.

[B]3) Install the drivers
[/B]Boot into recovery mode from the grub menu.
Log in, mount the flashdrive, run the sh script with root.

Here's the code for dummies:
```

sudo mkdir /media/disk
# put in the flashdrive
# you can do dmesg to see the location of it.. it'll be in square brackets
# e.g. [sdb]

sudo mount /dev/sdb /media/disk
cd /media/disk

sudo sh ./NVIDIA-Linux-x86-185.18.36-pkg1.run
# use tab to autocomplete the filename
# follow the installer and choose to let it configure automatically

```[B]4) Fix the 6 screen problem
[/B]Add the line to /etc/X11/xorg.conf under the Device Section where it says nvidia
```
Option    "ModeValidation" "NoTotalSizeCheck"
```You should now have something like this:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "ModeValidation" "NoTotalSizeCheck"  #fix 6 screen problem
EndSection
```To edit the file on the commandline:
```
sudo nano /etc/X11/xorg.conf
# add the line
# Ctrl + O to save
# Ctrl + X to exit

```I mean, you *could try* doing in with the 6 screens..

**5) Reboot**
Just hit the power button.

[B]That's it! Enjoy!

**Notes** a.k.a. complaints
[/B]The wireless switch toggles both bluetooth and wifi.
I find it annoying when my palm touches the touchpad and it clicks somewhere.. totally annoying!
I have no way of using the touch-strip, nor the touch buttons. They told me it only works with Vista.
Another drawback is the lack off media keys. They're not even in the FN keys!
There are some FN keys which I don't understand (under F4 and F5).
The monitor doesn't wake on a key press.. but the key gets pressed anyway.
The sleep (FN) key is right next to the Monitor-Sleep (FN) key. (accidents, anyone?)

---

### Post by adroitster on 2010-01-29
Hey Lian1238 please tell how did you make the skype work on your laptop ? I am having the similar config. Ideapad y550 , Geforce GT130M graphics card and nvidia 190.xx video drivers. I could solve my problem of 6 screens using xorg.conf options mentioned on nvnews.com thought solving the same 6 screen problem on 190.xx drivers requires little bit of more changes as compared to 185.xx drivers but thats ok. Can you please tell me what graphics driver are you using ? 185.xx or 190.xx. How did you make skype video work on you laptop. Skype can start my video but unable to show the stream from the sender as well the reciever on the screen but instead shows a white screen which is of almost no use. Please help me out with this problem. I have been digging throught the web since many days and finally I found you saying that you got skype to work properly. Please help me out! Thank you.

---

### Post by lian1238 on 2010-01-29
adroitster, try this in the terminal:

```
export XLIB_SKIP_ARGB_VISUALS=1
skype

```

That is my solution, hope that helps.
Edit: my nvidia driver version is now 190.42.

---

### Post by adroitster on 2010-01-31
> **lian1238 said:**
> adroitster, try this in the terminal:

```
export XLIB_SKIP_ARGB_VISUALS=1
skype

```

That is my solution, hope that helps.
Edit: my nvidia driver version is now 190.42.

 DUDE!! :D you are the saviour . Man searched for the solution for like hours. Thanks a ton. :D

How did you find the solution? Did you try it yourself or it was somewhere online which I missed?

---

