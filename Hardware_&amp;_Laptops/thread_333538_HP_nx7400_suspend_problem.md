---
title: "HP nx7400 suspend problem"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by psi36 on 2007-01-07
I'm running Ubuntu 6.10 (32 bit version for now) my HP nx7400 notebook I just bought..
There seem to be a few minor problems, returning from Suspend being the worst.
 
The explanations on [https://wiki.ubuntu.com/LaptopTestingTeam/HPnx7400](https://wiki.ubuntu.com/LaptopTestingTeam/HPnx7400), [http://emisca.altervista.org/nx7400/](http://emisca.altervista.org/nx7400/) and [http://home.no/slazz/nx7400/](http://home.no/slazz/nx7400/) don't help much, because different problems, specs and bios. 

My system:
bios-version:68YGU Ver. F.08
system-manufacturer:Hewlett-Packard
system-product-name:HP Compaq nx7400 (RH399EA#UUG)
system-version:F.08
kernel: 2.6.17-10-386

When i use Suspend, I can't restart. If I press the power button, the fans start working again and the power light is on, but the screen stays black. 
This doesn't seem to be the "bad state" problem that is mentioned on above websites.

When I select Suspend in Ubuntu, is that a suspend to disk? And when I do Hibernate is that suspend to ram?
Hibernate works fine. I sometimes get a message about a synaptics error before I come back to the logon screen, but everything works fine, also the touchpad.

Also some other small issues: the volume buttons (mute, down, up) and the special keys like fn + f3 for Suspend sometimes don't work. I did a reboot and now the problems gone, but would still like to know the cause of the problem.
The button to (de)activate WiFi and Bluetooth isn't working at all.

If anyone knows how to fix these problems, please let me know.

---

### Post by scrooge_74 on 2007-01-07
Check this out

[http://www.ubuntuforums.org/showthread.php?t=237264&highlight=suspend+hibernate+howto](http://www.ubuntuforums.org/showthread.php?t=237264&highlight=suspend+hibernate+howto)

[http://www.ubuntuforums.org/showthread.php?t=321369](http://www.ubuntuforums.org/showthread.php?t=321369)

---

### Post by psi36 on 2007-01-10
Might try that, but I don't think this is the solution for me.> **derekbei said:**
> Basically when the system bios is too old to support the newer ACPI power management, enabling the older APM power management will give you much better functionality.Since I already have the most recent bios, only a couple of months old, I don't think it's the same type of problem.

In the mean time I've installed the 64 bit version of Ubuntu 6.10 and now Hibernate isn't working either. Well Hibernate works, but I can't return from Hibernate.

---

### Post by psi36 on 2007-01-10
I tried the suspend script on [http://www.linux.com/article.pl?sid=06/05/24/1716222](http://www.linux.com/article.pl?sid=06/05/24/1716222) but when I run it my laptop doesn't suspend, but just leaves x an goes into a command line mode... Isn't helping me...

---

### Post by scrooge_74 on 2007-01-10
Any of the threads I gave you worked for you?

---

### Post by psi36 on 2007-01-11
The first one tells how to switch off ACPI and use APM, but I have a recent BIOS that should support ACPI, so that's no use to me. Hibernate worked on my laptop with the 32 bit version of Ubuntu 6.10, so I don't see the use in disabling ACPI.

The second thread first explains how to edit /etc/X11/xorg.conf for users of an nVidia card. I have an Intel integrated graphics card and already added the option "VBERestore" "true".
In /etc/default/acpi-support the line ACPI_SLEEP=true was already uncommented and I cahneged POST_VIDEO to false, but that doens't seem to change anything.

I also tried the two links on the bottom of the second thread, but I don't feel like running a patched kernel and I don't know if there's one for 64 bit. And I made the /usr/local/sbin/suspend.sh script as explained in the linux.com article, but it didn't suspend. It just got me into a non graphical interface.

Hiberanate worked in the 32 bit version of Ubuntu 6.10; but now that I'm using the 64 bit version it doesn't anymore. And even when I close the lid, whitch should only disable the screen, I can't use mouse or keyboard anymore when I reopen it.

---

### Post by psi36 on 2007-04-12
Still having this problem. It is quite annoying actually. And none of the solutions I've tried work for me. I am a bit stuck here...

---

