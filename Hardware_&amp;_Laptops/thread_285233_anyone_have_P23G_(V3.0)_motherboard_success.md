---
title: "anyone have P23G (V3.0) motherboard success?"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by w_ight on 2006-10-26
Has anyone gotten Dapper to boot with a P23G (V3.0) motherboard? I am waiting on a download of edgy to see if it will work. If you have gotten dapper or edgy to work please tell me how.

Specs:
P23G (V3.0)
Core 2 Duo 6300

I have been reading and trying any potential fix I can find. Via chipset, tried IDE to SATA adapter, tried various boot options acpi=off noapic nolapic pci=usepirqmask irqpoll all-generic-ide 

Why are the Core 2 Duo motherboards so problematic? Is it primarily early adoption issues?

---

### Post by zeroman on 2007-01-09
I am writing you from it right now.  No problem.  THe nic card disappears (known problem)
THis is a few months down the road from you.. but other than not the best onboard video supoport.. it works fine.

---

### Post by BenHines on 2007-02-13
Hi,

I'm new to ubuntu (and linux) as well and I have a P23G motherboard with a 3.2Ghz Celeron D.  I am also successfully running kubuntu (Dapper), but ran into the following issues, some of which have been resolved.
- Onboard video was using the vesa driver, which pretty well sucks.  Followed directions at [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) and got the 'via' driver to work.  Big improvement. 

- Onboard NIC did not work most of the time.  Resolved by slapping a NIC card into a PCI slot.  

- Onboard audio seems to have all sound come through the left speaker (both channels), but not sound through the right.  Haven't resolved this one yet. 

If anyone else has had problems with this board and resolved them, plz post here.  Thanks.

---

### Post by BenHines on 2007-02-17
Good news!  I contacted the tech support folks at PC Chips about the disappearing NIC on the P23G.  This, by the way, is a BIOS issue and has nothing to do with Ubuntu.  If you have this issue, you'll notice that on boot-up, the BIOS doesn't even see the onboard NIC.  If the BIOS can't see it, no operating system will be able to.  Anyway, PCChips tech support said to flash the latest BIOS for the P23G.  This was just released one month ago, so it is unlikely that existing P23Gs have this version.  Here's the site with the new BIOS:

