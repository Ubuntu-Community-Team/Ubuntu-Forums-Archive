---
title: "ERROR &quot;Unknown Keyword in Configuration File&quot; when installing Ubuntu for the first ti"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by Duke Morrison on 2009-06-10
Hi.
 
I Tried to install Ubuntu on to a fresh hard disc for the first time.  Had several issues with the first disc I burned, so remade disc at slower speed.
 
The installation finished without any problems, but when re-booting the machine, I get the following message
 
Unknown keyword in configuration file.
boot:
 
if I press enter, the "boot:" just shows up on the next line.
 
What can or do I need to do to remedy this?
 
Thanks for any help.  I realy was looking forward to learing about Linux, and Ubuntu.  I want to build a telephony server.

---

### Post by dstew on 2009-06-10
What happens when you reboot the machine? Do you get a grub menu? Is it a dual boot machine, or just Ubuntu?

---

### Post by Duke Morrison on 2009-06-10
Hi,
 
Thanks for the response. 
 
So, It turns out that when I hit enter, it then says:
 
Could not find kernel image:Linux
 
And if I reboot, I get the same messages over and over.
 
What did I do wrong.
 
This si a brand new HDD, on an older Sony VAIO desktop machine.
 
No partitions, just Ubuntu single boot OS.
 
Wanted to try it out.
 
D

---

### Post by dstew on 2009-06-10
How did you install Ubuntu? Did you use a CD-ROM, and partition the disks? What version of Ubuntu did you install?

---

### Post by Duke Morrison on 2009-06-10
Hi,
 
I installed the latest 9.04 Desktop version.
 
I see that I should have had at least 384MB of RAM although I only have 256 on that machine.  The install process asked about partitions, and I selected use whole disc, so there are no other partitions on the disc.
 
The installation process seemed to go fine with no errors, so I was assuming that there were no problems, at least none noted by the installer.
 
Not sure what to do.
 
D

---

### Post by Duke Morrison on 2009-06-10
Oh, and yes, I burned the image from  the download to a CD.  the first time, I burned it at 24X, and that one caused many errors for install, so I reburned it at 8X, and that one went all the way with no known errors during the installation.
 
after the instalation was completed, it said to restart teh computer, so I did.
 
But then got this error.
 
D

---

### Post by dstew on 2009-06-10
When you turn on your computer, and it starts to boot, what do you see on the screen? Do you see a grub menu?

---

### Post by Duke Morrison on 2009-06-10
Hey DSTEW,
 
Wow, what a dumb dumb I am.  It turns out that I somehow had left the bad image in my other cd drive, and at boot it was trying to boot from the CD.  That is why I was getting the error message.
 
After i removed the CD and rebooted the machine, th esystem went right to the grub menu and started to finish the install process.
 
Man do I feel stupid.  Any way,  thanks for responding.  I suppose I will take care to check what I am doing more thouroughly.  I have been playing disc tag the last few hours, and must have forgotten to remove that disc.
 
best regards,
 
D

---

### Post by dstew on 2009-06-10
Hah! That's a new one for me, old bad CD left in the drive. I would not have thought of it, but it seemed an interesting mystery. Glad you figured it out.

---

### Post by blade_ on 2010-10-12
Hi!

I know "the old crap CD inside drive" was the solution to the problem for the thread starter, but I have the same problem, no faulty disc in drive. Please give me some wisdom! 

I downloaded the .iso for 10.10 Netbook version for my laptop. Using the USB startup disc creator I made a startup usb drive, freshly formatted. I reboot my laptop and I go from Normal LG starup screen to the error message. Nothing happens when I press ENTER, I cannot write whatsoever. If I touch the power button it either immediately dies or nothing happens and I have to press and hold to get out of there...

Any suggestions?

---

### Post by luca.picci on 2010-10-12
> **blade_ said:**
> Hi!

I know "the old crap CD inside drive" was the solution to the problem for the thread starter, but I have the same problem, no faulty disc in drive. Please give me some wisdom! 

I downloaded the .iso for 10.10 Netbook version for my laptop. Using the USB startup disc creator I made a startup usb drive, freshly formatted. I reboot my laptop and I go from Normal LG starup screen to the error message. Nothing happens when I press ENTER, I cannot write whatsoever. If I touch the power button it either immediately dies or nothing happens and I have to press and hold to get out of there...

Any suggestions?

Hi, i experienced the same issue and solved with the workaround suggested at the launchpad bug [#608382]("https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382"). This appears to be a bug known since past july that has not yet been fixed.
The workaround is very simple: open the file /syslinux/syslinux.cfg on your flash drive and remove the keyword "ui" in the last row. After this retry to boot; this worked for me.

Bye

---

### Post by fiddler616 on 2010-10-19
> **luca.picci said:**
> Hi, i experienced the same issue and solved with the workaround suggested at the launchpad bug [#608382]("https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382"). This appears to be a bug known since past july that has not yet been fixed.
The workaround is very simple: open the file /syslinux/syslinux.cfg on your flash drive and remove the keyword "ui" in the last row. After this retry to boot; this worked for me.

Bye

This worked for me too. I was using Maverick x64, with a flash drive prepared with usb-creator.

---

### Post by jangirke on 2010-10-24
Got the same problem I will try the afore mentioned fix and let you know if it woked.

---

### Post by dianagk on 2010-10-27
Well, I don't have the "ui" keyword, but it tells me that the wrong keyword is in file gfxboot.cfg
I opened it and here it is:
foreground=0xFFFFFF
background=0x958490
screen-colour=0x270A1E
hidden-timeout=2
label normal=Normal
append normal=
label driverupdates=Use driver update disc
append driverupdates=debian-installer/driver-update=true
applies driverupdates=live live-install
label oem=OEM install (for manufacturers)
append oem=oem-config/enable=true
applies oem=live live-install install

I'm just trying to get back to 10.04 as 10.10 doesn't work good for me. 
Thank you

---

### Post by timothydonohue on 2010-12-02
jeez, guys.  Thanks for this!  some quick googling, and it turns out that the 'ui' in the /syslinux/syslinux.cfg line was exactly my problem!

---

### Post by rundee_f on 2010-12-11
> **luca.picci said:**
> Hi, i experienced the same issue and solved with the workaround suggested at the launchpad bug [#608382]("https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382"). This appears to be a bug known since past july that has not yet been fixed.
The workaround is very simple: open the file /syslinux/syslinux.cfg on your flash drive and remove the keyword "ui" in the last row. After this retry to boot; this worked for me.

Bye

Great thanks! works for my Meerkat..

---

### Post by hpladds on 2011-01-05
Worked for me too. With AMD Athlon 64 and Dual-core Atom processor machines. Please note that the "ui" must be deleted from /syslinux/syslinux.cfg NOT /syslinux.cfg.

---

### Post by rahul_bhise on 2011-09-27
> **luca.picci said:**
> Hi, i experienced the same issue and solved with the workaround suggested at the launchpad bug [#608382]("https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382"). This appears to be a bug known since past july that has not yet been fixed.
The workaround is very simple: open the file /syslinux/syslinux.cfg on your flash drive and remove the keyword "ui" in the last row. After this retry to boot; this worked for me.

Bye

thanks luca.picci deleting "ui" did it

---

