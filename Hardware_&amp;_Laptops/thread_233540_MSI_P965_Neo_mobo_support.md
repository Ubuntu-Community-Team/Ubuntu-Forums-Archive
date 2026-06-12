---
title: "MSI P965 Neo mobo support"
date: 2006-08-10
forum: Hardware &amp; Laptops
---

### Post by saftaplan on 2006-08-10
None of the Linux distro's I try to install with my MSI P965 Neo motherboard, recognize my LG HL-DT-ST DVD-RAM GSA-H20L PATA-drive and the Seagate ST3200822AS 200GB SATA-drive. I tried installing Gentoo 2006.0 x64, Ubuntu 6.06, Ubuntu 6.10 Knot 1, Fedora Core 5 x64, Fedora Core 6 Beta 2 (this one failing with a kernel panic), OpenSUSE x64 and Instlux Ubuntu, with no luck.

I think it's the JMicron JMB361 RAID controller, but I cannot just disable the controller in the BIOS, no device is recognized then (so the SATA and IDE-ports cannot work natively, I suppose?). Old Windows XP SP1 doesn't need a driver diskette and installs flawlessly :confused: 
Since I use Linux as my main OS, it's quite a big problem. Is there any chance this board/controller will be supported in the next version of Ubuntu?

---

### Post by KlausU on 2006-08-12
I do have exactly the same problem, this is not an Ubuntu problem, I tried with alot of different distros.

Have a look at:
[http://www.uwsg.iu.edu/hypermail/linux/kernel/0607.1/1730.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0607.1/1730.html)

The "all-generic-ide" might be a chance.

PLEASE leave a post here when you have got anything to work! This really sucks, I was short before buying a SATA DVD, but now as I know the origin of the problem and more people have it to i hope it can be solved.

---

### Post by saftaplan on 2006-08-13
The all-generic-ide kernel option seems to work with Gentoo 2006.0. Thank you! Ubuntu 6.06 seems to be able to mount the root filesystem but still hangs after this step, OpenSuse gives the same error as before.

The ethernet card wasn't working yet (although the necessary r8169 module is included with Gentoo) but that was the least of my concerns. My harddisk is listed as /dev/hdi and my dvd-ram as /dev/hdk, probably because of the other SATA controllers on the board (although the SATA port I'm using is marked as SATA1 on the mobo). Installation was going fine, until I needed to install GRUB: it said that ```
/dev/hdi does not have any corresponding BIOS drive
```
So I added the line ```
(hd0)   /dev/hdi
``` to /boot/grub/device.map, ran install-grub /dev/hdi again and it gave no errors this time. I reboot and grub spits out "error 21", which apparently means grub couldn't find my disk after all. So now I'm stuck here with GRUB. I can't really try LILO because it isn't on the install CD, and to be honest, I don't really have high hopes for that one.
I'm sorry, I know this is a Ubuntu and not a Gentoo forum, but it's at least one distro where I could go a step further. 

