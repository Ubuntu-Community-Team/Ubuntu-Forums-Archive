---
title: "[HOWTO] Dothan Support in Breezy (Kernel 2.6.12) (Pentium-M, Centrino, vcore, clock)"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by C38a7r1zvl on 2005-10-14
If you are getting errors like "Error inserting speedstep_centrino (/lib/modules/2.6.12-9-686/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device" while trying to get full speedstep support for your Pentium M Dothan, you most likely need to patch your kernel. It's quite easy, here's a small walkthrough:

1. Download the sources (sudo apt-get install linux-source-2.6.12)
2. cd /usr/src
3. tar xfj linux-source-2.6.12.tar.bz2
4. ln -s linux-source-2.6.12 linux
5. cd linux
6. cp /boot/config-2.6.12-9-686 .config
7. apply [this patch]("http://localhost.ruhr.de/~stefan/acerTM292/patches/cpufreq-speedstep-dothan-3.patch") to the sources
8. make-kpkg --initrd --append-to-version "-yourPostfix" --revision 1 kernel-image
9. sudo dpkg -i ../kernel-image-2.6.12-yourPostfix_1_i386.deb
10. reboot
11. sudo modprobe speedstep-centrino if it isn't loaded automatically

For further optimization (read: longer battery life, less noise, less heat) you can directly change the cpu voltage in speedstep-centrino.c. For reference here's the relevant part of my speedstep-centrino.c for my 1.8ghz processor:

> 
static struct cpufreq_frequency_table dothan_1800[] =
{
        OP( 600,  700,  700,  700,  700),
        OP( 800,  748,  748,  748,  748),
        OP(1000,  812,  812,  812,  812),
        OP(1200,  860,  860,  860,  860),
        OP(1400,  908,  908,  908,  908),
        OP(1600,  956,  956,  956,  956),
        OP(1800, 1036, 1036, 1036, 1036),
        { .frequency = CPUFREQ_TABLE_END }
};


The first number indicates the cpu frequency in mhz, the following four numbers the voltage. As far as I know currently only the third one is read, but you are on the safe side if you set them all to the same value.

If your system hangs after changing the vcore, you set it to low. Boot your old kernel and recompile with more conservative values :)

dunno, why the kernel guys don't directly include this patch as dothan has been around for months..

---

### Post by vayu on 2005-10-23
The patch shows 715, 725, 735, etc...   Is it the same for the 730?

---

### Post by moerl on 2005-10-23
Hmmm.. I'm using the 686 kernel.. should I install this one instead? I'm not seeing any errors/problems with 686 but was alwasys wondering if there was a kernel made specifically for Dothan equipped systems..

---

### Post by bryan986 on 2005-10-24
[QUOTE=moerl]Hmmm.. I'm using the 686 kernel.. should I install this one instead? I'm not seeing any errors/problems with 686 but was alwasys wondering if there was a kernel made specifically for Dothan equipped systems..[/QUOTE]

I am using the stock 686 kernel with my inspiron 9300/dothan processor, I can switch between 800mhz, 1.07ghz, 1.33ghz, 1.6ghz

---

### Post by moerl on 2005-10-24
I was just wondering... would I benefit from installing the kernel discussed in this thread over the Linux-686 kernel that I already have installed?

---

### Post by GoodPanos on 2005-10-24
Does this involve the 740 (1.73GHz) too?

**bryan986** how are you able to switch between processor speeds?

---

### Post by bryan986 on 2005-10-24
You can change it with the cpufreq panel applet, but first you must give that applet the root bit so it has access to change the stuff

```

sudo chmod +s /usr/bin/cpufreq-selector

```

Then click on the cpufreq applet and it should open a menu for you, edit the applet's preferences to choose what it shows

You may have to re-add the applet to get it to work

---

### Post by GoodPanos on 2005-10-24
Sorry, but I'm a bit puzzled.  Which *cpufreq applet* is this?  Where do you access this applet from?  If not present where can I get it?

---

### Post by emendelson on 2005-10-24
Right-click on the top-line panel. Choose Add to Panel. Select CPU Frequency Scaling Monitor. Click Add.

---

### Post by GoodPanos on 2005-10-26
Thank you for the instuctions.

I got it all working.  Is there a way though, to verify that indeed the processor is running at the speed I specified?

---

### Post by C38a7r1zvl on 2005-10-27
You can change the cpu **frequency** with the standard Ubuntu kernel, however you cannot change the **core voltage**.

You can "undervolt" virtually every Pentium M processor. My Pentium M 745 for instance is supposed to run with about 1.3V at the speed of 1.8MHz and 1V at 600MHz however it still works fine with 1V@1.8MHz and 0.7V@600MHz. The advantage of such undervolting is that your processor will obvoiusly need less power meaning your battery will last longer and the processor won't get as hot as with the high voltage as laid out by the specifications meaning of course your fan won't have to work that hard meaning your laptop will operate more quietly and again your battery will last longer :)

I am not aware of any disadvantages other than a potentially instable system. Read: Your computer might just hang if you pushed too hard. In this case just heighten the voltage step by step until you got yourself a stable system..

---

### Post by jordz on 2005-11-07
How can u undervoltage ur cpu with the standard 686 kernel? Because i can't find a speedstep_centrino.c ?

---

### Post by extremecarver on 2006-05-29
which patch should I apply for standard 2.6.15-23-686 dapper kernel in order NOT TO LOOSE WIFI??? -- I need a copy and paste howto to get this working with dapper - I even compiled ndiswrapper but I am allways loosing my wifi.

---

### Post by extremecarver on 2006-05-29
this is what I get if I apply the dothan-3 patch to my kernel (following your advice with 2.6.15:

root@localhost:/usr/src/linux# bzip2 -dc /usr/src/cpufreq-speedstep-dothan-3.patch.tar.bz2 | patch -p1
missing header for unified diff at line 3 of patch
patching file arch/i386/kernel/cpu/cpufreq/speedstep-centrino.c
Hunk #1 FAILED at 195.
Hunk #2 succeeded at 370 with fuzz 2 (offset 89 lines).
Hunk #3 FAILED at 390.
Hunk #4 FAILED at 404.
patch unexpectedly ends in middle of line
3 out of 4 hunks FAILED -- saving rejects to file arch/i386/kernel/cpu/cpufreq/speedstep-centrino.c.rej
patch unexpectedly ends in middle of line
root@localhost:/usr/src/linux#

---

### Post by extremecarver on 2006-07-17
Please not that when uptdating to 2.6.17 there is no ndiswrapper update needed when using dapper. If updating to 2.6.16 kernel I had to go back to firmware 2.4 in order to have IPW22OO supported

---

