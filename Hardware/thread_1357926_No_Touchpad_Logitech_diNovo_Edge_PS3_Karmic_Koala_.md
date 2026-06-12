---
title: "No Touchpad Logitech diNovo Edge PS3 Karmic Koala 9.10"
date: 2009-12-17
forum: Hardware
---

### Post by n3IVI0 on 2009-12-17
This question has already been asked, but so far, the solutions are either old or ineffective. Here's the deal. I'm running Xubuntu 9.10 on my PS3. So far, it's been great with only one caveat - my Logitech diNovo Edge keyboard/mouse doesn't work. Now, I have already figured out that getting this thing to work with the built in bluetooth is pointless. It won't work, and nothing anybody has tried is ever going to get it to work. So, plan B - the USB dongle. Now, this worked perfectly on 9.04 Jaunty, as others have noted - plug it in, sync it, instant keyboard/mouse function. In this latest iteration of xubuntu, it even syncs and maintains connectivity through reboots, only the touchpad does not work. It worked without a hitch on Jaunty, and now, this upgrade has broken it.

The closest thing to a solution I've been able to find is [here]("http://www.opcommando.com/?p=54"). Sounds great. Modify xorg.conf, and your touchpad will magically work again. BUT WAIT! 9.10 has no xorg.conf. Brilliant. Break my touchpad, and then deny me the only method of fixing it. Alright. So I do Ctrl-Alt-F1 to get to the CLI, and stop gdm with the command sudo service gdm stop. So far so good. My searches indicate that you can either use the command Xorg -configure (doesn't work. You have to chmod /usr/bin/Xorg to 777, which makes the command work finally, but then it tells you there's nothing to configure) or create it manually. Alright. So let's create the xorg.conf file manually in /etc/X11 and add these lines to it:

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Device" "/dev/input/mice"
Option "Protocol" "Auto"
EndSection

Section "ServerLayout"
Identifier "single head configuration"
Screen 0 "Screen0" 0 0
InputDevice "Keyboard0" "CoreKeyboard"
InputDevice "Mouse0" "CorePointer"
EndSection

Here's the catch. EVEN WHEN YOU ROLL YOUR OWN, if an xorg.conf file is present, xubuntu will NOT BOOT. X crashes to the command line every time. You can't start gdm, and if you reboot with the file present, it's the same deal.

I'm not some random noob asking a question that's already been answered because I couldn't be bothered to search. I've been to Google, this forum, the forum over at PSUbuntu.com, and Logitech's forum, and NOBODY has any idea how to fix this problem. I intend to keep using xubuntu 9.10 because it is blistering fast, even before you enable GPU vram swap. It runs every MAME game I throw at it fullscreen and full speed. Plus it looks cool. YellowDog 6.2 (where I could sync my keyboard/mouse and my Sixaxis controllers with the native bluetooth without a hitch) is kludgy, ugly, and slow, even running XFCE for the desktop. I REALLY don't want to have to go back to Yellowdog just to get my expensive wireless keyboard/mouse working properly. Isn't there anybody who knows how to solve this problem!? Thanks!

](*,)

---

### Post by n3IVI0 on 2009-12-19
bump

---

### Post by Exetubin on 2009-12-20
I'm having this same exact issue.
 
I wish this can be resolved soon because I'm using my PS3 as my backup HTPC right now (my other HTPC just died on me a few days ago).
 
Anyway, I also found a forum giving instructions to add a USB Bluetooth quirk:

 
options usbhid quirks=0x046d:0xc71f:0x00080000


under the /etc/modprobe.d/options, but, as you've guessed, Karmic (Ubuntu 9.10) does not have a /etc/modprobe.d/options directory.
 
The link to the forum is here:
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/1016821.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1016821.html)
 
Maybe there's a way to make it work, but, being a Linux noob, I guess my skills are quite limited.
 
Please post if you find a solution to this dilemma.
 
Thanks!

---