TIA for any further help [-o<

---

### Post by Tamale on 2006-08-14
> **saftaplan said:**
> None of the Linux distro's I try to install with my MSI P965 Neo motherboard, recognize my LG HL-DT-ST DVD-RAM GSA-H20L PATA-drive and the Seagate ST3200822AS 200GB SATA-drive. I tried installing Gentoo 2006.0 x64, Ubuntu 6.06, Ubuntu 6.10 Knot 1, Fedora Core 5 x64, Fedora Core 6 Beta 2 (this one failing with a kernel panic), OpenSUSE x64 and Instlux Ubuntu, with no luck.

I think it's the JMicron JMB361 RAID controller, but I cannot just disable the controller in the BIOS, no device is recognized then (so the SATA and IDE-ports cannot work natively, I suppose?). Old Windows XP SP1 doesn't need a driver diskette and installs flawlessly :confused: 
Since I use Linux as my main OS, it's quite a big problem. Is there any chance this board/controller will be supported in the next version of Ubuntu?


Took me a while, but I finally fixed this exact same problem on my MSI Neo 865 motherboard by changing from "SATA Mode only" with "PATA Keep" enabled to  "SATA + PATA Mode"  in bios.

Hope this helps anyone who runs into the same problem.

---

### Post by saftaplan on 2006-08-14
I had already examined the whole BIOS but I couldn't find such an option. The only option I could set that had something to do with it was in which mode the controller should run, IDE/RAID/Disabled. In RAID, linux wouldn't detect my drives, not even with all-generic-ide, and since the PATA and SATA controllers are both connected to it, Disabled gave even worse results. So IDE mode it is.

Now for the GRUB problem, it's solved by changing the SATA port of the HDD. It was connected to the only JMB361 SATA port on the board, now it's connected to another port on the Intel controller. At first it gave some DMA and IRQ errors (but I could still work with it) so I added irqpoll next to the all-generic-ide option aready appended. I added these options in grub's menu.lst, and I have a working Linux system now!
I didn't get the ethernet port working yet (I compiled r8169 in the kernel, so not as a module, and it still gives no sign of life), and I didn't test the on-board sound, but at least that's listed in lspci as detected.

I still ask myself what Ubuntu's problem is, it still hangs with the irqpoll and all-generic-ide options enabled. But Gentoo will do for now :) I'll update if I get the ethernet card working.

---

### Post by KlausU on 2006-08-14
Today I have installed Ubuntu with some tricks from Windows/HDD/Grub... but however it is far from perfect because it seems impossible to install a real Kubuntu since the netboot images are Ubuntu only... argh.

I have tried alot with the bios options and no success. Also no idea why all-generic-ide wont work. I think I will go with the installed Ubuntu and try to replace the kernel... well or just gentoo itself.

Do you have gentoo installed now, does the IDE work with the lates kernel without additional boot options?

---

### Post by saftaplan on 2006-08-15
I tried 2.6.17.8 today from kernel.org (so not gentoo-patched or something) but it didn't work, not even with the boot options enabled, which is weird because the link you gave clearly states that it's no problem for versions "prior to 2.6.18rc1" (I did not  disable AHCI, maybe I should try that).

Meanwhile I got the ethernet port working, which was fairly easy. Don't use the drivers from MSI's website but download them from [the RealTek site]("http://www.realtek.com.tw/downloads/downloads1-3.aspx?lineid=1&famid=All&series=All&Software=True#2005081Unix%20(Linux)"), follow instructions in readme, execute modprobe r1000 and check if it is detected with ifconfig eth0. If it works, add r1000 to /etc/modules.autoload.d/kernel-2.6 and all should be fine. 

And how exactly did you get ubuntu on your disk? By using the same method instlux uses (with grub4dos)? 'Cause I tried that and grub4dos failed, but it could be because my HDD was still connected to that JMB361 SATA port.

---

### Post by Cynical on 2006-08-18
This is a problem with jmicron controller support in the kernel, and has nothing to do with ubuntu obviously. The latest kernel (2.6.18) with the mm2 patch fixes the problem. By the time Ubuntu 6.10 is released there wont be any issues.

---

### Post by saftaplan on 2006-08-19
Ok thx for the reply Cynical :)
Everything I need from my mobo works for now except for the Realtek 883 (Intel HD Audio) soundcard. It plays sound with alsa, but it's very scrambled. Let's see if I can work out this last issue :-k 
Maybe [this]("http://ubuntu-tr.com/v6/node/252") has got something to do with it, but my Turkish isn't fluent ;) The [link]("http://www.linux-on-laptops.com/forum/printthread.php?t=286&page=2&pp=10") in the document doesn't seem to have much to do with it, I guess.

---

### Post by meronb on 2006-08-19
Since I'm having exactly the same problem (the grub-part), could give some more info on how you solved it? i'm using gentoo and my sata drive is connected to SATA1 on the mobo. Grub doesn't see it.Do I have to connect it to a different SAT-port?

---

### Post by saftaplan on 2006-08-19
Indeed, just connect it to another SATA port. Best it to connect it to the one right next to the SATA1 port, labeled SATA4 on the mobo if I'm not mistaken, because this is the one Linux will see as hda (else you will get a disk labeled hde or something, not that that's a problem, but it's just so much cleaner to connect it to the first port ;) ). If you check the BIOS, you'll see that your hard drive is indeed recognized now, and GRUB gives no errors anymore.
If you're still chrooted, I think you need to re-create your mtab file though, else the same errors will persist. Good luck ;)

---

### Post by dens57 on 2006-08-20
Does anyone succeed to get usb working with this mobo ?
Me as soon as I activate usb in bios boot stop at "booting kernel".

thanks
denis

---

### Post by dens57 on 2006-08-20
Just got it ! Need to disable IOAPIC in bios.

---

### Post by dens57 on 2006-08-20
Another issue , the dual core is not detected :

cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 6
cpu MHz         : 1863.705
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 3198.26

but the kernel is an smp :

Linux mainSrv 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686 GNU/Linux

