---
title: "HELP:  9.10 Shutdown/Restart issues (Its either one or the other depending on change)"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by WildSioux on 2009-11-02
I have installed Kubuntu 9.10 a few days ago on a different partition since I have LinuxMint 7 (Jaunty) KDE CE installed on another one.  Everything went well during install.  So far 9.10 runs smoother and faster than the Mint KDE CE with jaunty.

SYSTEM:  6 year old Gateway Desktop Intel Pentium 4, 1g ram, 80gb HD, NVIDIA 8400GS PCI card with 190.42 driver running.

The problem is, I can either fully shutdown but no restart.  Or fully restart and no shutdown.  Here is what the break down is (depending on changes made)...

Fresh 9.10 install (no changes made to grub, modules, halt, etc...).
Shutdown (from KDE gui) = YES
Restart (from KDE gui) = No, hangs with error **8262.0883491 Restarting System** (holding power button allows me turn off).

From that I searched and have changed a few things with acpi stuff in **/etc/default/grub in this line:**
```
GRUB_CMDLINE_LINUX="pci=noacpi"
```
RESTART = NO
SHUTDOWN = YES

```
GRUB_CMDLINE_LINUX="acpi=off" 
```
RESTART = YES
SHUTDOWN = NO

After making each of those changes, I updated grub with:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

Again, without any of those changes, I can SHUTDOWN, but not RESTART.

I also tried this (found in another thread)
```
sudo gedit /etc/init.d/halt

Add the following line to the top of the halt script:

rmmod snd-hda-intel
```

This didn't help my shutdown problem.  During shutdown, it will either hang with the Kubuntu splash.  Or it gets past it and throws up this error in text:
```
xxxx.xxxxxx System halt
```  Or something like that.  It acts like it is being shut down because the fans and HD clicks "off."  But clearly, the fans, and HD are still spinning.  When it hangs like that at shutdown...pushing the power button turns it off.

I should note, I have never had any issues like this in the Jaunty kernel.  At this point, I am at a loss.  I have removed any changes from grub and others.  This allows me to at least shutdown.  I can live with not being able to restart for now...(hopefully a fix comes out real soon).

Please help...Thank you!

---

### Post by WildSioux on 2009-11-02
I have found the fix (I hope) for this problem of being able to shutdown but not restart.  I say "I hope" because I have shutdown and restart the computer a few times now and it seems to be working.  Here is what I did after searching for a while with no fix or help except this.

[http://www.linuxquestions.org/questions/linux-newbie-8/weird-issue-when-restarting-ubuntu-9-737358/](http://www.linuxquestions.org/questions/linux-newbie-8/weird-issue-when-restarting-ubuntu-9-737358/)

I was getting this same error (just a different number).
> 801.648244]
Restarting System



I found it had nothing to do with acpi settings in grub.  Because when I added acpi=off or one of the other acpi lines...It allowed me to restart, but now it froze while shutting down.

That thread also had something in there about a "reboot" fix.  This solved my problem...
```
"reboot=b"
```

**I added that to /etc/default/grub**
Changed this line from:
```
GRUB_CMDLINE_LINUX=""
```

to:
```
GRUB_CMDLINE_LINUX="reboot=b"
```

After making that change, I did this:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg

```

I am now able to shutdown and restart without problems!!!  ;D

---

### Post by soma123 on 2009-11-04
> **WildSioux said:**
> I have found the fix (I hope) for this problem of being able to shutdown but not restart.  I say "I hope" because I have shutdown and restart the computer a few times now and it seems to be working.  Here is what I did after searching for a while with no fix or help except this.

[http://www.linuxquestions.org/questions/linux-newbie-8/weird-issue-when-restarting-ubuntu-9-737358/](http://www.linuxquestions.org/questions/linux-newbie-8/weird-issue-when-restarting-ubuntu-9-737358/)

I was getting this same error (just a different number).


I found it had nothing to do with acpi settings in grub.  Because when I added acpi=off or one of the other acpi lines...It allowed me to restart, but now it froze while shutting down.

That thread also had something in there about a "reboot" fix.  This solved my problem...
```
"reboot=b"
```**I added that to /etc/default/grub**
Changed this line from:
```
GRUB_CMDLINE_LINUX=""
```to:
```
GRUB_CMDLINE_LINUX="reboot=b"
```After making that change, I did this:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg

```I am now able to shutdown and restart without problems!!!  ;D


Thanks but it doesn't help completely. I am able to restart but during shutdown , it is giving the same I/O errors and then hanging :(

---

### Post by soma123 on 2009-11-04
Hi,
coment #19 in  [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589)  fixes this problem.

Cheers!!

---

