---
title: "Problems with acpi and Acer Aspire 1691WLMI"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by dsolsona on 2005-05-27
Hi all,

I have an acer aspire 1691 WLMI

I Found a problem with installation CD, tried with the default option to boot from the CD and it never loaded. After reading the boot help, i tried with the option acpi=off and then i was able to start all the installation process. 

My problem is that now i have the system installed but i dont have acpi running and i cant boot withouth acpi=off because the kernel never starts to load.

Someone now how to make ubuntu run with acpi on on the acer aspire 1691? I have kubuntu hoary.

Any help will be nice

P.D Sorry for my english...

---

### Post by duffman25 on 2005-06-01
I have the same problem here. Using ubuntu 5.04

---

### Post by dsolsona on 2005-06-01
I have new info on my problem with ACPI and the ACER ASPIRE 1691

I have some ACPI options working now, and some others not working. 

If i boot passing noapic option to the kernel and disabling PCMCIA services then I can work with ACPI. If you try to boot without the noapic option, the kernel never loads. If you dont disable PCMCIA services, it never finishes loading, stopped at PCMCIA services.

And now i have that on my syslog:

Jun  1 21:40:42 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node dfa2cf80), AE_NOT_FOUND
Jun  1 21:40:45 localhost kernel:     ACPI-0352: *** Error: Looking up [Z00B] in namespace, AE_NOT_FOUND
Jun  1 21:40:45 localhost kernel: search_node dfa2c1a0 start_node dfa2c1a0 return_node 00000000

I think maybe is something related with the dsdt table. I will try to put a dsdt table i found at [http://acpi.sourceforge.net](http://acpi.sourceforge.net)


And about APIC, i dont know whats that :p and well the laptop works well without it.

Any new input on that will be good.

---

### Post by Djax on 2005-06-01
Perhaps it's already done:
[http://acpi.sourceforge.net/dsdt/tables/ACER/Aspire_1691WLMi/](http://acpi.sourceforge.net/dsdt/tables/ACER/Aspire_1691WLMi/)

---

### Post by duffman25 on 2005-06-02
[QUOTE=Djax]Perhaps it's already done:
[http://acpi.sourceforge.net/dsdt/tables/ACER/Aspire_1691WLMi/](http://acpi.sourceforge.net/dsdt/tables/ACER/Aspire_1691WLMi/)[/QUOTE]

Can somebody explain how to use this? I'm afraid I'm to newbie... Thanxs.

---

### Post by dsolsona on 2005-06-02
Yeah, tried with that dsdt but i'm having some problems compiling the dsdt with the iasl. Thats the errors i get when i try to compile:

dsdt.dsl  1042:                     , AddressRangeMemory, TypeStatic)
Error    1094 -            Missing ResourceSource string (required) ^ 

I get 18 errors like this. 


My iasl version is: 

ASL Optimizing Compiler / AML Disassembler version 20050513 [Jun  1 2005]

Will try to find some help at the ACPI mail list.

---

### Post by dsolsona on 2005-06-06
Ok, main problems is fixed now.

I can boot with acpi and I have allmost all the acpi stuff working.

Now the only problem I have with acpi is the fan not working. I will do another post for that problem.

For the people who has an acer aspire 1691WLMi to fix acpi problems you need:

1) boot with noapic option
2) Disable pcmcia services
3) Download a custom dsdt for the Aspire 1691 from [http://acpi.sourceforge.net](http://acpi.sourceforge.net)
4) Compile the dsdt and install it (at initrd for example)
5) You're rdy :-)

---

### Post by duffman25 on 2005-06-07
[QUOTE=dsolsona]Ok, main problems is fixed now.

I can boot with acpi and I have allmost all the acpi stuff working.

Now the only problem I have with acpi is the fan not working. I will do another post for that problem.

For the people who has an acer aspire 1691WLMi to fix acpi problems you need:

1) boot with noapic option
2) Disable pcmcia services
3) Download a custom dsdt for the Aspire 1691 from [http://acpi.sourceforge.net](http://acpi.sourceforge.net)
4) Compile the dsdt and install it (at initrd for example)
5) You're rdy :-)[/QUOTE]

I'm having a lot of compilation errors. Could you say what compiler version you have used and any if it's necessary to do something strange to make it compile? Thanxs.

---

### Post by Djax on 2005-06-07
> I'm having a lot of compilation errors. Could you say what compiler version you have used and any if it's necessary to do something strange to make it compile? Thanxs. 
From which compilation are you talking about?

