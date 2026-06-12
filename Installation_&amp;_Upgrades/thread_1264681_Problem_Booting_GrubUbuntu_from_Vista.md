---
title: "Problem Booting Grub/Ubuntu from Vista"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by wpdj on 2009-09-12
I'm banging my head against the wall trying to boot Ubuntu from Vista. I've used bcdedit in Vista to make what I think are the appropriate changes to the Vista boot process. Once the Vista's boot manager starts I am able to select from the choices of Windows Vista or Grub. When I select Grub it fails with "Grub Invalid Partition Table."

My configuration is a pair of Raid1 drives for Vista and a 3rd drive for Ubuntu. I can successfully boot Ubuntu by changing the boot priority for the drives in the BIOS. While changing the hard disk boot priority is an adequate solution for me, it's not a good solution for other users of the system.

I believe that I need to modify grub's configuration so that it initiates stage1 from the Vista raid volume and continues with the follow-on stages from the Ubuntu drive. I've run the boot_info_script032.sh file and am attaching the RESULTS.txt file here.

Some help with grub configuration would be greatly appreciated.

Thanks!

---

### Post by rob-ward on 2009-09-12
Is there any perticular reason you arn't using grub to boot both vista and ubuntu, I have always fond that it is easier than trying to get the windows boot loader to point to grub to point to ubuntu

---

### Post by louieb on 2009-09-12
Believe  you need to put Grubs stage1 code in the PBR - yes that right the PBR (partition boot record). of partition sdc1.  

Perhaps the easiest way would be boot to Ubuntu - at the grub menu press **c**
for the **grub>** prompt. 

verify what grub calls the  PBR you want to modify 

```
find /boot/grub/stage2
``` 

will return the partition where stage2 is found example [B](hd0,0)  

[/B]```
root **(hd0,0)**
setup** (hd0,0)**
quit

```
That should allow Vista to chainload Grub. 

Nice explication of the Vista/Win7 boot process - [Multibooters, Pictures here worh 1000+ words]("http://www.multibooters.co.uk/multiboot.html")

---

### Post by wpdj on 2009-09-12
> **rob-ward said:**
> Is there any perticular reason you arn't using grub to boot both vista and ubuntu, I have always fond that it is easier than trying to get the windows boot loader to point to grub to point to ubuntu

I'm avoiding the approach of having grub boot both OSs because I'm uncertain how that approach would work with the raid configuration. I've already seen that Ubuntu doesn't recognize the individual drives as a raid volume.

---

### Post by wpdj on 2009-09-12
> **louieb said:**
> Believe  you need to put Grubs stage1 code in the PBR - yes that right the PBR (partition boot record). of partition sdc1.  


I'm reasonably sure that the stage1 code needs to be resident on the Vista partition so that Vista's Boot Manager can initiate Grub. From the way I'm interpreting the RESULTS.txt file, Grub isn't looking in the right place for stage2.

---

### Post by louieb on 2009-09-12
> **wpdj said:**
> I'm reasonably sure that the stage1 code needs to be resident on the Vista partition ... 

That was true in XP   - Vista is  a whole different animal.  Are you using EasyBCD?

Where did you get your stage1 code?

---

### Post by wpdj on 2009-09-12
> **louieb said:**
> That was true in XP   - Vista is  a whole different animal.  Are you using EasyBCD?

Where did you get your stage1 code?

I'm not using EasyBCD; I'm editing the Vista System Store directly with bcdedit. I got the stage1 code by dd'ing it from the drive where Ubuntu was installed. Specifically I did this:
% dd if=/dev/sdc of=/linux.bin bs=512 count=1
and then copied the linux.bin file to the Vista C: drive. Vista's boot manager definitely loads the linux.bin file otherwise I wouldn't be getting to Grub at all.

---

### Post by louieb on 2009-09-12
Ok think this is what may be going on - Grub numbers drives  by boot order.
It looks like the stage1 file you copied is trying to boot the 1st drive in the boot order.  Guess you'll just have to try and build a stage1 that looks on the 3rd drive.   

Just wonder if you had sdc 1st in the boot order when you install Ubuntu?

lol - interesting problem

From the results.txt

```

sda1: ____________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     [COLOR=Red]Grub0.97 in the file /linux.bin looks at sector 1 of 
                       the same hard drive for the stage2 file.[/COLOR] A stage2 file 
                       is at this location on /dev/sdc. Stage2 looks on the 
                       same partition for /boot/grub/stage2.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

```

---

### Post by wpdj on 2009-09-12
> **louieb said:**
> Ok think this is what may be going on - Grub numbers drives  by boot order.
It looks like the stage1 file you copied is trying to boot the 1st drive in the boot order.  Guess you'll just have to try and build a stage1 that looks on the 3rd drive.   

