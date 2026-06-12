---
title: "How to turn an USB thumb drive into a Win7 recovery disk?"
date: 2010-11-01
forum: Hardware
---

### Post by yminus on 2010-11-01
I am considering to buy a SSD. But all SSD vendors seem to be incapable of developing a firmware update mechanism that does not depend on commercial OSs like windows.

As I only have Linux machines I asked how to update the firmware without windows or mac and the support recommended
> download a Win7 recovery ISO and use that. But the SSD will be part of my NAS that won't have any CD/DVD drive. So I tried to use an USB thumb drive instead. I tried to create a bootable USB drive using [unetbootin]("http://unetbootin.sourceforge.net/") . When using unetbootin the unetbootin boot menu shows up, but the recovery system does not start. Instead the boot menu shows up again.

I found a lot of howtos about copying the [Win 7 Recovery]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/") stuff to usb and make it bootable, but all are using windows tools. I also know how to copy Linux live systems to usb and boot them, but I don't know how this can be done with a windows live cd.

Maybe you can help me.

---

### Post by yminus on 2010-11-07
I could not find out how a Windows Recovery CD may be booted from CD. I found a [script to extract the initial/default boot image from a CD](http://www.uni-koblenz.de/~krienke/ftp/noarch/geteltorito/). But I know to little about booting process to use it for booting from usb.

It is [SandForce](www.sandforce.com), the vendor of the SSD processors, that is responsible for the windows dependency. According to this [survey](http://www.behardware.com/articles/794-1/ssd-2010-roundup-15-ssds-compared.html) there are few SSD  processors competitive to the SandForce SF-1200, e.g. the [Marvell](http://www.marvell.com) 88SS9174. But [SSDs featuring the latter processor](http://www.crucial.com/store/partspecs.aspx?IMODULE=CTFDDAC128MAG-1G1) are much more expensive.

So I won't buy a SSD now and wait for a affordable SSD with a firmware upgrade tool that has no ridiculous dependencies on proprietary commercial operation systems.

---

### Post by oldfred on 2010-11-07
I have seen posts that said it worked if they just copied it or used unetbootin, but I think that was just for the full windows install.

I tried several times to use the repair only ISO and could not get it to boot or it asked for the CD.

I did make it work without win7 by creating the CD from the ISO and then using the CD to copy itself to a flash drive using the standard windows commands from the CD. That booted. I then installed grub2 and was able to make that boot, so I could then install additional ISO to loop mount and make a full win7 & linux repair CD.

Some info here:
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

Repair only CD
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by yminus on 2010-12-31
[OCZ has developed a firmware update tool for linux]("http://www.ocztechnologyforum.com/forum/showthread.php?82289-1st-Public-beta-test-of-OCZ-Sandforce-Linux-based-firmware-upddate-tool")! So there is no need for a bootable windows usb drive. 
I tested this tool with my brand new [OCZ Vertex 2]("http://www.ocztechnology.com/products/solid-state-drives/sata-ii/2-5--sata-ii/performance-enterprise-solid-state-drives/ocz-vertex-2-sata-ii-2-5--ssd.html"). And it works!

---

