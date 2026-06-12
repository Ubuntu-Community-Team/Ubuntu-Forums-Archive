---
title: "dell inspiron 1100 640x480 video driver"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by intrigue on 2005-07-15
i installed ubuntu last night, and the installation was a breeze. It looks really solid and functional, and i can't wait to get going using it. during the X installation it prompted me for the screen resolutions i would like to run, and I disabled everything but 1024 (this is the native resolution of my laptop lcd). upon logging into gnome the screen resolution was only 640x480 with a 4" black border around it. i went into the System>Preferences> Screen resolution and the only choice is 640x480. I thought it might not have detected and installed the right driver, so i did some searching and to my amazement found intel had a working linux driver for my card (intel 845GM) on their support website. (Dell was no help) It was in rpm format, so i did some searching on that and found out i've gotta use the alien -i package.rpm command. I ran this as root without the x server running, and it seemed to have installed it fine. I logged back into gnome and 640x480 was the only choice still.

Im running a Dell Inspiron 1100.

Is there some further configuration I need to be doing within gnome or grub? I looked for a hardware manager to install the drivers like most OS's have and couldn't find one.

As a possibly unrelated question, is there some way to increase the resolution outside of X?

What strikes me as odd, is that when i boot into the Ubuntu live cd and Knoppix the resolution is 1024, so i know there is a working driver out there. Is there some way i could find out which driver these are loading and manually load it into my installation?

Im sure its an easy newbie fix, but Ive looked in the forums and found nothing on installing this particular card, and don't know anything about configuring debian or ubuntu

thanks in advance for any help

---

### Post by erdejo on 2006-03-15
Hi Y'all,

I have the same problem as Intrigue, but with me it doesn't work when using the Live CD. I also have a Dell Inspiron 1100 and it gives me only the 640x480 option in Resolution menu. :confused: 
I am using the standard "install" (starting the boot from cd) of the live Cd and like Intrigue even tried to uncheck everything but the 1024 option when asked so during boot.
It also seems that my wireless card is not recognized or not working for I have no connection. I have to be honest and let you know that I haven't fooled with that due to the limited screen area......:cry:  But if anyone has any tips on how to go about setting that up (after fixing the video thing) then please feel free to do so....:-| 
I am also new to the Ubuntu experience, although I have tried my hands on Linux back in the early to mid nineties....:rolleyes:  Which wasn't all that bad, just limited time to put into so it kinda died....
But now I am so sick and tired of the Winblows thing thatI would like to be able to switch entirely (or as much as possible for I do a lot of 2D and 3D graphics including CAD and don't know how well Linux is equipped for this...) to this amazing free software and its community!
Anyway, to make a long story not too much longer...If anybody knows why the reso is limited to 640x480 on my Dell let me know..

Thanx in advance!

Regards, Eric

---

### Post by pdobrev on 2006-03-18
I've got a similar problem - the only resolution that my Dell Latitude D510 would run is 1024x768 but I would like also to have 640x480 to play Starcraft in full screen :(

---

### Post by pdobrev on 2006-03-18
These lines in /etc/X11/xorg.conf solved my problem:
Section "Monitor"
        Identifier      "Generic Monitor"
[B]        HorizSync       31.5 - 48.5
        VertRefresh     59.0 - 75.0
[/B]        Option          "DPMS"
EndSection

---

### Post by ninotob on 2006-06-13
One caveat -- the screen refresh rate stuff won't work unless you have the latest bios.  Won't work with bios A22, but after flashing to A32, worked great.

Here is a link to a bootable iso for flashing the bios:  
[http://www.geocities.com/randomnumbergenerator2001/bootcd_A32_1100.zip](http://www.geocities.com/randomnumbergenerator2001/bootcd_A32_1100.zip)

Found here:  
[http://www.geocities.com/randomnumbergenerator2001/#bios_info](http://www.geocities.com/randomnumbergenerator2001/#bios_info)

And I got there from some other ubuntu post I don't feel like looking up.  Anyway, if you try the easy fix suggested above for getting 1024x768, if it doesn't work, check your bios version when the computer is booting up.

---

### Post by durableapostle on 2006-06-14
Try this:

[http://www.ubuntuforums.org/showthread.php?t=190022&highlight=dell+1100]("http://www.ubuntuforums.org/showthread.php?t=190022&highlight=dell+1100")

---

### Post by ed_agamemnon on 2006-07-01
try a package called 915resolution -- i have a Dell Inspiron 1300 and it works a treat :)

---

### Post by x1982mitzu on 2006-10-03
hello!!!! i need some help please! i have a dell 1100 inspiron and i have that resolution problem...on this forum i found the answer to it...but i dont know where i should modify those parameters...Section "Monitor"
Identifier "Generic Monitor"
HorizSync 31.5 - 48.5
VertRefresh 59.0 - 75.0
Option "DPMS"
EndSection... i just dont know where i should go and write or modify these parameters... pls can you help me??thank you

---

### Post by timothyli on 2006-10-25
these lines are from the file

/etc/X11/xorg.conf

---

### Post by dbott67 on 2006-10-25
From a terminal type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` to backup your existing file.  Then type:
```
sudo gedit /etc/X11/xorg.conf
```
and add/modify the lines above.

If you totally hose it up, boot into the terminal and type:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

-Dave

---

### Post by k0hog on 2007-02-20
I have used automatix now resolution is full screen. Thanks for all your help.

---

### Post by Everything Is Relative on 2007-03-28
> **ninotob said:**
> One caveat -- the screen refresh rate stuff won't work unless you have the latest bios.  Won't work with bios A22, but after flashing to A32, worked great.

Here is a link to a bootable iso for flashing the bios:  
[http://www.geocities.com/randomnumbergenerator2001/bootcd_A32_1100.zip](http://www.geocities.com/randomnumbergenerator2001/bootcd_A32_1100.zip)

Found here:  
[http://www.geocities.com/randomnumbergenerator2001/#bios_info](http://www.geocities.com/randomnumbergenerator2001/#bios_info)

And I got there from some other ubuntu post I don't feel like looking up.  Anyway, if you try the easy fix suggested above for getting 1024x768, if it doesn't work, check your bios version when the computer is booting up.
\\:D/ \\:D/ \\:D/ 

**[SIZE="3"]After countless hours and many days and what seemed like 1000 of posts.... I finally got my answer....[/SIZE]**

I could not get anything better than the 600X480 resolution in UBUNTU 
but after following the advice of NINOTUB it worked under 60 seconds. 

This is right on the money. Should fix everyones problems. You still may have to edit 
some lines using the 
sudo /etc/X11/xorg.conf line

Thanks!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Sweet Sister Morphine on 2007-06-24
Thanks guys.  I'd been having the same problem, but I followed your collective advice and now everything is jake.  :D

---

