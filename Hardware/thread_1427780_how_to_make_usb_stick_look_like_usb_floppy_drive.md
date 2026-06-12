---
title: "how to make usb stick look like usb floppy drive?"
date: 2010-03-11
forum: Hardware
---

### Post by MichaelBurns on 2010-03-11
I have figured out how to make the contents of my usb stick "look like" the contents of a floppy - I think.  I used "dd" to write an exact copy of various boot floppy images, and then used "dd" again to look at the results on the usb stick.  It "looks good", with the appearance of "FAT12" and such in the first 512 bytes.  From nautilus I see various files that "look like" what I would expect to see on a boot floppy.  However, the usb stick still hotplug-mounts the same way.

I want the usb stick to mount from "/dev/fd0" (well, I'm not quite sure, maybe "/dev/fd/0"?), but instead it mounts from "/dev/sdx" (where "x" is some letter) as if it is still a usb stick (duh).  Apparently udev takes care of this.  That's fine.  What I want to know is:  what can I do to the usb stick in order to "trick" udev?

I want to "trick" my laptop into thinking that the usb stick is actually a usb floppy drive at a very low level, so that I can "trick" my bios to boot from it.  Apparently, byte-level writing to the boot sector is not low-level enough.  I have a bios setting for "usb floppy legacy emulation", and I'm assuming that this is for booting from a usb floppy drive.  But, apparently, the usb stick still looks like a usb stick rather than a floppy drive, regardless of my low-level attempts to disguise it as a floppy.

Any ideas?  Hopeless?

---

### Post by Fafler on 2010-03-12
It's is not possible to do it that way. Tricking Linux into believing it's a floppy drive is far away from enough to trick the BIOS. BIOS will still see the drive as a flashdrive because of the firmware in the flashdrive says so. There might be utilities out on the net that can change that, but i have no knowledge about that.

Pressing F12 at boot time doesn't give you an option for booting from the flashdrive?

---

### Post by Post Monkeh on 2010-03-12
you can't do this - your bios HAS to support booting from usb otherwise you can't boot from a usb, but if your laptop doesn't have a floppy drive, it should have an option to boot from usb. your bios will never see your usb device as a floppy, it will only see it as a usb device.

you can set a full size usb to be bootbable, i have 9.10 booting from my usb stick.

what exactly are you trying to boot?

---

### Post by MichaelBurns on 2010-03-12
I have not tried f12; I will try that next time I reboot.

Ultimately, I want to boot ubuntu from the usb stick, but for now, I'm just trying to boot dos.

Any ideas what is the purpose of the usb floppy legacy emulation in my boot menu?

---

### Post by Post Monkeh on 2010-03-12
> **MichaelBurns said:**
> I have not tried f12; I will try that next time I reboot.

Ultimately, I want to boot ubuntu from the usb stick, but for now, I'm just trying to boot dos.

Any ideas what is the purpose of the usb floppy legacy emulation in my boot menu?

you're trying to boot dos from your usb?

can't really help you there, i've only ever booted ubuntu (made by going into system > administration > usb startup disk creator)  but you don't or shouldn't need to do loads of fiddling to your usb stick. all you should need to do is set the bootable flag (which the usb startup disk creator does for you anyway) and put the necessary files on. if your bios is capable of booting from usb you should see an option if you hit the right button to bring up your bios boot device selector. if your bios setup screen offers options for usb i'd imagine you should be able to boot from usb somehow.

make sure you follow a guide relevant for the os you're trying to boot. you need to make sure all the right files are copied, for a dos boot disk it would need to have the right MBR installed (on to the usb stick) i'd imagine, as i said i've only ever done it with ubuntu which installs grub direct to the usb stick.

---

### Post by srs5694 on 2010-03-12
The key to bring up boot options varies from one BIOS to another. Sometimes it's F12, other times it's F10, and it may be other things on some systems, too. There's usually a prompt during the boot process, although it's easy to miss -- it's usually only present for a few seconds and then vanishes.

Your motherboard documentation might describe the purpose of "USB floppy legacy emulation" in more detail. My hunch, based only on the name, is to enable the BIOS to treat a true floppy drive that connects via USB like it treats a floppy drive that connects to the motherboard, so that you can use boot floppies via USB floppy drives and access them as floppies from DOS. Such devices do exist -- or at least they did. (I haven't looked for one recently.) I doubt if USB floppy drives look exactly like USB flash drives to either the BIOS or an OS, but I can't really be sure of that since I've never used one.

All the BIOSes I've seen in the last two or three years, if not longer, have supported booting from USB disk devices such as USB flash drives. Such an option might not be active by default, though. If you can't find it in a boot option when you press F12 (or whatever), try entering your BIOS setup utility (usually by pressing F2 or Del, but some systems use other keys) and searching for it. If your computer is very old, you might be out of luck.

---

### Post by Joshua on 2011-01-10
> **MichaelBurns said:**
> I have not tried f12; I will try that next time I reboot.

Ultimately, I want to boot ubuntu from the usb stick, but for now, I'm just trying to boot dos.

Any ideas what is the purpose of the usb floppy legacy emulation in my boot menu?

Did anyone ever figure out how to make this work?  I think I'm trying to do the same thing.

I have an old laptop (Averatec 3280).  I want to re-purpose the laptop and make it boot from something other than a hard disk or optical disk (I want it to be silent, and they're too loud) and I want it to be wireless (of course I'll have a power cable, but I don't want a network cable).  BIOS gives the option to boot four things:

> Removable Dev.
CD/DVD:HL-DT-ST DVD-RW GCA-4080
HDD:IBM-DJSA-210
Network:PXE 2.33

As far as I know, there is no option to bring up a BIOS boot menu.  I'm pretty sure boot menus and general USB booting ability were not common when this laptop was made.  Based on my criteria, I think that getting "Removable Dev." to work is the only option.  In my laptop, I have some options for enabling "Legacy USB Support" which may be similar to your "USB Floppy Legacy Emulation" and I believe the purpose of that and the "Removable Dev." option are to allow booting from a USB Floppy drive.  I've been trying the same thing - using dd and various floppy images to make USB flash based media look like a floppy disk (thumb drives, SD cards, etc.).  Unsuccessful so far.  Like you, I would eventually like to boot into an Ubuntu variant, but I'd settle for anything right now, as long as it's not hard drive or optical drive based.

Oh, and I know I could buy an SSD or IDE-to-compact flash adapter, but I'd prefer not to put the money into it.

---

### Post by cpmman on 2011-01-18
This may help:

[_***http://ubuntuforums.org/showpost.php?p=10366070&postcount=18***_]("http://ubuntuforums.org/showpost.php?p=10366070&postcount=18")

My usb hard disk ceased booting after a grub2 update but now the Plop Boot Manager is able to load the usb module(s) necessary to boot from usb - it does for my external disk and it may from a usb stick.

Good luck and let us know if it does - we could keep other live cd images and/or distros on sticks with the improved access times over cd even on those machines like mine with no bios usb facility.

---

### Post by Joshua on 2011-01-18
> **cpmman said:**
> My usb hard disk ceased booting after a grub2 update but now the Plop Boot Manager is able to load the usb module(s) necessary to boot from usb - it does for my external disk and it may from a usb stick

I don't understand how this would work.  Is your USB hard disk the only bootable device on the system?  So that disk contains GRUB, GRUB2, Plop, or whatever you're using?

If you are able to boot from that disk, and access the boot loaders, doesn't that mean you have USB support in the BIOS?  Or did you need to do something to the disk itself to get it recognized by the BIOS?

---

### Post by cpmman on 2011-01-18
I have an old Acer TravelMate which does not provide for booting from usb.  It has a 30Gb internal disk which contains 20Gb of XP and 10Gb of Maverick (in separate / and /home partitions).  The plpbt.bin file is placed in /boot on that partition and I have placed a plop boot menu in /etc/grub.d/40_custom which points to the usb external disk partition containing the grub2 (i.e. a normal installation on the usb drive).

The documentation in the Plop download readme.txt file once unzipped explains how to install for various boot systems including dos,grub,grub2,LILO,Windows and others to install to hard disk,cd,floppy,usb.

```
Run from GRUB2 
     __________________________________________________________________ 
 
   Download the current boot manager [104]plpbt-5.0.11.zip. Extract it to 
   get the boot manager binary program plpbt.bin. 
 
   Copy the plpbt.bin file to /boot. 
 
   You have to choose the correct root settings in grub.cfg for your 
   system. 
   The following is an example 
menuentry "Plop Boot Manager" { 
    set root=(hd0,1) 
    linux16 /boot/plpbt.bin 
} 
 
   When you reboot, you should be able to start the boot manager from your 
   grub menu. 

```I installed mine to my bootable internal hard disk but rather than edit the grub.cfg (which is deprecated in grub2) I added it into the 40_custom file so that it will survive any more grub updates that may occur.  Mine reads 

```
menuentry "Plop Boot Manager" { 
    set root=(hd0,2) 
    linux16 /boot/plpbt.bin 
} 

```The Plop menu allows you to boot from any device attached and powered on to your machine.  I think it contains the usb module(s) that grub2 seems to have lost in the last couple of months.

---

### Post by MichaelBurns on 2011-01-19
*accidental double post; not sure why*

---

### Post by MichaelBurns on 2011-01-19
@Joshua:
If you can tolerate the noise from a *very* brief access to your optical or hard drive that occurs only at the very beginning of the boot, then Plop may be the way to go.  I wound up using Plop for my solution (although noise wasn't at all a concern for me).  I didn't notice much noise from it.  It probably spun for about a second to load the Plop boot loader, and then jumped right to the usb.  (I modified the configuration file before burning so that it would boot automatically to usb.)  I was even able to eject the Plop disk within seconds, well before Ubuntu was anywhere near finished loading.  After that, it was all completely silent from the usb (and the godaweful noise from my cpu fan, which begs the question: is your optical drive really such a noise problem whereas your cpu fan is tolerable?).

---

### Post by Joshua on 2011-01-20
I was planning to use the thing as a network music jukebox in my kitchen that would play a slideshow or something when it wasn't doing anything else.  My goal was to make it small and to boot VERY fast.  So I planned to strip it of anything unneeded (including the optical drive) and mount it on the wall or something (maybe digital-picture-frame-style).

I see how I could use the optical drive, or another hard drive, but even disregarding the noise, either of them would slow the boot process because they have to spin up before use (I expect spinup to be a bigger delay than reading the data because there will be very little software to load).  I'm starting to think I'll just use a flash card mounted in place of the hard disk.  I have an unused 4 GB compact flash card laying around, and I found [this]("http://www.amazon.com/gp/product/B0036DDXUM/ref=oss_product") to make it look like a normal hard disk.  I think it will be worth the $10.

As far as the CPU fan, I'm planning to scale the processor to half speed (1.6 GHz to 800 MHz).  Hopefully that will almost eliminate the fan noise.

---

### Post by Joshua on 2011-01-20
Sorry, duplicate post.  Is there a way to delete these?

---

