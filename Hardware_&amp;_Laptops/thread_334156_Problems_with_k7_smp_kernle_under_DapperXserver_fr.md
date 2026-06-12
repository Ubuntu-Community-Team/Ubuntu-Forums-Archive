---
title: "Problems with k7 smp kernle under Dapper/Xserver freez"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by bastardop on 2007-01-08
Hello
@first i say sorry for my bad english but i give my best.
no to my problem. I've got an AMD Athlon64 X2 3800+  now i wnat my Dapper Drake to support both Cores and installed the k7-smp kernel. The system also starts but after a while my Xserve doenst react to my mouse actions and i must restrat the Xserver. With an i386 Kernel my System works. I've also tried out the 64 bit version with a k8 Kernel this configuration also works but i do not like thze 64bit version.
Under Edgy Eft i have got the same Problem.
I use the nvidia-glx driver for my graphic card.

I hope you can help me with my Problem please.


MfG
Bastardp

---

### Post by hal10000 on 2007-01-08
Did you install the linux-restricted-modules package corresponding to your kernel version?
try [COLOR="Red"]dmesg | grep nvidia[/COLOR] in a terminal window.
The output should look like 

nvidia: module license 'NVIDIA' taints kernel

If you get no output at all, then you have to install the correct restricted-modules package and presumably reconfigure your graphic settings or edit your /etc/X11/xorg.conf file. ([COLOR="Red"]sudo gedit /etc/X11/xorg.conf[/COLOR]). The relevant part looks like:

```

Section "Device"
        Identifier      "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
        Driver          "nv"
        BusID           "PCI:5:0:0"
EndSection

```
change only the Driver entry to
```

Section "Device"
        Identifier      "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
        Driver          "nvidia"
        BusID           "PCI:5:0:0"
EndSection

```

---

### Post by bastardop on 2007-01-08
i have installd the resricted modules for both kernel versions and in my xorg.conf i hav the nvidia driver. I Also get a GUI with the k7-smp kernle but after a wihle the GUI doesn't react to that what i do with my mouse. The Arrow moves but theres i no reaction to my  clicks  just Crtl+Alt+Bacpsace  works to restart the Xserver and then  i freezes after a while again.is it possible that the k7-smp kernel hast got problems with the nvidia-glx (i've got a Nvidia GeForce 7300 Gt)
when i type 
dmesg | grep nvidia
with the i386 kernel i got no output even i use the nvidia driver in xorg.conf and have installed the restricted modlues
this is the output of 
dmesg | grep NVIDIA
[   42.013480] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006

---

### Post by hal10000 on 2007-01-08
I don't use a smp kernel, but i've never heard of problems with it.
Maybe you should install (and compile) the latest nvidia driver from nvidia's website, the release number is 1.0-9746.
If you do so, take in mind that you have to install this driver from the command line (without a running xserver) and that you need to have some some packages installed (xorg-dev, binutils, gcc, linux-headers and maybe others too)

---

### Post by bastardop on 2007-01-09
okay i thhink i would test the originial nvidia drive this week and would look if it runs.
The 686-smp kernel would only work with Pentium or?

---

### Post by bastardop on 2007-01-10
so today i tried the nvidia driver from the website. With the K7 kenrel it doesn't works it is the same situation as before and i found out that the driver from the nvidia isn't an alternative for me because i need the resriced modules but thex dont't work't eith the driver.

Another Point is that i boot my kernel with acpi=off is that possible a reason fpr the failuer? For one week i still have the option to send the mobi back and get another one.

Please Help my


Bastardop

---

### Post by az on 2007-01-10
> **bastardop said:**
> Hello
@first i say sorry for my bad english but i give my best.
no to my problem. I've got an AMD Athlon64 X2 3800+  now i wnat my Dapper Drake to support both Cores and installed the k7-smp kernel. Bastardp

Did you install the linux-image-k7-smp package or

sudo apt-get install linux-k7-smp?

You need to do the linux-k7-smp package, and not just the kernel image package.   You only need linux-k7, since linux-k7-smp will install the same kernel.  The k7 kernel is already smp.

---

### Post by bastardop on 2007-01-10
i have installed the meta package linux-k7-smp in synaptic  when i searv for linux k7 i have the header the image and the resricted modules installed all for kenrle 2.6.15.27

i hope i get my system to run with the dual core

---

### Post by hal10000 on 2007-01-10
If you compiled and installed the latest nvidia driver from the nvidia website you don't need restricted modules anymore.

But take in mind that every time you change the running kernel, you then have to compile the driver again for that running kernel.

Perhaps you may delete the acpi=off option.

---

### Post by bastardop on 2007-01-10
i need the resritced drivers for my FritzCard and CAPI
i can not delet acpi´off because the the kernel doesn't boot i try without and with noacpi  and i became a kernel panic then with the k7 and the i386 kernel.
in the kernel log i also found nothing @the point when the Xserver frezze.

---

