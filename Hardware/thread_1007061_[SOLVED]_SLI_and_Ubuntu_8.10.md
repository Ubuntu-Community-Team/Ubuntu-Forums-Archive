---
title: "[SOLVED] SLI and Ubuntu 8.10"
date: 2008-12-10
forum: Hardware
---

### Post by DeathStrikeVirus on 2008-12-10
Hello,
I wasn't sure if I should post this here or in Hardware, but this is my gaming rig so I'll post here.

I recently upgraded from an evga Geforce 8800 GT that ran great on Ubuntus 8.04 and 8.10 to dual evga Geforce 9800 GTXs in SLI.

My problem is that Grub fails to load.  I can still type commands, but I'm a novice with Linux, let alone being competent with the terminal.

Thanks for the help.

---

### Post by Perfect Storm on 2008-12-10
Thread moved.

---

### Post by Perfect Storm on 2008-12-10
Ubuntu Forum Staff bump.

---

### Post by waspbr on 2008-12-10
As far as I know, your SLI should not interfere with grub at all, I am not exactly sure what is wrong but if I had your problem I would try to use a supergrub CD ([http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")) to restore everything to normal.

good luck, don't hesitate to post if you have any more problems

---

### Post by DeathStrikeVirus on 2008-12-11
Oops, I misstated what my problem is. (It was late).  I had a grub problem but fixed it and wasn't related to SLI.

My problem is after grub, Ubuntu loads up and when it should be going to the log in screen I get text only.  I have two HDDs, one that has XP Home and Ubuntu 8.04; the other has Ubuntu 8.10.

XP loads fine in SLI, Ubuntu 8.04 loads fine as well.  8.10 goes to terminal text only.

There's only one error that come up in the text above login.  It says that Kinit failed to initialize.  

I borrowed this [screenshot]("http://i44.photobucket.com/albums/f41/DeathStrikeVirus/view226706583be606d9611251259.jpg") from another forum.  That's exactly what my error is.

This [Thread]("http://www.linuxforums.org/forum/ubuntu-help/134544-ubuntu-wont-boot-sli.html") suggested sudo dpkg-reconfigure -phigh xserver-xorg as a fix.  This updated something but didn't fix the problem.  

Thanks.

---

### Post by Perfect Storm on 2008-12-11
nwm

---

### Post by DeathStrikeVirus on 2008-12-12
Bump.

---

### Post by waspbr on 2008-12-12
have you tried booting in restore mode (usually the second boot option in grub), there you could try to restore X and fix broken packages... I am not sure if it will but it may help

this generally happens when a package is missing, in my little experience it is often related to xserver-xorg. 

in the command line, try to log in as root and write "startx" see if something comes out

---

### Post by DeathStrikeVirus on 2008-12-18
Well, it is fixed.  I updated from 8.04 to 8.10.  When it did that, it wrote over the old xorg.conf.  It also left it blank and did not recognize my video cards, that's why X didn't start.

[http://ubuntuforums.org/showthread.php?t=965180&page=4](http://ubuntuforums.org/showthread.php?t=965180&page=4)
> **Cambo said:**
> I was having the same problem of X not starting up after installing Intrepid. (We won't go into the mess that was created trying to upgrade Hardy :/ )

The answer I ended up working out was to add a Busid entry in the Device section of my /etc/X11/xorg.conf file.

To find the correct Busid, I used;

    sudo lspci | grep VGA

The output I got from this was;

    01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
    04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

(Yes, SLI :D )

So, I then edited the Device section of my /etc/X11/xorg.conf to read as follows;

    Section "Device"
	Identifier	"Configured Video Device"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
    EndSection

A quick;

    sudo service gdm restart

and I was greeted by X running at the maximum resolution of my LCD monitor.

Hope that helps one or two of you.



Cambo

This worked great for me.  Not only does X start, but now my computer is running screaming fast in SLI.  

Thanks for helping out, all.

---

