---
title: "Intel Wireless setup"
date: 2005-03-08
forum: Hardware &amp; Laptops
---

### Post by acaus on 2005-03-08
I am a novice to linux but want to make it work. However, I have no idea how to get my wireless to work on my laptop. I have a Toshiba A2 with an intel pro wireless card and centerio processor. Some very detailed idiot proof help would be greatly appriciated.
Ubunto is the best I have seen by the way!!!

---

### Post by alastair on 2005-03-08
Hard to say - you give no detail about what does not work, or what you have tried.

If I was starting from scratch, I would download and install a "Hoary" (latest dev) snapshot CD ISO image e.g.

[http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/5.04/array-6/hoary-install-i386.iso](http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/5.04/array-6/hoary-install-i386.iso)

See what happens at boot after an install. I have an Intel centrino thinkpad that seems to work. At boot, check the log files e.g.

/var/log/syslog

Look for lines mentioning "ipw" (the intel wireless chipset).

---

### Post by jerome bettis on 2005-03-08
i wouldn't bother with that.   there's three easier ways of doing it.

1.  there's a thread in the faq section that outlines this step by step.  probably check that out first.

2.  download the source file and firmware image from [http://ipw200.sf.net](http://ipw200.sf.net) and compile it. (move the firmware files to /usr/lib/hotplug/firmware and in the source directory, do: sudo make ;  sudo make install)... if you get any errors let us know.

3.  instead of compiling it, download the 2.6.10 kernel source from [www.kernel.org](www.kernel.org), go into the patches directory of the ipw2200 download, and patch / recompile the kernel as per the readme file.

good luck, any further questions just ask.

---

### Post by jliedeka on 2005-03-09
I just installed Warty on a new Vaio S270 and the Intel wireless worked out of the box.  You may want to check your boot messages to see if there are any problems.

     Jim

---

