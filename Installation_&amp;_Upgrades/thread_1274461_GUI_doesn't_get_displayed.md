---
title: "GUI doesn't get displayed"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by JVo on 2009-09-24
Okay, so first off, I'm a total newbie.
 
About 6 months ago, I decided to install ubuntu on an old IBM T22 Thinkpad laptop. My memory is a bit hazy, but I think it installed successfully. But then I attempted to install a wireless USB adapter, wasn't able to get it to work (didn't have the appropriate driver for it, I think). And so I gave up on the computer, and haven't looked at it or thought about it in 6 months. I only mention the wireless adapter, because my memory tells me that that messed things up.
 
Now, 6 months later, I've taken the computer out, and tried starting it. It went through its initial self test, showed me the ubuntu logo and progress bar, and then it went to a blank screen (briefly showing a flashing underscore in the top left). After this, nothing happens. 
 
I found something online about how maybe it doesn't understand my graphics card. And about how I should be able to press "Alt-F1" or "Ctrl-Alt-F1" to get to a command prompt from the blank screen, but that does nothing.
 
If I remember correctly, when I installed, I did have some trouble choosing the appropriate graphics card/display options (my graphics card wasn't shown in the list).
 
Thanks for any advice!
 
P.S. I can't find my ubuntu cd anymore, but I'll buy or obtain another if necessary.

---

### Post by rreese6 on 2009-09-24
Did you try to boot in the recovery mode? The second selection in the grub menu.
If you can get to a prompt we should be able to diagnose the issue.
In the meantime it would be a good idea to download Ubuntu, or Xubuntu
but not the latest version as there are some problems with older laptops. try version 8.04 
Let us know when you have that ready.

---

### Post by JVo on 2009-09-24
> **rreese6 said:**
> Did you try to boot in the recovery mode? The second selection in the grub menu.
If you can get to a prompt we should be able to diagnose the issue.
In the meantime it would be a good idea to download Ubuntu, or Xubuntu
but not the latest version as there are some problems with older laptops. try version 8.04 
Let us know when you have that ready.
 
Thanks for the reply! Yep, I'm totally clueless. I think I saw the grub menu option, but didn't think to go there. I'll try that later when I get home.

---

### Post by JVo on 2009-09-24
By the way, any advice on what to do once I'm in the recovery mode?

---

### Post by JVo on 2009-09-24
Oh yeah. This is the link I was referring to that I'd found: [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)
 
It's for kubuntu, but maybe it applies to ubuntu, too? 
 
It says that after you get a command line, to type: "sudo dpkg-reconfigure xserver-xorg" to set display type and resolution, followed by "startx". Maybe I should do that?

---

### Post by rreese6 on 2009-09-24
That may be the simplest way, give it a try
the difference between Kubuntu and Ubuntu is te desktops basically, so ok to follow that instruction.
let us know

---

### Post by JVo on 2009-09-25
[FONT=Arial]Okay, I've gotten to a command line through the recovery mode. What's weird is I run 
[/FONT][FONT=Arial]"sudo dpkg-reconfigure xserver-xorg", and it's apparently supposed to ask me 
what settings I want for my display, resolution, and refresh rate. But it 
never asks me for that. Instead, it asks me the following:

1) Use kernel framebuffer device interface?
2) Autodetect keyboard layout?
3) Keyboard layout
4) XKB rule
5) keyboard model
6) keyboard variant
7) keyboard options

So, basically the last 6 questions are all about my keyboard. Then it finishes the script and logs the warning:
"...xserver-xorg postint warning: overwriting possibly customized configuration file; backup in /etc/X11/xorg.conf....."

Anybody have a clue? Thank you!
[/FONT]

---

### Post by rreese6 on 2009-09-25
I may be wrong but it would appear that is only going to run in VESA mode. 
Were you able to list the xorg.conf from /etc/X11 folder?
can you post that here?

---

### Post by JVo on 2009-09-25
> **rreese6 said:**
> I may be wrong but it would appear that is only going to run in VESA mode. 
Were you able to list the xorg.conf from /etc/X11 folder?
can you post that here?

/etc/X11/xorg.conf:

....comments....

Section "Device"
   Identifier  "Configured Video Device"
   Option      "UserFBDev" "true"
EndSection

Section "Monitor"
   Identifier "Configured Monitor"
EndSection

Section "Screen"
  Identifier "Default Screen"
  Monitor  "Configured Monitor"
  Device "Configured Video Device"
EndSection

 
You're saying it may only allow the option of the VESA display type? And that's why it's not asking me?

Thanks so much!

---