For the kernel, I follow this [KernelHowto](http://www.ubuntulinux.org/wiki/KernelHowtoKernelHowto) .

For the compilation of iasl (20050309), I used the package **flex-old**. The next version of iasl is more restrictive.

---

### Post by duffman25 on 2005-06-08
[QUOTE=Djax]From which compilation are you talking about?

For the kernel, I follow this [KernelHowto](http://www.ubuntulinux.org/wiki/KernelHowtoKernelHowto) .

For the compilation of iasl (20050309), I used the package **flex-old**. The next version of iasl is more restrictive.[/QUOTE]

I'm having problems with the dsdt compilation. I'm using the custom one provided by acpi at sourceforge. I've found a nice tutorial (in spanish) here: [www.ubuntu-es.org/node/3028](www.ubuntu-es.org/node/3028) but, as I've said, I can't manage to compile the dsdt since it gives me a lot of errors. I'm using the package acpica-unix-20050309.tar.gz. I've installed flex-old and pretty much everything needed to compile it.

Here's the output:

#@A1691:~/acpi$ sudo ./acpica-unix-20050309/compiler/iasl -d ACER-Aspire_1691WLMi-S3C11-custom.asl
Intel ACPI Component Architecture
ASL Optimizing Compiler / AML Disassembler version 20050309 [Jun  7 2005]
Copyright (C) 2000 - 2005 Intel Corporation
Supports ACPI Specification Revision 3.0

Loading Acpi table from file ACER-Aspire_1691WLMi-S3C11-custom.asl
 tbutils-0221: *** Warning: Invalid table signature found: [/*
 ]
Table header is invalid!
Couldn't get table from the file


So basically my problem is that I don't know how to compile the dsdt file provided by the people at acpi.sourceforge

Any help is appreciated

---

### Post by Djax on 2005-06-09
>  sudo ./acpica-unix-20050309/compiler/iasl -d ACER-Aspire_1691WLMi-S3C11-custom.asl
Intel ACPI Component Architecture
ASL Optimizing Compiler / AML Disassembler version 20050309 [Jun 7 2005]
Copyright (C) 2000 - 2005 Intel Corporation
Supports ACPI Specification Revision 3.0

Loading Acpi table from file ACER-Aspire_1691WLMi-S3C11-custom.asl
tbutils-0221: *** Warning: Invalid table signature found: [/*
]
Table header is invalid!
Couldn't get table from the file 

**iasl -d** is for decompilation

ACER-Aspire_1691WLMi-S3C11-custom.asl  is an already disassembled file (source code quite ready).

So it's quite normal that iasl complains.

To compile the ACER-Aspire_1691WLMi-S3C11-custom.asl, do:
**iasl -tc ACER-Aspire_1691WLMi-S3C11-custom.asl**

If the compilation is errorfree, it will produce a DSDT.aml and a ACER-Aspire_1691WLMi-S3C11-custom.hex

If you want to use the "-d" option, do:

```
cat /proc/acpi/dsdt > dsdt.dat
iasl -d dsdt.dat
```
It will create a dsdl.dsl, which must be rather similar to ACER-Aspire_1691WLMi-S3C11-original.asl (some details about the iasl version and the decompilation date can vary.)

---

### Post by duffman25 on 2005-06-09
[QUOTE=Djax]**iasl -d** is for decompilation

ACER-Aspire_1691WLMi-S3C11-custom.asl  is an already disassembled file (source code quite ready).

So it's quite normal that iasl complains.

To compile the ACER-Aspire_1691WLMi-S3C11-custom.asl, do:
**iasl -tc ACER-Aspire_1691WLMi-S3C11-custom.asl**

If the compilation is errorfree, it will produce a DSDT.aml and a ACER-Aspire_1691WLMi-S3C11-custom.hex

If you want to use the "-d" option, do:

```
cat /proc/acpi/dsdt > dsdt.dat
iasl -d dsdt.dat
```
It will create a dsdl.dsl, which must be rather similar to ACER-Aspire_1691WLMi-S3C11-original.asl (some details about the iasl version and the decompilation date can vary.)[/QUOTE]


Thanxs. I've managed to compile the custom dsdt but it's not working here :(
I've followed the steps and generated the DSDT.aml & the ACER-...-custom.hex.
My question is, to install it what exactly I have to do? I've never done this kind of things in linux :(

Edit: I've followed the instructions found here: [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml) but when I enable acpi (I mean I boot without the acpi=off) & boot with the patched initrd the computer freezes. :(

I'm using kernel 2.6.10-5

---

### Post by Djax on 2005-06-09
I use the method that add the DSDT.aml in the initrd. There is an other method but, as I understand it, we have to recompile the all kernel each time we change the DSDT.

Your kernel must support customise DSDT support.

You must have **ACPI_INITRD=y** in your /usr/src/linux/.config ( or
/proc/config.gz if you have enable **CONFIG_IKCONFIG_PROC=y**)

I put my DSDT.aml in my initrd.img that way:

```

$ cd /boot
$ sudo su
# cp initrd.img-2.6.11 initrd.img-2.6.11-ACPI
# echo -n "INITRDDSDT123DSDT123" >> initrd.img-2.6.11-ACPI
# cat DSDT.aml >> initrd.img-2.6.11-ACPI
# echo -n "INITRDDSDT321DSDT321" >> initrd.img-2.6.11-ACPI
```

You have to modify your /boot/grub/menu.lst to reflect this change:

```
root (hd0,1)
kernel /boot/vmlinuz-2.6.11 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.11-ACPI
savedefault
boot
```

If the boot hangs, try with the option   **pci=noacpi**  and/or **noapic**

---

### Post by duffman25 on 2005-06-10
[QUOTE=Djax]I use the method that add the DSDT.aml in the initrd. There is an other method but, as I understand it, we have to recompile the all kernel each time we change the DSDT.

Your kernel must support customise DSDT support.

You must have **ACPI_INITRD=y** in your /usr/src/linux/.config ( or
/proc/config.gz if you have enable **CONFIG_IKCONFIG_PROC=y**)

[/QUOTE]
Hi, thanxs for responding :)

I can't find /usr/source/linux/.config or /proc/config.gz 
My ubuntu installation doesn't seem to have created those files.

I've tried the other steps, but as soon as I boot with acpi (i.e. removing acpi=off) the laptop hangs. I've been searching for this problem and found another method which is even more simpler, but I have the same problems. It says:

1. compile the DSDT. Done.
2. do the following:
```

sudo su
cp DSDT.aml /etc/mkinitrd/DSDT
dpkg-reconfigure kernelpackageinuse

```

where in my case the kernelpackageinuse is linux-image-2.6.10-5-686

after executing dpkg-reconfigure the output is:

```

Not touching initrd symlinks since we are being reinstalled (2.6.10-34.2)
Not updating image symbolic links since we are being updated (2.6.10-34.2)
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.10-5-686
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

If I try to reboot without acpi=off the laptop hangs. If I boot with noapic then the computer freezes at some point during the boot process (but not at start). I've tried noapic and nopcmcia as kernel parameters with no luck. How do you disable the pcmcia services? (edit: found hw-detect/start_pcmcia=false but my laptop still freezes)

---

### Post by duffman25 on 2005-06-10
Finally!

After looking the forums how to disable the pcmcia services I found this thread: [http://ubuntuforums.org/showthread.php?t=25489&highlight=pcmcia+services](http://ubuntuforums.org/showthread.php?t=25489&highlight=pcmcia+services)

It point to a bug report: [http://bugzilla.ubuntu.com/show_bug.cgi?id=9101](http://bugzilla.ubuntu.com/show_bug.cgi?id=9101)
and in the comments I could find the solution:

1. boot into recovery mode
2. execute: dpkg --purge pcmcia-cs

And now I can boot with the noapic option and have some battery status in my laptop.

Thanxs everyone that helped and hope this helps others :D

---

### Post by Confuse on 2005-06-23
Sorry to bring up yet another old topic, but are the dstd's provided by acpi-devel already FIXED? Or are they just decompiled? I'm having troubles getting any readings from my battery in my Acer Aspire 3000 and I think its related to a buggy dstd.

---

### Post by X-fact0r on 2005-06-28
I have an Apire 1691 and can't even boot the installation CD!
Disabled acpi from boot options but the installation hanged up on hardware detection...

I really want to install Hoary on my laptop so please help me out.
I found this early post, but I don't even know how to disable the pcmcia services... can you please make a n00b step-by-step descrition on how to install Ubunto into this dumb laptop? :? 

[quote=" dsolsona"]

Ok, main problems is fixed now.

I can boot with acpi and I have allmost all the acpi stuff working.

Now the only problem I have with acpi is the fan not working. I will do another post for that problem.

For the people who has an acer aspire 1691WLMi to fix acpi problems you need:

1) boot with noapic option
2) Disable pcmcia services
3) Download a custom dsdt for the Aspire 1691 from [http://acpi.sourceforge.net](http://acpi.sourceforge.net)
4) Compile the dsdt and install it (at initrd for example)
5) You're rdy[/quote]

Thanks in advance.

---

### Post by Djax on 2005-06-28
> I have an Apire 1691 and can't even boot the installation CD!
Disabled acpi from boot options but the installation hanged up on hardware detection...

I really want to install Hoary on my laptop so please help me out.
I found this early post, but I don't even know how to disable the pcmcia services... can you please make a n00b step-by-step descrition on how to install Ubunto into this dumb laptop?  

Here you can read how I install my aspire 1694:
[http://users.linuxbourg.ch/didier/blog/?p=2&lp_lang_view=en](http://users.linuxbourg.ch/didier/blog/?p=2&lp_lang_view=en)

The original text is in french, so some sentences are not verbatim.

---

### Post by X-fact0r on 2005-07-06
Great stuff Djax!
Imanaged to install it flawlessly on my laptop.  \\:D/ 

Keep the good work.

---

### Post by J2R on 2005-07-07
Is everything working for you on the Acer Aspire 1691? Including wi-fi, hibernation, battery management? I had to give up and revert to Windows XP, but I'd much rather be using Linux (I've been using Linux as my main desktop OS for the last 18 months). I couldn't get the internal wi-fi working with Ubuntu.

---

### Post by SwimmerBoy on 2007-10-25
Can anyone help me in order to use the acer 1691 fan always on?

My Acer is getting 2 hot...

---

