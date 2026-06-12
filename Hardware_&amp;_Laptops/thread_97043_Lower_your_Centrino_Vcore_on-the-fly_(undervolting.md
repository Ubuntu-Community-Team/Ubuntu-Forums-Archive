---
title: "Lower your Centrino Vcore on-the-fly (undervolting)"
date: 2005-11-30
forum: Hardware &amp; Laptops
---

### Post by tawk on 2005-11-30
Hello,
after reading a [Gentoo-Wiki-Page]("http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU") and a [Dothan Howto in ubuntuforums.org]("http://www.ubuntuforums.org/showthread.php?t=75810") I was able to compile a kernel which can change the vcore of my Centrino without rebooting and recompiling the kernel. 
Similar to Notebook / Centrino Hardware Control under Windows it saves a lot of power and cools down my CPU.

This is what i have done:
(I hope it is useful for you)

install following packages:
- kernel-package
- build-essential
- linux-source-2.6.12

Do in a Root-Terminal:
```
cd /usr/src
tar -xjvf linux-source-2.6.12.tar.bz2
ln -s linux-source-2.6.12 linux
cd linux
gedit arch/i386/kernel/cpu/cpufreq/speedstep-centrino.c
// Patch this file as described in the Gentoo-Wiki-Page (Manualy edit your kernel source code)
cp /boot/config-2.6.12-*-?86 .config
make-kpkg --initrd --append-to-version -uservcore --revision 1 kernel-image
dpkg -i ../kernel-image-2.6.12-uservcore_1_i386.deb
```

after rebooting you can read and change your vcore for the different frequencies:
read:
```
user@ubuntu:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/voltage_table
1308,1180,1084,988
```
change:
```
root@ubuntu:~$ echo "1068,908,796,700" > /sys/devices/system/cpu/cpu0/cpufreq/voltage_table
```
Be careful: Too low numbers can freeze your Laptop. Lower the voltages in small steps and try stability first (e.g. with mprime)

But please notice: Do this at your own risk, I don't know if it works with your Notebook. In the worst case your notebook could be damaged!
For my on my Samsung X20 with Pentium-M 740 (Sonoma chipset) it is working without problems. The only thing I had to do after installing the new kernel was to recompile my Kernel-Module for the ati fglrx-driver:
```
sudo module-assistant a-i fglrx
```

---

### Post by angrylittleman on 2005-12-03
This looks good!  I love running CHC in "the other OS whos name we do not speak."  I can't wait to give this a try.  If I patch the kernel, will I have problems later with other modules not built against the patch?

alm

---

### Post by tawk on 2005-12-18
I had no problems at all, after having rebuilt the ATI module. Anyhow, it could happen that you have to reinstall your WLAN drivers. 
But if you encounter any problems, simply switch back to your standard kernel.

---

### Post by Delvien on 2005-12-18
I wish somone would create a user friendly GUI version of Notebook Hardware control for Ubuntu, i would actually pay money for it.

---

### Post by taseal on 2005-12-21
[QUOTE=Delvien]I wish somone would create a user friendly GUI version of Notebook Hardware control for Ubuntu, i would actually pay money for it.[/QUOTE]

ditto

I keep looking for one, but with 0 luck...

---

### Post by bonsiware on 2005-12-26
Everithing work for me!

But I have a pair of questions (noob):
- I have the i686 kernel installed, but when I compile following your instructions I build an i386 one; how can I build an i686 kernel?
- is there a way to set voltages permanently , so I don't have to change vcore every time I reboot?

thank you

bye

---

### Post by tawk on 2005-12-28
@bonsiware

- I'm not sure about it, but I think your compiled kernel uses the 686 options and headers, although it is named 386.

- permanent voltages:
This is what I did (very bad hack, but works fine):

sudo gedit /etc/acpi/undervolt.sh
```
#!/bin/sh
echo "1068,908,796,700" > /sys/devices/system/cpu/cpu0/cpufreq/voltage_table
```
sudo gedit /etc/X11/gdm/PostLogin/Default
```
#!/bin/sh
/etc/acpi/undervolt.sh
```

Hope it helps...
(from noob to noob)

---

### Post by bonsiware on 2005-12-28
Thank you for the reply!

- You are right saying that my kernel is for 686 even if it's named 368

- I'm not home now (in front of windows now because of work), but I will soon try your undervolt.sh script and autostart

bye

---

### Post by Confuse on 2005-12-28
What speed centrinos are you guys doing this with? I have a very lowend 725.

---

### Post by psusi on 2005-12-28
It is REALLY not a good idea to try using voltages lower than those set by the manufacturer.  It might seem to work ok for a while, but odds are it will cause some instability at some point.  

There are plenty of people who thought that they could overclock their cpu frequency just a bit and be fine.  The World of Warcraft forums are full of posts saying that "everything else" works just fine, but glitches and crashes happen when they play WoW.  When they finally tried to undo their overclocking, the problems went away.  

The moral of the story is that messing with things like this can make your life harder at some point in the future when you try doing something you have not before, and it won't work.  Human tendancy being what it is, you will very likely say "it can't be because of the undervolting, because everything else works" when in fact, that IS the cause of the problem.

---

### Post by bonsiware on 2005-12-28
[QUOTE=psusi]It is REALLY not a good idea to try using voltages lower than those set by the manufacturer.  It might seem to work ok for a while, but odds are it will cause some instability at some point.  

There are plenty of people who thought that they could overclock their cpu frequency just a bit and be fine.  The World of Warcraft forums are full of posts saying that "everything else" works just fine, but glitches and crashes happen when they play WoW.  When they finally tried to undo their overclocking, the problems went away.  

The moral of the story is that messing with things like this can make your life harder at some point in the future when you try doing something you have not before, and it won't work.  Human tendancy being what it is, you will very likely say "it can't be because of the undervolting, because everything else works" when in fact, that IS the cause of the problem.[/QUOTE]

I know that it's not a good idea.
But i need this tweak to let my laptop work properly!

I own a M6ne motherboard ASUS. 
It has overheating problems (70° idle and over 95° when busy) and it often shutdown itself when I compile a kernel or convert a video...

This looks like to be a 'feature' of this series of ASUS machines...

With undervolting I can use it normally!

I lowed down my voltage of only 80mV about, what I need not to reach critical temperatures.

However you are RIGHT to say that the best voltage is the one suggested from manufacturer!

bye

---

### Post by bonsiware on 2005-12-28
@tawk

I've tried your solution to set voltages at login time, but it doesn't work for me...

I'm looking for an other solution...

Thank you again!

---

### Post by bonsiware on 2005-12-28
@tawk

I've found one solution!

```
sudo gedit /etc/init.d/undervolting
```
then I've pasted the vcore settings command...
```
#! /bin/sh
echo "1148,1148,1148,1148,1148,1116,1052,1004,940,908" > /sys/devices/system/cpu/cpu0/cpufreq/voltage_table
```
...saved the file... and enabled executing permissions
```
sudo chmod +x /etc/init.d/undervolting
```
then I installed BUM (Boot Up Manager) 
```
sudo apt-get install bum
```
System --> Administration -->Boot-up Manager 
...and activated the undervolting entry.
(I didn't know how to activate the new script manually)

bye

---

### Post by bonsiware on 2005-12-28
[QUOTE=Confuse]What speed centrinos are you guys doing this with? I have a very lowend 725.[/QUOTE]

I think my one is a Pentium M 735 1.7Ghz...

---

### Post by Dogmatica on 2006-01-08
I tried compiling the new kernel, first I installed gcc-3.4 (version 4 was included in Kubuntu)
The compiling process ends with the following message.
What am I doing wrong?

>  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
  KSYM    .tmp_kallsyms1.S
  AS      .tmp_kallsyms1.o
  LD      .tmp_vmlinux2
  KSYM    .tmp_kallsyms2.S
  AS      .tmp_kallsyms2.o
  LD      vmlinux
  SYSMAP  System.map
  SYSMAP  .tmp_System.map
Inconsistent kallsyms data
Try setting CONFIG_KALLSYMS_EXTRA_PASS
make[1]: *** [vmlinux] Fout 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Fout 2
root@kubuntu:/usr/src/linux# pwd[/INDENT]


---

### Post by Jasman on 2006-03-05
Just want to say that everything I've read on undervolting in windows says that you really won't damage anything by doing it. I have a very similar Asus (Z70V or M6V) and it has the same problem with the fans (updated bios helps). But the real kicker is that safe undervolting can give you a lot more battery time for regular use. Anyway, I don't think undervolting is dangerous the way overclocking may be. Best advice from various places is to learn how to do it in windows (and torture test your safe voltages), then try to get it working in linux using those same voltages.

---

### Post by Alor on 2006-04-20
hi. i am one of the authors of [http://linux-phc.sourceforge.net/](http://linux-phc.sourceforge.net/)

if there are any problems with any kernel sources, i would be very interested.

so it would be nice if someone can send me the errormessages while applying the patch and maybe give me a link so that i can download the sources myself. than we will try to change the patch to be compatible with the ubuntu-sources.

a way to use linux-phc without patching is using a kernel-source which already includes the linux-phc patch. at the moment that would be the beyond sources:

[http://iphitus.loudas.com/beyond.php](http://iphitus.loudas.com/beyond.php)


thank you for using linux-phc and for helping to improve it!

edit: for further discussion of this topic please visit: [http://ubuntuforums.org/showthread.php?t=146366&page=3](http://ubuntuforums.org/showthread.php?t=146366&page=3)

roman schwarze

---

### Post by flapane on 2006-10-22
no help for undervolting an A64?

---