Just wonder if you had sdc 1st in the boot order when you install Ubuntu?


I agree that I need to build a stage1 that looks on the 3rd drive. Any suggestions on how to do it?

I honestly don't remember whether the target drive for Ubuntu was first in the BIOS priority when I installed from the Live CD. I'm thinking it wasn't since the menu.lst file that resulted from the grub install identified the Vista OSs on hd0 and hd1...

---

### Post by louieb on 2009-09-12
> **wpdj said:**
> I agree that I need to build a stage1 that looks on the 3rd drive. Any suggestions on how to do it?

Haven't got a clue. -  actually I do but - its kinda crazy.  Here  it goes. Boot order sda sdb sdc - boot to live CD - at grub> prompt - root (hd2,0) - setup (hd0) - quit. Now you have a stage1 in the MBR of sda  that points to sdc - copy it off and and restore windows IPL code to the MBR. 

Gota be a safer saner way - do you a spare drive to temporarily replace sda with? 

> I'm thinking it wasn't since the menu.lst file that resulted from the grub install identified the Vista OSs on hd0 and hd1...     Saw that too - when you installed Ubuntu I guess you press the advanced button on the live cd or use the alternate cd to get gurb in the MBR of sdc?

---

### Post by wpdj on 2009-09-12
> **louieb said:**
> Haven't got a clue. -  actually I do but - its kinda crazy.  Here  it goes. Boot order sda sdb sdc - boot to live CD - at grub> prompt - root (hd2,0) - setup (hd0) - quit. Now you have a stage1 in the MBR of sda  that points to sdc - copy it off and and restore windows IPL code to the MBR. 

Gota be a safer saner way - do you a spare drive to temporarily replace sda with? 

Saw that too - when you installed Ubuntu I guess you press the advanced button on the live cd or use the alternate cd to get gurb in the MBR of sdc?

Yes, I used the advanced button to specify that the bootloader should be on sdc.

setup (hd0) seems destructive ;-)

Looking at the grub documentation I get the feeling that "install" can be made to do what I need, if I understand it correctly (which I don't entirely).

---

### Post by louieb on 2009-09-12
The setup command gives grub the target MBR or PBR to put the stage1 file. 

Don't recall ever using the grub-install command. The method I described in post #3 is referenced as [Installing grub natively]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively") in the [GNU GRUB Manual 0.97]("http://www.gnu.org/software/grub/manual/grub.html")    and gives this waring
> **Caution:** Installing GRUB's stage1 in this manner will erase the normal boot-sector used by an OS.     The advantage is I control which boot sector I'm going to erase / overwrite. And since you already know how to backup an MBR its just a matter of restoring it if needed. 

[grub-install]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall") has its own waring 
> **Caution:** This procedure is definitely less safe...  several ways in which your computer can become unbootable. For example, most operating systems don't tell GRUB how to map BIOS drives to OS devices correctly&#8212;GRUB merely guesses the mapping..BTW: Have you tried the 1st Windows option when you boot to the drive with Ubuntu?  My guess is that it would work. Won't hurt anything to give it a try.

---

### Post by wpdj on 2009-09-13
> **louieb said:**
> The setup command gives grub the target MBR or PBR to put the stage1 file. 

Don't recall ever using the grub-install command. The method I described in post #3 is referenced as [Installing grub natively]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively") in the [GNU GRUB Manual 0.97]("http://www.gnu.org/software/grub/manual/grub.html")    and gives this waring
The advantage is I control which boot sector I'm going to erase / overwrite. And since you already know how to backup an MBR its just a matter of restoring it if needed. 

[grub-install]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall") has its own waring 

Right now I'm making an image of the current state of the Windows installation. Once that completes I'll give your idea a shot.

> **louieb said:**
> BTW: Have you tried the 1st Windows option when you boot to the drive with Ubuntu?  My guess is that it would work. Won't hurt anything to give it a try.

Actually no, I haven't tried booting Windows from the Grub/Ubuntu boot choices. In order to boot Ubuntu from sdc I have to make that drive the first priority in the BIOS drive ordering. This BIOS only allows me to only include one hard disk volume in the three choices for boot priority (e.g.,  (1) IDE STxxxx, (2) CD-ROM, (3) Removable Drive). With the Ubuntu drive (the IDE STxxxx drive) first I'm not sure whether Windows will see the raid array as its first drive. And I'm not convinced that the grub map command will help in this regard since that only specifies a single device.

But as you say, trying it probably won't hurt.

---

