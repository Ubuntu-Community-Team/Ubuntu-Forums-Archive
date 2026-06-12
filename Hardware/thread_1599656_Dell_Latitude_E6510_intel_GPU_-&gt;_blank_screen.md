---
title: "Dell Latitude E6510 intel GPU -&gt; blank screen"
date: 2010-10-18
forum: Hardware
---

### Post by dvandyck on 2010-10-18
Hi all,

This thread concerns the graphics problems on the Dell Latitude E6510 with intel GPU. The problem is partially discussed in the thread on the similar problem for the Dell Latitude E6510 with an Nvidia Card, but for that configuration the problem is solved, see:

  [http://ubuntuforums.org/showthread.php?t=1582154](http://ubuntuforums.org/showthread.php?t=1582154)

I first installed Ubuntu 10.04.01 (64 bit). I could install graphically without problems, first   boot without problems but after installing updates every thing I did   yielded a black screen (including recovery-mode or using "text" as boot   option --even with the previous kernel which worked fine at first boot). 

Afterwards I installed 10.10 hoping the problem would be fixed. At first, things looked worse as the install DVD booted immediately with a blank screen, which worked fine on 10.04.01. Strangely enough, I could perform the install grapically by pressing F6  and using the "nomodeset" option provided by the installer. I do not  understand why the installer can do its thing graphically but I cannot  boot graphically even with the "nomodeset" option -- why is the working  graphics configuration DURING installation not used AFTER installation? 

I tried several boot options without success (always blank screen, no cursur, no mouse pointer). Using
 nomodeset -> I can login in text mode, no X
 i915.modeset=0 xforcevesa -> I get text on CTRL-ALT-F7 but no  graphics and can switch to terminals using CTRL-ALT-F1 to F6 (I cannot  do this if I boot normally)
 
My graphics card is the intel i915 integrated graphics card. It is reported as
"Intel Corporation Core Processor Integrated Graphics Controller (rev 02)"
by lspci.

I assume it is a i915 chipset because I get the following error message during boot:
"intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled"

It appears to be a known bug:

[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/600453]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453")

which also describes a temporary solution by using  the vanilla 2.6.36-rc6 kernel with the following patch:

 [https://bugs.freedesktop.org/attachment.cgi?id=38868](https://bugs.freedesktop.org/attachment.cgi?id=38868)

A more technical discussion of the problem can be found in the following bug report:

[https://bugs.freedesktop.org/show_bug.cgi?id=29278](https://bugs.freedesktop.org/show_bug.cgi?id=29278)

I welcome a fairly easy non-hacker solution using an official Ubuntu kernel. 

I am hoping for a quick bug fix in the first kernel update of 10.10 or a simple solution not involving a patch and recompilation of an unofficial kerne (as the one above)l.

kind regards

Dries

---

### Post by rolfje.com on 2011-02-02
I just received a Dell e6510 witn the Intel GPU as my new work laptop and I noticed the same problem. I got Ubuntu installed with the "alternative" disk because I needed full disk encryption (why that's not a part of the default installer disk baffles me).

Booting intu Ubuntu graphical user interface always fails, black screen, as described. Pluging in an external monitor helps, but I never seem to be able to get both the laptop panel and the external panel turned on simultaniously.

I installed the latest updates last friday, and I was sad to see that the simple fix (adding a few ms wait statements here and there) are still not part of the latest kernel distributed with Ubuntu.

I heard it was fixed and then un-fixed in a later kernel, and then re-fixed :-) Any news on when we get the kernel with the re-applied fix in it?

I'd really like to use Ubuntu at work. I like Windows 7 over XP, but I like to have 100% control over who accesses my data and what my machine does even more.

---

### Post by ptorpman on 2011-02-03
Hi,

After nearly going insane installing 10.10 on the E6510, I managed to get something workin at last.

What I did was:

[LIST=1]
[*] Install the amd64 debs located in: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc4-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc4-maverick/)
[*] Edited /boot/grub/grub.cfg and removed quiet and splash. Instead I added nomodeset and xforcevesa.
[*] In the console I generated a xorg.conf file (Xorg -configure) and copied the new file to /etc/X11/xorg.conf. 
[*] I changed the driver in xorg.conf to vesa and added some modes that might fit my screen. E.g Modes "1920x1080"
[/LIST]

Now I can see the something on my laptop - before it was just blank as for you guys...

There are still some problems though.. Sleep and Hibernate does not work at all for me... So the computer needs to be either on or off...

I am pretty annoyed about the fact that this graphics chip is not supported. And it seems like the 11.04 will not contain any fix for it either... 

I'll try this setup out for a while and see if it will be OK to use at work, but if it doesn't I will have to change to Window$ 7 and run Ubuntu in VirtualBox or something like that... 
To be frank with you, that would suck!

Cheers,
- Peter

---

### Post by ptorpman on 2011-02-03
After I had gotten my screen up with 10.10, I figured what the hell and updated to 11.04... 

I also set the /etc/default/grub variable GRUB_CMDLINE_LINUX_DEFAULT="nomodeset xforcevesa acpi=off" ...

And I got pretty amazed that it actually booted up... 

It looks nice, but I have only run it for a short while, so I can't give you any more in-depth status than this...

It works! (so far)

/ Peter

---

