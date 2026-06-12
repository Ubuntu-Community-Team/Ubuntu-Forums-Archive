---
title: "ubuntu X1950 problems"
date: 2008-05-01
forum: Hardware
---

### Post by iKar310 on 2008-05-01
After I installed ubuntu I noticed my resolution is bas as hell..so I went to Hardware drives  and I saw that my graphic card is checked but It says not in use and has a red lamp..how to activate her????

thx :((((

---

### Post by Jonothewright on 2008-05-01
I find that the easiest way to get the drivers right is with Envy. You can install it from Synaptic by searching for envy. I used the EnvyNG-core and envyng-gtk. Once it is installed look in applications>System Tools>EnvyNG. Launch it and let it do the Automatic install (unless you want to select a specific driver). It has worked for me every time. I hope it helps you.

Cheers

---

### Post by Riptr on 2008-05-01
Hello there.

I just came across this page in a search and I decided to try the Envy package with my Sapphire X1950 GT, I tried the package but when Ubuntu restarted I was presented with a completely black screen. 

Luckily, I managed to use Xfix from the GRUB boot-menu to at-least allow me to use Gnome-failsafe.

Is there any driver packages for the X1950 GT (AGP) graphics card which would allow Native Linux games like Quake 4 to run?

---

### Post by xMachina on 2008-05-13
Hi guys,

the X1950Pro AGP graphics card is a real pain to get going in Linux. Fortunately, some guy called Alastair over at the ATI bugzilla has figured out how to get it going by:

1) Follow the manual install option for the Proprietary ATI drivers at [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.4_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.4_Driver_Manually)

EXCEPT before rebooting, you also need to make sure the AGP memory listing matches up at 3 places, to avoid the "ATI black screen of death":

2) Look up exactly how much video RAM your card has, eg from the box, receipt, or the ATI control centre in windows (it will either be 256MB or 512MB). Fpr the instructions below I'll go with 512, but substitute as appropriate.
3) edit your /etc/X11/xorg.conf, and add the following line at the end of the fglrx device section:
>  Option      "MaxGARTSize"       "512"
4) edit your grub boot instructions for your kernel in the /boot/grub/menu.lst file, adding vmem=512 to your kernel boot line for your main kernel, e.g.:  
> 
title           Ubuntu 8.04, kernel 2.6.24-16-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.24-16-386 root=UUID=64fa7a1b-a8d7-45fb-a891-a81f3977bc13 ro quiet splash vmem=512
initrd          /boot/initrd.img-2.6.24-16-386

5) Ok, now reboot, but ENTER YOUR BIOS and look for the setting related to AGP memory, for me it was in the "Advanced Chipset Features" section. Change it to the same value as the others, eg 512MB.

...and that worked for me, ~1600 FPS in fg_glxgears ;) Haven't tried Compiz etc yet.

---

### Post by jam007 on 2008-06-14
I have problems with ATI Radeon Sapphire X1950 PRO 256MB.
After installation of ATI-drivers and restart it works for 1-5 minutes and then "Black Screen of Death". Uninstalling the drivers makes Ubuntu work again.
I have tried to add the lines in xorg.conf and menu.lst as suggested above. (Substituting 256 for 512). Without any success.
(PCI-Express buss, AMDx2 64, Asus M2N-E, Ubuntu 8.04)
Does anyone know how to get it to work? I would love to have 3D support under Linux.
(I am not familiar with kernels, X11 files etc.)

---

### Post by alexforcefive on 2008-06-14
For the AGP x1950, this guide is good: [http://www.linuxmint.com/forum/viewtopic.php?t=6317](http://www.linuxmint.com/forum/viewtopic.php?t=6317)

The important part is... 

> But before you reboot you need to blacklist a couple of modules.

Code: sudo gedit /etc/modprobe.d/blacklist


and add the following:

# EDAC modules to fix false PCI-E detection
blacklist i82875p_edac
blacklist edac_mc

---

### Post by jam007 on 2008-06-16
After removing the card, cleaning and reinstalling it. Restaring and installing the ATI drivers again everything worked fine and I got 3D and everything :) . Maybe it was an hardware trouble. (But the card worked under MS Visa...)

---

### Post by xMachina on 2008-06-17
Glad to hear you got it sorted jam007. I haven't seen the intermittent problem before with this card - maybe there was something weird with your previous driver install. Anyway, it works eh ;)

---

