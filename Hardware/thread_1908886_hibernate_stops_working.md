---
title: "hibernate stops working"
date: 2012-01-14
forum: Hardware
---

### Post by maniat1k on 2012-01-14
It may seem silly, but since I put the video drivers ([http://ubuntuforums.org/showthread.php?t=1903831](http://ubuntuforums.org/showthread.php?t=1903831)) in my Lubuntu 11.10. All of a sudden stopped working the  functionality to hibernate my notebook, which is totally embarrassing me, and I use it a lot.
 If I start to hibernate the computer obeys and this seems to do everything normal, but when I want to return from hibernation, it does nothing, just freezes...:confused:

---

### Post by Rodney9 on 2012-01-14
Hibernation seems to be un-reliable as the others posted

From the Lubuntu wiki > Hibernation may be unavailable with automatic partitioning

The default partitioning recipe in the installer will in some cases allocate a swap partition that is smaller than the physical memory in the system. This will prevent the use of hibernation (suspend-to-disk) because the system image will not fit in the swap partition. If you intend to use hibernation with your system, you should ensure that the swap partition's size is at least as large as the system's physical RAM. (345126)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by varunendra on 2012-01-15
If the swap were less than physical memory, then the system shouldn't have been able to hibernate at all. It would have failed with "Not enough space.." error. So I don't think it is swap size problem.

@maniat1k,
When you attempt to resume from hibernation, do you see any reasonable disk or screen activity? Or does it seem like stuck even before loading begins (very little or no disk activity at all)?

If it shows disk activity like it's attempting to resume, then freezes, it may be driver issue. But if it doesn't even attempt to resume, then it may be some disk-configuration issue.

Accordingly, please have a look at this article: [http://turbulentsky.com/resume-from-hibernate-failed-on-ubuntu.html](http://turbulentsky.com/resume-from-hibernate-failed-on-ubuntu.html)
Even though it was originally written for gutsy, it still seems to be helpful for some people. Go through the comments as well, especially comment no #16 on the above page.

Also, just to be sure it is not swap space problem, please post the outputs of:
```
sudo fdisk -l
```

and right before going to hibernate:
```
free -mt
```

---

### Post by Savio2010 on 2012-01-15
Visiting my blog may help you.


 I have noticed this issue mostly when 'Encrypt home folder' option is enabled during installation. Because when home folder is encrypted the swap space is also encrypted and leads to a failure when resuming Ubuntu.:(

Good luck.:P
[http://savio2010.blogspot.com/](http://savio2010.blogspot.com/)

---

### Post by maniat1k on 2012-01-17
> **varunendra said:**
> If the swap were less than physical memory, then the system shouldn't have been able to hibernate at all. It would have failed with "Not enough space.." error. So I don't think it is swap size problem.

@maniat1k,
When you attempt to resume from hibernation, do you see any reasonable disk or screen activity? Or does it seem like stuck even before loading begins (very little or no disk activity at all)?

If it shows disk activity like it's attempting to resume, then freezes, it may be driver issue. But if it doesn't even attempt to resume, then it may be some disk-configuration issue.

Accordingly, please have a look at this article: [http://turbulentsky.com/resume-from-hibernate-failed-on-ubuntu.html](http://turbulentsky.com/resume-from-hibernate-failed-on-ubuntu.html)
Even though it was originally written for gutsy, it still seems to be helpful for some people. Go through the comments as well, especially comment no #16 on the above page.

Also, just to be sure it is not swap space problem, please post the outputs of:
```
sudo fdisk -l
```and right before going to hibernate:
```
free -mt
```
[INDENT][FONT=Courier New]:~# fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 4096 bytes
Tamaño E/S (mínimo/óptimo): 4096 bytes / 4096 bytes
Identificador del disco: 0xe430e430

Dispositivo Inicio    Comienzo       Fin      Bloques  Id  Sistema
/dev/sda1               2048     3999743       1998848       82  Linux swap / Solaris
/dev/sda2*     3999744    33998847    14999552       83  Linux
/dev/sda3        33998848   625141759   295571456     83  Linux
[/FONT][/INDENT][INDENT][FONT=Courier New]:~# free -mt
                       total          used          free     shared    buffers     cached
Mem:               2752            685           2066               0      11           370
-/+ buffers/cache:        303           2448
Swap:             1951              0             1951
Total:           4704            685           4018
[/FONT][/INDENT]When I try to "wake up" my laptop some disk activity I can see but with no results: also I look up on /var/log/syslog and don't see nothing strange.

> **Savio2010 said:**
> Visiting my blog may help you.


 I have noticed this issue mostly when 'Encrypt home folder' option is enabled during installation. Because when home folder is encrypted the swap space is also encrypted and leads to a failure when resuming Ubuntu.:(

Good luck.:P
[http://savio2010.blogspot.com/](http://savio2010.blogspot.com/)

I have no encyption on my home... thanks, anyway I will look at you blog's article.

---

### Post by varunendra on 2012-01-17
> **maniat1k said:**
> :~# free -mt
[INDENT][FONT=Courier New]                        total          used          free     shared    buffers     cached
**Mem:               2752**            685           2066               0      11           370
-/+ buffers/cache:        303           2448
**Swap:             [COLOR=Red]1951[/COLOR]**              0             1951
Total:           4704            685           4018[/FONT]
[/INDENT] So it clearly shows your physical memory (2752 MB) is larger than swap space (1951 MB). I don't know how you could hibernate earlier, or how your notebook even pretends to hibernate now, but this clearly is an 'insufficient swap' issue.

Accordingly, please boot with live cd, run gparted and increase swap partition's size to at least 2752 MB or more. Then reboot normally and see if hibernate works again.

**PS:**
Just out of curiosity- Can you tell us for sure how much physical memories your system RAM and graphic card do separately have?
I've never noticed it and currently don't have access to a PC with discrete graphics card to verify this, but am wondering if it is your graphic card's RAM which has been added with system memory to show up as 2752MB total physical memory.

---

### Post by Idyll on 2012-01-17
You may also find this FAQ helpful.  It helped me with a machine once:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

It's remarkably satisfying once you get the system hibernating successfully again, so goodluck!

Mike

---

### Post by maniat1k on 2012-01-17
> **varunendra said:**
> [/INDENT]So it clearly shows your physical memory (2752 MB) is larger than swap space (1951 MB). I don't know how you could hibernate earlier, or how your notebook even pretends to hibernate now, but this clearly is an 'insufficient swap' issue.

Accordingly, please boot with live cd, run gparted and increase swap partition's size to at least 2752 MB or more. Then reboot normally and see if hibernate works again.

**PS:**
Just out of curiosity- Can you tell us for sure how much physical memories your system RAM and graphic card do separately have?
I've never noticed it and currently don't have access to a PC with discrete graphics card to verify this, but am wondering if it is your graphic card's RAM which has been added with system memory to show up as 2752MB total physical memory.

Thanks for the replay! I will do that...

[INDENT][FONT=Courier New]~# lspci -v -s 00:01.0
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9806 (prog-if 00 [VGA controller])
        Subsystem: Acer Incorporated [ALI] Device 0520
        Flags: bus master, fast devsel, latency 0, IRQ 42
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 4000 [size=256]
        Memory at d0400000 (32-bit, non-prefetchable) [size=256K]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx_updates, radeon
[/FONT][/INDENT][INDENT][FONT=Courier New]~# cat /proc/meminfo | grep MemTotal
MemTotal:        2818432 kB
[/FONT][/INDENT]

---

