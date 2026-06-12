---
title: "Toshiba Satellite L505D-GS6000 ACPI Issues"
date: 2010-05-06
forum: Hardware
---

### Post by sicdrummer18 on 2010-05-06
I just updated from Ubuntu 9.10 to 10.4 on my Toshiba Satellite. After booting I get a bunch of random ACPI errors. When I was on 9.10, I used pci=noacpi as a boot flag and it worked with some problems such as, wireless, fan and I think my second core not working and no battery support, but pci=noacpi doesn't work for me in 10.4. I've also tried acpi=off, with no success.

Any help is appreciated.

Specs:

Toshiba Satellite L505D-GS6000
AMD Turion II Dual-Core Mobile M500 2.20GHz 64-Bit
4GB Ram
ATI Mobility Radeon HD 4200
Insyde H20 Bios

(More specs can be listed as needed.)

---

### Post by tjfitz on 2010-05-06
I'll add my two cents here.  I have a brand new, Toshiba Satellite L505D-LS5002 that came with Windows 7.  I  just finished installing Xubuntu from the x64 livecd, and all I get is a  page full of hex codes and gibberish (I think these are also acpi errors).  It's the same thing  that I got when I first booted from the livecd without specifying any  boot parameters.  To get the livecd to boot, I hit f6 and selected the  first three options (I think they disabled acpi, apic, and lapic).

---

### Post by sicdrummer18 on 2010-05-06
I've tried those. But I'm not looking into disabling things, I'm wanting it to work like its supposed to.

---

### Post by colinwhipple on 2010-05-06
Look in this message thread:

[http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d](http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d)

---

### Post by sicdrummer18 on 2010-05-07
> **colinwhipple said:**
> Look in this message thread:

[http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d](http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d)

Thanks for the suggestion, but I've seen that thread enough already. I really don't want to compile a kernel for a system that I have to use everyday for both school and work, just to be on the safe side.

---

### Post by tjfitz on 2010-05-08
> **sicdrummer18 said:**
> I've tried those. But I'm not looking into disabling things, I'm wanting it to work like its supposed to.
Yeah, me too!  (I wasn't posting as a suggestion, just as someone else having the same problem)

---

### Post by tjfitz on 2010-05-08
I'm not interested in recomiling anything either.  For one thing, I'd have to actually get a successful boot to do so.  I'd rather go back to Windows 7.  But really, I'd rather just have Ubuntu working like it should.

---

### Post by dino99 on 2010-05-08
into synapic, repo tab, add :
[COLOR="Blue"]ppa:ubuntu-x-swat/x-updates[/COLOR], validate, update and upgrade

then, install a recent kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/)

howto:
 in that strict order, by double clicking on the packages ( need gdebi to be installed):
** linux-source....all.deb
** linux-headers...all.deb
** linux-headers (choose i386 or amd64)
** linux-image (choose i386 or amd64)

then reboot with this kernel

---

### Post by sicdrummer18 on 2010-05-10
Thanks for the help everyone.

But, after compiling and installing custom kernels, installing patches and trying all other suggestions given to me, I've decided to just give up and go back to Windows. At least I know that works.

---

### Post by sicdrummer18 on 2010-05-11
I decided to try a few more times. But absolutely everything I've tried has failed. Has anybody found a Patch or kernel that will work with a Toshiba Satellite L505D-GS6000?

---

### Post by corelulos on 2010-05-25
> **dino99 said:**
> into synapic, repo tab, add :
[COLOR=Blue]ppa:ubuntu-x-swat/x-updates[/COLOR], validate, update and upgrade

then, install a recent kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33.3-lucid/")

howto:
 in that strict order, by double clicking on the packages ( need gdebi to be installed):
** linux-source....all.deb
** linux-headers...all.deb
** linux-headers (choose i386 or amd64)
** linux-image (choose i386 or amd64)

then reboot with this kernel

I have the same laptop, GS6000, tried the above. same results,  acpi=ht in boot menu didn't work either, what next?
* I found this script <[http://ubuntuforums.org/showpost.php?p=9357919&postcount=268](http://ubuntuforums.org/showpost.php?p=9357919&postcount=268)   that made the whole install work.  I now have a working Lucid on my L505D-GS6000!
Had to do a little cleanup of the couple previous attempts to get it to work but that was no biggie...

---

### Post by waffleboi9 on 2010-05-25
> **corelulos said:**
> I have the same laptop, GS6000, tried the above. same results,  acpi=ht in boot menu didn't work either, what next?
* I found this script <[http://ubuntuforums.org/showpost.php?p=9357919&postcount=268](http://ubuntuforums.org/showpost.php?p=9357919&postcount=268)   that made the whole install work.  I now have a working Lucid on my L505D-GS6000!
Had to do a little cleanup of the couple previous attempts to get it to work but that was no biggie...

Hey corelulos, thanks for confirming that 10.4 works on the L505D-GS6000. I was looking at laptops today, but I almost changed my mind when I was reading about these issues. I'm going to take the plunge and buy it now. Thanks!

But just to clarify, now that you've been through it, was is the minimal, most concise set of steps to get this working? Do I just attempt a normal install, then run hex0r's script? Did you have any problems booting the first time?

Thanks! K

---

### Post by jcer93705 on 2010-05-26
> **sicdrummer18 said:**
> I just updated from Ubuntu 9.10 to 10.4 on my Toshiba Satellite. After booting I get a bunch of random ACPI errors. When I was on 9.10, I used pci=noacpi as a boot flag and it worked with some problems such as, wireless, fan and I think my second core not working and no battery support, but pci=noacpi doesn't work for me in 10.4. I've also tried acpi=off, with no success.

Any help is appreciated.

Specs:

Toshiba Satellite L505D-GS6000
AMD Turion II Dual-Core Mobile M500 2.20GHz 64-Bit
4GB Ram
ATI Mobility Radeon HD 4200
Insyde H20 Bios

(More specs can be listed as needed.)

I have a quetion because I might get the same laptop u have for 499 at best buy but i have to know, did youre laptop came with hdmi and did you're ati was detected by the os? Did you got accelerator working?

---

### Post by waffleboi9 on 2010-05-28
Thanks corelulos! Everything worked great. To summarize:

for L505D GS6000

Install 10.4
Boot with pci=noacpi
Run HexOr's script found here: [http://ubuntuforums.org/showpost.php?p=9357919&postcount=268](http://ubuntuforums.org/showpost.php?p=9357919&postcount=268)
Get wifi drivers from here (thanks corerlulos!): [http://www.4shared.com/file/crG9xUGH/realtek_drivers_and_instructio.html](http://www.4shared.com/file/crG9xUGH/realtek_drivers_and_instructio.html)

Thanks everyone! I have 10.4 working on my Toshiba Satellite L505D GS6000, with everything fine, power controls, trackpad, wifi now.

---

