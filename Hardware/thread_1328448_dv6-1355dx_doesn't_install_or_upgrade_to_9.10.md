---
title: "dv6-1355dx doesn't install or upgrade to 9.10"
date: 2009-11-16
forum: Hardware
---

### Post by iiretepii on 2009-11-16
I've been looking around the forums for an answer to this question but couldn't find it.  I recently bought an hp dv6-1355dx because the hinge on my gateway broke and... yada yada... when I downloaded the 64-bit karmic live CD it showed the main screen with the options for things the CD can do.  When I selected install Ubuntu, the screen flashed and then there was nothing.... the screen was black and my CD-rom was working like a mad fiend sort of like it was preparing the installation.


VIVA LA/EL UBUNTU!,
Pete

---

### Post by iiretepii on 2009-11-16
i wonder how long it usually takes to get a reply?

---

### Post by Squonk07 on 2009-12-10
Are you sure the disc you made is good? I know it sounds a little like needling, but I have this exact same computer and have installed 64-bit Karmic without a problem. In fact, I was extremely impressed with just how well Karmic works on this machine.

I installed from a USB flash drive; I stopped wasting discs for Ubuntu installs around about 8.10 Intrepid Ibex. If possible, give that a try and see if that helps.

---

### Post by henrycoule on 2009-12-17
I have this same HP DV6-1355dx and I am unable to install ubuntu on it. This is what happens. When I use Live CD or USB I can select install ubuntu on this computer or try ubuntu without installing. Thats it from this point my LCD screen becomes blank.  I do not see anything again but i can hear the login sound after LIVE CD or USB startup gets to the desktop but nothing is displayed. Why is this?

---

### Post by stblack on 2009-12-21
I can confirm your problem on my DV6-1323.
9.04 works fine, 9.10 dan't be installed.
The Cd it's good, with VirtualBox works fine.

Bye
Stblack

---

### Post by henrycoule on 2009-12-21
> **stblack said:**
> I can confirm your problem on my DV6-1323.
9.04 works fine, 9.10 dan't be installed.
The Cd it's good, with VirtualBox works fine.

Bye
Stblack

Yes with my Vmware it works fine but never on the system itself without Vmware. Is there an issue with this HP dv6 and Ubuntu? or Linux?

---

### Post by shilo on 2010-01-06
To fix the issue with installation:

1) Boot the Live CD
2) press f6.  You don't need those options, though, so press esc
3) down arrow to the install option
4) you see the boot command.  You need to fix it.  press backspace to get rid of the --
5) type ```
nomodeset
``` after quiet and splash.

I made a few other changes after install.  My /etc/default grub looks like this, now:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=2
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
GRUB_DISABLE_LINUX_RECOVERY="true"
```It may also help to know that HDMI output works even without fixing the screen.  I actually installed Ubuntu with an external monitor before learning the nomodeset command.

---

### Post by henrycoule on 2010-01-08
I got Lucid which works good without issues. I think 9.10 Karmic has issues with the display which it doesnt say

---

### Post by mad2ogs on 2010-03-31
Hey,

I have this same note dv6-1355dx. I installed karmic fine and it works very nice. My question here is if any of you has tried installing any other linux ou unix system on it. 

I tried debian and it gave me a kernel panic!
I tried fedora and it freezes during the instalation
I tried FreeBSB and it mest up totaly my harddrive, i had to take it out e plug it in a portable case to restore mbr. 

Well, just to see if anybody has gotten other systems working on it.

I updated my bios before i tried all this.

thanks to all

---

### Post by dma88 on 2010-04-15
I just got a dv6, been having the exact same problem.  I tried the nomodeset fix, and it worked- for a while.  the logo was on the screen for a few minutes and it's reading from the cd.  Then a screen of code, then it goes black again.

The only difference is, when it goes black, it stops reading from the cd and it stops booting.  When I was watching it boot up with a black screen earlier, it must have gotten all the way to the desktop.  I could press ctrl-alt-del, then enter, and it restarted.  It ejected the cd and waited for me to press enter, then it shut down.

but now with the nomodeset fix, it works for a while, but it stops booting once the screen goes black.  no reading from the cd, no ctrl-alt-del, no rebooting.  is there a fix for the fix?

---