Is there anyone with the same issue ?

thanks

---

### Post by saftaplan on 2006-08-20
Here it's detected as 2 CPU's... Maybe you should dig through your kernel configuration or something. Are you using gentoo?

---

### Post by dens57 on 2006-08-21
no Ubuntu dapper , I've checked and the kernel is smp

---

### Post by thotz on 2006-08-28
Could you have a look at Ubuntu Bug [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502)

It will be fixed in Ubuntu Edgy soon.

---

### Post by fireboxtester on 2006-09-02
I made a wiki page to put all of the information about this P965/jmicron issue in one place:
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

As you can see it's a pretty major issue.  There are already 3 bugs and at least 9 forum threads regarding this.  Hopefully we can get this fixed for Edgy.  (I'm going to test Knot 2 later tonight)

---

### Post by lazerradial2003 on 2006-09-11
Does anyone know if this issue has been resolved yet? I'm building a PC on a budget because my other machine died and since Ubuntu is my main OS it's quite important that it works! I can't seem to find any budget motherboards that dont have some sort of jmicron IDE support. This is especially important because i was hoping to carry on using my IDE hard drives for a bit until i could afford some SATA ones... Any suggestions would be very much appreciated!

---

### Post by jaredvolkl on 2006-09-13
Just upgraded to a Gigabyte P965 and Core 2 Duo E6300 (OC'ed to 7x350 = 2.45GHz) and of course I ran into this IDE controller problem. 

From my initial research on this, it seems I may be able to get the install working though a USB drive of some kind. I have one of my DVD drives connected via a IDE to USB adapater and I also have a memory card reader connected via USB. I was messing around last night and couldn't get my mobo to boot from the USB DVD drive, I imagine because there needs to be some sort of USB driver loaded to do it.

I was also thinking maybe I could use my 1GB SD card to install Ubuntu. I have to get to work pretty soon, but when I get home I'll be messing around again. If anyone has any success or has a clue how I'd do the card reader install, I'd much appreciate the help. Windows is fun and all, but I want my Linux!

---

### Post by lazerradial2003 on 2006-09-13
If you search the wiki for core 2 duo support, that has details of how to install from a usb stick (card reader should be the same since both are USB mass storage devices) Does your BIOS have an option to boot from USB-DVD/ USB-CD as opposed to just boot from USB...that's just a random thought because i remember seeing options that specific on mine.

---

### Post by jaredvolkl on 2006-09-13
Thanks for the info Laz, I'll check it out when I get home. I did see the wiki already, but I wasn't sure if that option would work with my card reader. I'm afraid that since I've had problems getting the DVD drive I have connected via USB to boot, I may also have the same problems with the card reader. 

I have a USB key, but it's only a 128MB drive, so there's no way I'm fitting dapper on that. Unless...maybe someone could help me slim down the install to under 128MB.

Just a thought, but a couple of times I've used an old breezy disc to install when the dapper disc had problems booting or running and then I was able to upgrade to dapper. That was always on old hardware though and being that this problem is a kernel problem I'm thinking that probably won't work. Maybe it's worth a shot.

---

### Post by lazerradial2003 on 2006-09-13
It's worth a shot, i think your probabely right that the kernel still won't like it but anythings worth trying, I was reading something on a website about older kernels being ok with the all-generic-ide parameter at boot(not sure if thats the right parameter but you know the one i mean), so maybe you could install an older version with the right boot option and then upgrade it to dapper over the internet?

 That's completely based on a vague memory of reading an incomplete explanation on a website in the small hours whilst trying to solve this problem before, so please no-one give it too much weight.

---

### Post by jaredvolkl on 2006-09-15
Well, just reporting back that the boot from card reader was a no go. I have 3 USB options in my BIOS and none of them trigger my USB DVD drive nor my USB card reader. I also found some stuff on netbooting, and managed to get a tftp server set up on my old laptop to do the servering, but when I tested the server by trying to download the pxe image, it failed to find the file.

The next thing I'm going to try is Edgy Knot 3. I'm not to hopeful at this point and I'm very close to seeing how much a SATA optical drive would cost.

---

### Post by lolikapuxa on 2006-10-16
hey this topic is inactive for what? 4 weeks?

 Has anyone got the msi neo working whith ubuntu?

---

### Post by lazerradial2003 on 2006-10-16
This thread is still very active on that topic:

[http://ubuntuforums.org/showthread.php?p=1619345](http://ubuntuforums.org/showthread.php?p=1619345)

lazerradial2003

---