[http://www.pcchips.com.tw/PCCWeb/Downloads/ProductsDetail_Download.aspx?DetailID=387&DetailName=BIOS&DetailDesc=P23G(V3.0)&MenuID=35&LanID=2](http://www.pcchips.com.tw/PCCWeb/Downloads/ProductsDetail_Download.aspx?DetailID=387&DetailName=BIOS&DetailDesc=P23G(V3.0)&MenuID=35&LanID=2)

Unfortunately, the flash utility runs under DOS and I don't have a floppy drive on my machine.  So, I downloaded a Win98 boot CD from the site below, burned the ISO image to a CD and then added the contents of the zip file from PCChips into its own directory (called 070115) on the CD.  The boot image is available from:

[http://www.allbootdisks.com/index.php?option=com_remository&Itemid=42&func=fileinfo&parent=folder&filecatid=1866](http://www.allbootdisks.com/index.php?option=com_remository&Itemid=42&func=fileinfo&parent=folder&filecatid=1866)
 
After booting from the CD, I just ran the BIOS flash utility, which automatically reboots the machine (CDROM is drive D):

```

    cd D:\070115\ecs_flash
    FDOS.BAT D:\070115\070115.ROM

```

At first boot, the NIC wasn't seen.  I rebooted the machine again and hel the "Page Up" key, which clears the CMOS.  I then went through the BIOS setup and have had no problems since.  By the way, I was also having trouble with the on-board sound coming out of only one speaker.  The BIOS upgrade has fixed this as well. 

I hope this helps other P23G owners.  Note that flashing the BIOS can turn your motherboard into a paperweight if you screw it up.  Do this at your own risk.

---

### Post by dannymichel on 2007-03-29
I don’t have any floppy disks or blank cds. I used them all. Now the boot disk I have doesn’t have ntsf or cd rom support. I’m not sure what the proper way to flash the bios is even. I see instructions here...  [http://www.ubuntuforums.org/showthread.php?p=2169097#post2169097](http://www.ubuntuforums.org/showthread.php?p=2169097#post2169097) that say type cd D:\070115\ecs_flash 
    FDOS.BAT D:\070115\070115.ROM. does he mean type cd D:\070115\ecs_flash to get into the directory on my hard drive then type FDOS.BAT D:\070115\070115.ROM or does he mean type FDOS.BAT  then press enter and then type D:\070115\070115.ROM then enter? Even if I understood what that guy was saying, the instructions from the manufacturer website says to do this.... [http://www.ny-dev.com/forums/f215/flash-bios-p23g-v1-0a-1426/#post6459](http://www.ny-dev.com/forums/f215/flash-bios-p23g-v1-0a-1426/#post6459) say to type A:\>AFUXXX 060307S.ROM /p /b /n /c /x" and then press "Enter. Does this mean I’m supposed to use the floppy boot disk to boot in does then take that disk out and put in another disk with the bios updates I downloaded from the website and type that in? Even if I have that right, the instructions that my manufacturer gave me says to download their bios updates. The updated bios file in my manufacturers files have FDOS.BAT and 070115.ROM in it which is described at [http://www.ubuntuforums.org/showthread.php?p=2169097#post2169097](http://www.ubuntuforums.org/showthread.php?p=2169097#post2169097) . What do I REALLY do?

---

### Post by Moonrakre on 2007-03-30
Many thanks for this.  I have a P23G(V1.0) and wanted to load Trixbox (Asterisk) but it came up with no Ethernet.  Pretty useless for a VOIP product.   It now works, and my DSL usb drive loads and works OK too.

The guidance on how to get a bootable CD to DOS was invaluable in implementing the fix, once again, many thanks.

Of course Trixbox runs on Centos, and I think DSL is (sort of) debian, just proving that the problem is not a Ubuntu one!

Best wishes

Adrian
:)

---

### Post by jesuspi on 2007-04-05
> **BenHines said:**
> Good news!  I contacted the tech support folks at PC Chips about the disappearing NIC on the P23G.  This, by the way, is a BIOS issue and has nothing to do with Ubuntu.  If you have this issue, you'll notice that on boot-up, the BIOS doesn't even see the onboard NIC.  If the BIOS can't see it, no operating system will be able to.  Anyway, PCChips tech support said to flash the latest BIOS for the P23G.  This was just released one month ago, so it is unlikely that existing P23Gs have this version.  Here's the site with the new BIOS:

[http://www.pcchips.com.tw/PCCWeb/Downloads/ProductsDetail_Download.aspx?DetailID=387&DetailName=BIOS&DetailDesc=P23G(V3.0)&MenuID=35&LanID=2](http://www.pcchips.com.tw/PCCWeb/Downloads/ProductsDetail_Download.aspx?DetailID=387&DetailName=BIOS&DetailDesc=P23G(V3.0)&MenuID=35&LanID=2)

Unfortunately, the flash utility runs under DOS and I don't have a floppy drive on my machine.  So, I downloaded a Win98 boot CD from the site below, burned the ISO image to a CD and then added the contents of the zip file from PCChips into its own directory (called 070115) on the CD.  The boot image is available from:

[http://www.allbootdisks.com/index.php?option=com_remository&Itemid=42&func=fileinfo&parent=folder&filecatid=1866](http://www.allbootdisks.com/index.php?option=com_remository&Itemid=42&func=fileinfo&parent=folder&filecatid=1866)
 
After booting from the CD, I just ran the BIOS flash utility, which automatically reboots the machine (CDROM is drive D):

```

    cd D:\070115\ecs_flash
    FDOS.BAT D:\070115\070115.ROM

```

At first boot, the NIC wasn't seen.  I rebooted the machine again and hel the "Page Up" key, which clears the CMOS.  I then went through the BIOS setup and have had no problems since.  By the way, I was also having trouble with the on-board sound coming out of only one speaker.  The BIOS upgrade has fixed this as well. 

I hope this helps other P23G owners.  Note that flashing the BIOS can turn your motherboard into a paperweight if you screw it up.  Do this at your own risk.

Hey there,

Do you know if this can be sorted out using winXP? I have a dual boot system (winXP & Xubuntu Edgy) and two HDD: one for booting both OS's and the other for assorted junk. This second drive can be mounted on both OS (it's an old drive, it has a FAT32 partition). Can I just transfer the files to this drive, boot to winXP and update the BIOS? or do I have to go old-school and boot from a floppy drive (which I don't have) or download an old Win98 image (which I find annoying, as I'm trying to leave MicroSoft for good)? 

Any ideas on this? I don't feel like getting a new silicon-based paperweight :)

---

### Post by jesuspi on 2007-04-11
Hi everyone,

Just flashed the bios following BenHines' post and everything worked great... thanks for the advice, especially about the clearing the CMOS part... I thought for a minute there that nothing had worked!

---

### Post by LALING on 2007-11-30
After flashing my mobo and clearing CMOS, nothing worked at all. I even used the mobo setup defaults and still nothing worked.

So what I did was reset the CMOS on the mobo using the jumper, and everything went well.

So if you have tried the method above, and you still got no ethernet recognition, then try to reset the CMOS from the mobo using a jumper.

Although, I recommend this as a last resort due to the fact that you're going to have to mess around with your computer insides.

---

### Post by jellopowderpuff on 2008-02-28
Anybody have a new link?  I get 404 for this:
[http://www.pcchips.com.tw/PCCWeb/Dow...uID=35&LanID=2](http://www.pcchips.com.tw/PCCWeb/Dow...uID=35&LanID=2)

---

### Post by JunCTionS on 2008-05-02
I know this post is more than 2 months old, but just in case you never found it, the link I used is going through the homepage: [www.pcchips.com](www.pcchips.com) then to Downloads 
Product Category
   Motherboards
   Socket 775 (in...
Model
   P23G

I flashed it under windows but it still didn't work. I think I'll try a cold boot just to be sure.

---

### Post by JunCTionS on 2008-05-02
had to reset the BIOS even if I flashed it.
and in case other people didn't understand it as first (as I didn't) this is a problem that does not come with linux at all, in my case in came when I entered the BIOS to change the Boot order to load the Live CD, here the old BIOS would then disable the ethernet.
and for the newcomers, if you don't want to have to reset the BIOS (which involves opening up the case) flash it before you enter the setup :)
good luck and thanks for the pointers

---