### Post by rreese6 on 2009-09-25
Let's also look at what video card you have.

```
lspci | grep VGA
```
post result here

I think you might have an S3 Savage Video Card. and there is a driver for that one for xorg..
I found some interesting sites about thinkpadn T22 and Linux
[http://www.thinkwiki.org/wiki/Category:T22](http://www.thinkwiki.org/wiki/Category:T22)
[http://www.thinkwiki.org/wiki/S3_Savage_IX8](http://www.thinkwiki.org/wiki/S3_Savage_IX8)
[http://www.thinkwiki.org/wiki/Savage](http://www.thinkwiki.org/wiki/Savage)

once you confirm you video card we will go forawrd

you might want to try to modify your xorg.conf file with this information:
```
Section "Device"
Identifier "Configured Video Device"
Option "AGPMode" "2"
Option "AGPSize" "8"
#Option "ShadowStatus" "true"
#Option "ShadowFB" "true"
Option "NoAccel" "true"
EndSection
```

---

### Post by JVo on 2009-09-25
> **rreese6 said:**
> Let's also look at what video card you have.
 
```
lspci | grep VGA
```
post result here
 
I think you might have an S3 Savage Video Card. and there is a driver for that one for xorg..
I found some interesting sites about thinkpadn T22 and Linux
[http://www.thinkwiki.org/wiki/Category:T22](http://www.thinkwiki.org/wiki/Category:T22)
[http://www.thinkwiki.org/wiki/S3_Savage_IX8](http://www.thinkwiki.org/wiki/S3_Savage_IX8)
[http://www.thinkwiki.org/wiki/Savage](http://www.thinkwiki.org/wiki/Savage)
 
once you confirm you video card we will go forawrd
 
you might want to try to modify your xorg.conf file with this information:
```
Section "Device"
Identifier "Configured Video Device"
Option "AGPMode" "2"
Option "AGPSize" "8"
#Option "ShadowStatus" "true"
#Option "ShadowFB" "true"
Option "NoAccel" "true"
EndSection
```
 
Yes, I do have the S3 Savage Video card. So maybe install a driver for it? Should I try modifying xorg.conf first?

---

### Post by JVo on 2009-09-25
I also noticed this link that you provide [http://www.thinkwiki.org/wiki/S3_Savage_IX8](http://www.thinkwiki.org/wiki/S3_Savage_IX8) has a section titled "Blank Screen", which describes a problem similar to mine (although on a T20 running Debian). Does the info there help us?

---

### Post by rreese6 on 2009-09-25
It seemed so to me.
I would back up the xorg.conf file first
```
cd /etc/X11
ls -l xorg*
sudo cp xorg.conf xorg.conf.bad

```

Then I would copy the data I gave to you and opening the xorg.conf file with an editor (I like using nano)
sudo nano xorg.conf

then modify the xorg file

once finished hit CTRL X to exit and save it

then try startx to see it it worked
if so, reboot

I am sorry it took so long to get back to you, I had an idea to put this laptop on a pcmcia wired connection
and the pcmcia connector pins bent. so I had to completely disassemble the laptop, pull the motherboard out and fix the bent pins...took a bunch of time....but I am up and running wired now...so faster speed :)
And the amazing part, is everything works :)

---

### Post by JVo on 2009-09-25
> **rreese6 said:**
> It seemed so to me.
I would back up the xorg.conf file first
```
cd /etc/X11
ls -l xorg*
sudo cp xorg.conf xorg.conf.bad

```Then I would copy the data I gave to you and opening the xorg.conf file with an editor (I like using nano)
sudo nano xorg.conf

then modify the xorg file

once finished hit CTRL X to exit and save it

then try startx to see it it worked
if so, reboot

I am sorry it took so long to get back to you, I had an idea to put this laptop on a pcmcia wired connection
and the pcmcia connector pins bent. so I had to completely disassemble the laptop, pull the motherboard out and fix the bent pins...took a bunch of time....but I am up and running wired now...so faster speed :)
And the amazing part, is everything works :)


Whoo hoo!!! It worked! I used the changes to the file that you gave me. I cannot thank you enough. 

By the way, earlier today I had actually downloaded 8.04 (twice to be sure). I actually had attempted to install both, but both had errors. Does that happen a lot? (Anyway, I'm glad that the install failed, because this worked and was a lot easier.)

---

### Post by rreese6 on 2009-09-25
Ok Great! Now mark the post as solved so it will help others.
Have fun!

Having errors when installing is related to a bad cd burn usually.
that is fixed by burning at a slower speed (4x or 8x) for the older hardware.
Also always run the CD media check when you boot up the CD.
take care

---

