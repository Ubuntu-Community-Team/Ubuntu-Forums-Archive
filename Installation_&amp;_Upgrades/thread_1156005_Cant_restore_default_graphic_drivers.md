---
title: "Cant restore default graphic drivers"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by ierpe on 2009-05-11
I installed ati drivers on a 9.04, and after reboot, the graphic driver ***** up...
I have a laptop lenovo z61m

to restore the default driver, I tried:

- the automatic recovery from the recovery mode menu
- aticonfig --initial -f (says no device found or smthg like that)
- dpkg-reconfigure -phigh xserver-xorg
- apt-get remove --purge xorg-driver-fglrx (says the package isnt installed)
- I removed the ati driver from /usr/lib/xorg/modules/drivers

And all this doesnt work. I installed the catalyst 9.4 driver.
Is there a way to restore the default ubuntu driver??

Please help im in distress here! :confused:

---

### Post by ierpe on 2009-05-11
Sorry to insist but I kinda need my system running in about an hour... anyone has an idea?

What is the command to start in low graphics mode, as Jaunty doesnt seem to give the option...

---

### Post by ierpe on 2009-05-11
Ok I understood my mistake and... omg

I was looking at the specs on the net for this laptop (its a laptop from work) when i was looking for drivers, and I saw 2 pages with ati graphic cards and I supposed it was an ati... but no! :-S

its an intel 945gm chipset! omg...

Any idea how to recover? please help

---

### Post by nghalion on 2009-06-24
Hello,

I have the same problem..did you figure out a solution??
Please help

---

### Post by Claus7 on 2009-06-24
Hello,

this is a quick one: either you should reinstall the necessary packages from synaptic or you should reinstall the drivers providing that you download them from intel's website. Try the first which is easier and if it doesn't work you have some work that should be done!

Regards!

---

