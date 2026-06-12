---
title: "Wron GPU info in Ubuntu!"
date: 2009-03-11
forum: Hardware
---

### Post by MivloV on 2009-03-11
Hello people!

I have a weird problem. I have just installed "Ubuntu 8.10" on a "Zepto Mythos A15" laptop with a "GeForce 9650M GT" video card.

The thing is that when I look in the "Nvidia X Server Settings" or use "lspci" the GPU information is wrong. It says "GeForce 9300M GS" instead of "GeForce 9650M GT". Why is that and how can i fix it?

I have the nvidia 177 driver installed.

---

### Post by avilella on 2009-04-13
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

If you have access to any of the laptops below and have tried to run Linux, please take a moment to provide the DSDT information for the laptop in this link:

[http://bugs.launchpad.net/bugs/312756](http://bugs.launchpad.net/bugs/312756)

Sony Vaio Z-series (intel/nvidia)
Fujitsu Siemens Amilo XI 3650 (intel/nvidia)
BenQ Joybook S42 (intel/nvidia)
ASUS N10J (intel/nvidia)
Dell Studio XPS 13 (nvidia/nvidia)
ASUS Intros G71Gx (?/nvidia GeForce 260M)
MSI GT628 (?/nvidia GeForce 160M)
LG Xnote P510 Laptop (?/nvidia GeForce GT 130M)
HP HDX 18t (?/nvidia GeForce GT 130M)
Dell XPS M1730 (nvidia/nvidia)
MSI EX630 (nvidia/nvidia -- )
Toshiba Qosmio X305-Q706/Q708 (nvidia/nvidia -- 9400m + 2x9800m GTS)
Acer Aspire 7530 (nvidia/nvidia -- 9100M G + GeForce 9300M GS)
ASUS X83Vm-X1 (?/nvidia)
+ Clevo M860TU (?/nvidia GeForce 9800M GTS)
+ Acer Aspire 8930G (?/nvidia GeForce 9700M GT)
+ Asus G50V (?/nvidia GeForce 9700M GT)
Zepto Mythos A15 (?/nvidia)
Lenovo ThinkPad T500 (intel/ati)
Lenovo ThinkPad T400 (intel/ati)
ASUS M51Ta (intel/ati)
Fujitsu-Siemens Amilo Sa 3650 (intel/ati)
MSI PX211 12'' (intel/ati)
HP Pavilion tx2500 (intel/ati)

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:
sudo apt-get install acpidump iasl           # on Debian-based systems

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug report. This information will allow the developers to fully implement the hybrid graphics features for Linux.

---

