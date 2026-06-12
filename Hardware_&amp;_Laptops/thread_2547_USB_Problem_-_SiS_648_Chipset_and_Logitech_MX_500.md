---
title: "USB Problem - SiS 648 Chipset and Logitech MX 500"
date: 2004-10-29
forum: Hardware &amp; Laptops
---

### Post by Phreneticus on 2004-10-29
Hello,

I have a MSI MS-6701 (Medion OEM) Motherboard with a SiS 648 Chipset.

I thought that my Ubuntu Installation was succesfull but on first boot X was'nt able to load. I looked at the XF86Config-4 and found the problem fast. A SiS Grafics Driver was loaded but I don't have SiS Onbaord grafics I have an Ati Radeon. I changed the driver to Radeon and X loaded without Problem.

Now that the GUI worked my Mouse didn't work, again I looked in XF86Config-4 but didn't see something wrong than I bootet Fedora Core 2 and Kanotix und compared the XF86Config-4's and the Mouse entrys were exactly the same. But in Kanotix and Fedora my Logitech MX 500 pluged in USB works. I also looked in /dev if there is something with USB but did'nt find anything.

I'm still a newbie but have no fear from the command line. I hope someone can help me out with this problem cause I realy want to try and use Ubuntu. And I don't want to give up that easy.

Youres sincerely Phreneticus

PS.: Sry, for my bad english.

---

### Post by cacofonix on 2004-10-30
[QUOTE=Phreneticus]Hello,

I have a MSI MS-6701 (Medion OEM) Motherboard with a SiS 648 Chipset.

I thought that my Ubuntu Installation was succesfull but on first boot X was'nt able to load. I looked at the XF86Config-4 and found the problem fast. A SiS Grafics Driver was loaded but I don't have SiS Onbaord grafics I have an Ati Radeon. I changed the driver to Radeon and X loaded without Problem.

Now that the GUI worked my Mouse didn't work, again I looked in XF86Config-4 but didn't see something wrong than I bootet Fedora Core 2 and Kanotix und compared the XF86Config-4's and the Mouse entrys were exactly the same. But in Kanotix and Fedora my Logitech MX 500 pluged in USB works. I also looked in /dev if there is something with USB but did'nt find anything.

I'm still a newbie but have no fear from the command line. I hope someone can help me out with this problem cause I realy want to try and use Ubuntu. And I don't want to give up that easy.

Youres sincerely Phreneticus

PS.: Sry, for my bad english.[/QUOTE]

Would you be able to post your kern.log file from /var/log please

Thanks

---

### Post by Phreneticus on 2004-10-30
Here is my Kernel Log.

---

### Post by cacofonix on 2004-10-31
It looks like your suffering from bug number 1971 if you go [**here**](https://bugzilla.ubuntu.com/show_bug.cgi?id=1971)  it list the bug your having trouble with. You can get a kernel patch from there or if your not comfortable patching your kernel, you can turn of usb mouse support in your bios  (the patch should be in the next kernel released)

Cacofonix

---

### Post by Phreneticus on 2004-10-31
Firstof all thank u very much for your help cacofonix. I went du the page but wasn't able to find a Kernel patch there. I tried to turn of USB Mouse Support in my Bios but it lacks having this option the only option avaible was turning off usb keyboards, I tried it anyway but it didn't help. Since I can't use apt because of some w-lan problems I would prefer to have the pssibility to download the deb Packages by myself and install them. I hope someone could hive me a Link where I can find the latest precompiled Kernel for Ubuntu and his sources as deb packages.

---

