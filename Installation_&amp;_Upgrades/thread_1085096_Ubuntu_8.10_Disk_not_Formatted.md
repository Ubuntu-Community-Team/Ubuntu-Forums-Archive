---
title: "Ubuntu 8.10 Disk not Formatted"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by jumby on 2009-03-02
I just today got my 8.10 UBUNTU install CD, i put it into my laptop CD drive, it spins, makes some noise, but nothing comes up, so i then go to my computer and click on CD drive and it says the disk is not formatted, or its a format windows cant read. I installed on my mums computers, but i dont know if that has completely worked. Is it something wrong with my CD or laptop?

Toshiba Satellite L25 S1193
1.5gb ram
6gb freespace
windows xp

---

### Post by Rallg on 2009-03-02
I once had a problem reading an install CD on a particular computer. Perhaps different CD drives are better than others.

Did you say that you were able to install Ubuntu on a different computer? If the installation completed successfully, then it is likely to be OK. If so:

On the other computer, place the CD in its slot. Do not run it. Instead, copy its contents to a single, large *.iso file and put the file on the Desktop. (I believe that the Brasero program can do this, but I am not sure.)

You can then burn the *.iso file to a new CD, and try that one in your own computer.

Or, if both computers have USB, and your own computer can boot from USB: In Ubuntu, go to menu system - Administration - Create a USB startup disk. Put a minimum 1Gb USB in the slot. Use the *.iso file to put bootable live Ubuntu on the USB.

If that works, then insert the USB in your own computer, and at boot time choose to boot from USB. Be patient. After ubuntu loads, you can use it to install.

---

