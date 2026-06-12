---
title: "Disable thermal module of acpi in ubuntu 9.10"
date: 2009-11-05
forum: Hardware
---

### Post by NatalieG on 2009-11-05
Is it possible to disable the thermal module of acpi in ubuntu 9.10. And if so How?

I think it reads the incorrect temperature or the action it takes when it tries to cool down the machine (with the fans of course) causes a conflict in the machine thereby locking/freezing the machine.

The BIOS itself does enough of a job to keep the machine on temperature when needed, the OS doesn't need to assist it.

---

### Post by NatalieG on 2009-11-06
Bump

---

### Post by schiotz on 2009-11-06
You could try to recompile your own kernel, and leave out the thermal zone acpi support.  I have not tried to compile kernels under ubuntu, but essentially you need to install kernel-sources, go to /usr/src/linux, do a "make xconfig" or "make menuconfig", find the ACPI thermal zone module, disable it, save the new configuration, and then do a "make" followed by a "make install modules_install".  I **strongly** recommend googling for the detailed instructions for your version of Ubuntu.

**WARNING**: disabling thermal zone support may be dangerous.  If you BIOS does not turn on the fans, or if the kernel disables is support in the BIOS, you may permanently damage the processor! 

/Jakob

---

### Post by NatalieG on 2009-11-06
I already tested if the BIOS takes over the cooling and it does. If revs up when during heat producing operations en revs down when the system is idle

Mhhhh, a recompile is bit of a risk. I was hoping for a less destructive method. But I will investigate it.

---

### Post by schiotz on 2009-11-06
> **NatalieG said:**
> 
Mhhhh, a recompile is bit of a risk.

Absolutely!  It allows for anything from medium to king-size disasters :-)

Do make a boot CD first, take backups, and be prepared for the worst...

It is entirely possible that less drastic alternatives exist, but I do not know them.

---

### Post by prytoluk on 2010-08-21
OMG! I can't believe i've finally found a solution to my (your) problem.

I did this on Ubuntu 10.04, but it should work for any version:

To disable Acpi Thermal module withouth recompiling kernel:

Open up a terminal and do the following:
[COLOR=Red]cd /etc/default
sudo gedit grub[/COLOR]

Ok, after you insert you password it should pop the Gedit text editor, and there should be a line like this:
[COLOR=Red]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]

Change it to this:
[COLOR=Red]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash thermal.off=1"
[COLOR=Black]
Now you save the document.
Back in the terminal you do the following command:[/COLOR]
update-grub
[COLOR=Black]
Now reboot your PC and the thermal module won't be loaded.
I used this because ubuntu would cause me sudden thermal shutdowns with misread information AND my bios can mange the fans and thermal activity. If you realize that your pc is getting warmer, undo those steps! I don't want no burnt chips![/COLOR]
[/COLOR]

---

