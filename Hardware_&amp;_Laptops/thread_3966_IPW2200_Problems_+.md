---
title: "IPW2200 Problems +"
date: 2004-11-10
forum: Hardware &amp; Laptops
---

### Post by Eklipz on 2004-11-10
I just finished a fresh installation of ubuntu on my Dell 600m laptop.  I've got an IPW2200 wireless card in it, but I seem to be having problems activating it.  I have modprobed the ipw2200 driver, but when I try to add my wireless card under the networking configuration wizard, it won't allow me to activate it.  Ive added it as wlan0, or as eth1, but neither work.  Ive entered my SSID correctly, as well as my WEP key.  I also have tried using DHCP and manual configuration.  Nothing I can do works.  Does anyone have any idea what is wrong?  Am I missing something?

---

### Post by knappen on 2004-11-18
Try:

modprobe firmware_class

Hope it helps.

---

### Post by skipsjh on 2004-11-18
There is something wierd with the parallel port blocking the wireless and the sound from working on 600m's and D600's.  Try either disabling the parallel port in the BIOS, or adding "acpi_irq_isa=7" to the boot command line.  Both of these tricks worked for me, with disabling the parallel port being the more permanent fix.

~Scott

---

### Post by macpilot on 2004-12-30
[QUOTE=skipsjh]There is something wierd with the parallel port blocking the wireless and the sound from working on 600m's and D600's.  Try either disabling the parallel port in the BIOS, or adding "acpi_irq_isa=7" to the boot command line.  Both of these tricks worked for me, with disabling the parallel port being the more permanent fix.

~Scott[/QUOTE]
 I tried both but it did not work, I can't get ipw2200 to show when adding an eth interfaceyu

---

### Post by labbe on 2004-12-30
You need to use the manual setting...
I have the same card and It's works now...
Take a reinstall and find everything you need and take it on the installation.
If you cant enable it, you have done some wrong.
Try to change IP adress...
Name of ruoter?
If its a dell I can help you.

---

### Post by jerome bettis on 2005-01-20
my ipw2200 is mapped to eth0 under ubuntu.  it was eth1 under debian.

try sudo iwlist eth0 scan and see what happens.

also i hope you're using the latest version of the driver from ipw2200.sourceforge.net

---

### Post by macpilot on 2005-01-21
the irq=7 worked in my dell d600, now how can I upgrade the ipw2200 I have downloaded the files from sourceforge but when I run
sudo make or make alone I get an error that says no rule to make

Any ideas would be appreciate it.

JN

---