### Post by alpinerod on 2009-12-21
FYI, the DiNovo Edge works perfectly (through the dongle) with a laptop running karmic koala, and yes, the trackpad also works. The problem seems to be with the PS3 (I'm having the same issue)

---

### Post by n3IVI0 on 2009-12-21
So what's the difference between xubnuntu on a laptop and on a PS3? What difference is there between the two builds that makes it non-functional on the PS3?

---

### Post by Exetubin on 2009-12-21
I'm currently here in the office at the moment and I stumbled upon this:
 
[http://ubuntuforums.org/showthread.php?t=1303510](http://ubuntuforums.org/showthread.php?t=1303510)
 
[[FONT=Calibri][SIZE=3][COLOR=#800080]http://ubuntuforums.org/showpost.php?p=8060578&postcount=2[/COLOR][/SIZE][/FONT]]("http://ubuntuforums.org/showpost.php?p=8060578&postcount=2")
 
 
I'm not sure if this fixes the touchpad problem, so, I'll have to try it later.
 
If someone can try it, please let us know if it works.
 
Errr... maybe the link above is for solving a different problem altogether, but, it's worth a try?
 
Thanks!

---

### Post by n3IVI0 on 2009-12-22
This didn't work for me. The problem was not a failure to detect the keyboard after suspend. In fact, as near as I can tell on my rig, it not only works before boot in Petitboot, but carries through all the way to the desktop. The problem is that the touchpad is not active, ever, where it was in Jaunty, and apparently works just fine when Karmic is installed on other platforms.

---

### Post by Exetubin on 2009-12-22
n3IVI0,
 
Thanks for trying.
 
I didn't get a chance to try the solution last night, so, you actually saved me some time :).

---

### Post by n3IVI0 on 2009-12-24
You are welcome. Now. Doesn't anybody know what could be causing this behavior? No touchpad on this keyboard when the PS3 build of xubuntu 9.10 is installed, but on regular desktop versions of xubuntu, the touchpad works just fine. What is the difference between the builds that is causing this problem?

---

### Post by alpinerod on 2009-12-24
> **n3IVI0 said:**
> You are welcome. Now. Doesn't anybody know what could be causing this behavior? No touchpad on this keyboard when the PS3 build of xubuntu 9.10 is installed, but on regular desktop versions of xubuntu, the touchpad works just fine. What is the difference between the builds that is causing this problem?

would like to add that touchpad doesn't work on Ubuntu (not just XUbuntu) ppc build.  Just logically speaking, we may have to move this discussion (or start another one with link to this) in the ppc & mac forum. Is that against the rules?

---

### Post by Exetubin on 2009-12-30
BUMP!
 
Has anyone found a solution for this issue?
 
I'm still struggling to get this working.
 
Thanks in advance!

---

### Post by ljorn on 2010-01-01
Hi
I had the same 'no-touchpad-working' problem using my PS3+Logitech diNovo Edgekeyboard w/ touchpad+Xubuntu 9.10- It worked fine before I upgraded to 9.10 from within Xubuntu 9.04. After many experiments, I found out removing the package Xserver-Xorg-Input-Synaptics solved my problem. At the same time I installed petit boot but that alone did not cure the problem, so I believe the Xserver-Xorg... package is the crook.

good luck!=P~

---

### Post by Exetubin on 2010-01-01
Everyone,
 
Just verifying that ljorn suggestion (to uninstall Xserver-Xorg-Input-Synaptics) FIXED the touchpad problem!
 
Happy happy joy joy! :P
 
Thanks ljorn

---

### Post by alpinerod on 2010-01-02
Confirmed solution!

Thanks a ton

---

### Post by vgrisham on 2010-01-06
Thanks so much to everyone on this thread, especially ljorn. My keyboard and touchpad now both work well (well, scrolling is a little tricky, but I think it may be the pad itself).

By the way, this solution works on AMD Karmic (Gnome).

---

### Post by n3IVI0 on 2010-01-06
Awesome! It works!! Yay, full-functioning Xubuntu on the PS3 and I don't have to be tethered by a cable anymore!

---

### Post by ps3mhome on 2010-05-13
Hi! I am about to buy a Logitech diNovo Edge for use with a ps3 with ubuntu 9.10.

Is my understanding correct that you use it with the USB dongle (of the diNovo Edge) and not with the built-in bluetooth?

Do you just insert the dongle, press connect on the keyboard and on the dongle, or do you have to do anything more (install drivers, etc)?

---

### Post by zoggnoff on 2011-03-30
I wanted to implore this solution but when I went to remove Xserver-Xorg-Input-Synaptics it came back as package not found. What gives? I am using 9.10 on PS3 with a Logitech USB keyboard. Same ongoing problem

Update:  I TAKE THAT BACK IT WORKS! MAN! I don't know why but you have to use the right syntax

```
sudo apt-get remove xserver-xorg-input-synaptics
```you should probably use *purge* in place of *remove *because *purge *is more encompassing

:guitar:

---

