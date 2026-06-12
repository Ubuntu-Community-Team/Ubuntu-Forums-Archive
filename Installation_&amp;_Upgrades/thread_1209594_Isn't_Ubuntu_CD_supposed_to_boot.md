---
title: "Isn't Ubuntu CD supposed to boot?"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by New2Linux8 on 2009-07-10
Hi, I'm new here... an experienced programmer but not a Unix/Linux expert ... 
 
An old WindowsME system of mine blew up and I can't restore it, so I decided to go to Linux. I downloaded Ubuntu v9 and burned the CD on my Vista machine.
 
I thought I read that the cd is supposed to boot when I put it in the WinME system, but it doesn't. The CD tries to read, but then it goes back to WinME and bombs again.
 
Any help would be appreciated. I have no idea what's next.

---

### Post by estyles on 2009-07-10
Does the CD boot on your Vista machine?

Two likely causes: 1) The CD didn't burn right.  2) Your BIOS isn't set up to boot from CD.

---

### Post by New2Linux8 on 2009-07-10
Thanks....
 
I won't try to boot it on the Vista machine -- don't want to risk losing the o/s.
 
On the Win ME machine, the BIOS is set to boot the CD and floppy before the hard drive.  Vista is so obtuse that I don't know if it's burned right... took 2 tries, first failed because the default is RW format and the iso file didn't fit. So I changed to the other format, apparently for CD-R disks.

---

### Post by 73ckn797 on 2009-07-10
Was it burned as an image (iso)?

---

### Post by estyles on 2009-07-10
> **New2Linux8 said:**
> Thanks....
 
I won't try to boot it on the Vista machine -- don't want to risk losing the o/s.


I'm not telling you to install it.  Just stick it in the drive and reboot.  It's not some crazy monster that's going to overwrite your hard drive on reboot.

The whole point of the live CD is that you can boot up with it and try out Ubuntu without making any changes whatsoever to your system - it leaves the harddrive alone unless you select "Install".

---

### Post by estyles on 2009-07-10
> **73ckn797 said:**
> Was it burned as an image (iso)?

This is a good point too.  If you put the disk in your machine and browse to it, does it show several files and directories, or does it just show a *.iso file?  If it just shows an iso file, it's not burned right.

Another thing to try would be to put another bootable CD (like a Windows CD) into the machine that you're trying to use...  just to see if that one boots up.

---

### Post by b@sh_n3rd on 2009-07-10
> **New2Linux8 said:**
> ...I won't try to boot it on the Vista machine -- don't want to risk losing the o/s...

I'd be worried booting into my *Ubuntu* machine with a Winblows cd worried I'll lose *my* OS :lolflag:

Hi **New2Linux8**, to be able to boot into the LiveCD, you should setup your PC so in the BIOS setup menu. Any luck on that? It's quite simple...When your PC boots it'll tell you to press a series of keys or a key (i.e: F2; Ctrl+Alt+Del) to enter the setup menu. Then in the setup menu there should be section that mentions something like, "Boot order". There make your CD-ROM drive the first boot device. That oughta do it if your CD compilation is good.

---

### Post by b@sh_n3rd on 2009-07-10
> **estyles said:**
> ...I'm not telling you to install it.  Just stick it in the drive and reboot.  **It's not *some crazy monster* that's going to overwrite your hard drive on reboot**...
:lolflag: :lolflag:

---

### Post by unlimitedz on 2009-07-10
> **estyles said:**
> This is a good point too.  If you put the disk in your machine and browse to it, does it show several files and directories, or does it just show a *.iso file?  If it just shows an iso file, it's not burned right.

He's right, You want to use the option in your CD burning software to "Burn Image to Disk" as it's most commonly referred to.  Otherwise, if you do something like a "Burn Data" or similar, you will get a CD with just the .iso file on it, which is not what you need.  An ISO is an "Image" of a disk.;)

---

### Post by jrox717 on 2009-07-10
The first thing I would try is to boot from the Ubuntu cd on your Vista machine. All you do is reboot the computer with the cd in the drive, then a menu will show up and you can select "Try Ubuntu with no change to my computer" (obviously just don't select "Install Ubuntu" and you'll be fine). If that works, but you aren't able to boot from the cd on your ME machine, I would try something like Smart Bootmanager, which I've used. You can make a bootable floppy disk and boot into that, then select your cd drive and it will boot from the Ubuntu cd. 
Obviously, if you can't boot to the cd on the vista machine, then there's a problem with the cd and you need to burn it over again.
Good luck! I hope you enjoy using Ubuntu!

---

### Post by New2Linux8 on 2009-07-10
Thanks everyone!!.... 
 
Not sure if this is the answer, but I accidentally copied the file "desktop.ini" that Vista set up in the "to be burned" folder, to the CD. I'm making a new disk with only the iso file... someone else asked if the ubuntu file was an iso file... yes, it was/is.
 
*** well that's not it!!  I guess Windows needs that file... on my Vista machine, the o/s says please insert a disk after I insert it and close the drive door!

---

### Post by estyles on 2009-07-10
> **New2Linux8 said:**
> Thanks everyone!!.... 
 
Not sure if this is the answer, but I accidentally copied the file "desktop.ini" that Vista set up in the "to be burned" folder, to the CD. I'm making a new disk with only the iso file... someone else asked if the ubuntu file was an iso file... yes, it was/is.
 
*** well that's not it!!  I guess Windows needs that file... on my Vista machine, the o/s says please insert a disk after I insert it and close the drive door!

Did you check the files on the burned disk (presumably the first one, since you say you can't access the second one on your vista machine)?  If you burned it as data, which is a common mistake, then the drive will contain just one file - the .iso file.  That won't work.

If you burned it properly, then the disk should show several files and directories.

---

### Post by New2Linux8 on 2009-07-10
I think this is the problem. Am I supposed to use "Infra Recorder" to convert the iso file to the format (folders/files) it's supposed to be on the CD? All that's on the cd is the iso file.

---

### Post by merlinus on 2009-07-10
Select disk image, and then navigate to the .iso.  Do not burn as a data disk!

---

### Post by 73ckn797 on 2009-07-10
If you have burned the ISO as an ISO using whatever program you burn with, then the disk contents will list as seen in the screenshot attached to this message. The example given is Ubuntu 9.04.

[IMG]http://ubuntuforums.org/home/frank/Desktop/Screenshot.png[/IMG]

---

### Post by Ra-Hoor-Khuit on 2009-07-10
How to Burn Ubuntu to ISO (Using Infra Recorder):

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by New2Linux8 on 2009-07-10
HOPELESS !!
 
I used Infra Recorder according to the instructions on the web page [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
 
I used the button "'Write Image" as it said, selected the iso file I downloaded, it wrote the cd, and when I put the cd back in the drive to look at it, Vista tells me to insert a disk, so I think it's not valid.
 
I have no idea what is wrong with this process.

---

### Post by merlinus on 2009-07-10
Boot your computer from the cd, not run the cd from vista.

---

### Post by dogbitedavehumphreys on 2009-07-10
Well HOWDY!

Am so totally brand new here (like I registered 10 minutes ago).

I have this exact same problem.  Am trying to set up old Millenium PC as a server (kind of for the hell of it, a journey of a thousand miles begins with one step and all that), downloaded Server install as ISO, saved to disk and

doesn't load on boot
doesn't load on boot on my laptop (XP)

I have set BIOS for floppy at startup on ME to no avail

and I could use any suggestions that you all have.

and, have a nice day.

---

### Post by New2Linux8 on 2009-07-10
> **merlinus said:**
> Boot your computer from the cd, not run the cd from vista.
 
An earlier post said that I should be able to look at the contents of the disk to see that it was OK. I'll try to boot it on my dead win ME machine that I'm trying to migrate to Linux.
 
thanks so much ---- again!!!!

---

### Post by KarmicKoalaa on 2009-07-10
Try different burning software, I used InfraRecorder to burn my Windows 7 disc and it didn't work so had to reburn it using something else. I can't remember what I used to burn my Ubuntu disc though.

---

### Post by New2Linux8 on 2009-07-10
UPDATE -
 
The cd is no good.  can't read it on the Vista machine,  can't boot it on the Win ME machine.  The BIOS is set to boot the CD first.  It's not a good disk.
 
I'm going to restore the original Win ME (which is pre-service-pack 2 crap), then ... not sure.

---

### Post by 73ckn797 on 2009-07-10
A very good and free burner program is called "CDBurnerXP" found here: [http://cdburnerxp.se/](http://cdburnerxp.se/)

---

### Post by 73ckn797 on 2009-07-10
> **New2Linux8 said:**
> UPDATE -
 
The cd is no good.  can't read it on the Vista machine,  can't boot it on the Win ME machine.  The BIOS is set to boot the CD first.  It's not a good disk.
 
I'm going to restore the original Win ME (which is pre-service-pack 2 crap), then ... not sure.


Did you burn the disk at the slowest speed? That can sometimes be a problem when burning too fast.

---

### Post by New2Linux8 on 2009-07-10
> **73ckn797 said:**
> Did you burn the disk at the slowest speed? That can sometimes be a problem when burning too fast.
 
 
No, but I used 4x speed. not the slowest, but slow. It finished "normally".
 
Maybe because the drive is a CD-RW/DVD-R ?  The program isn't giving the option of making the disk a CD-R... or is it doing that anyway?  Not sure. But still, it should be able to read what it wrote.

---

### Post by andrewc6l on 2009-07-10
Some older combo DVD/CD readers can't read CD-R. I've run into that before; I ended up buying a real DVD/CD-RW and popping that in instead.

---

### Post by az on 2009-07-10
> **New2Linux8 said:**
> HOPELESS !!
 
I used Infra Recorder according to the instructions on the web page [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
 
I used the button "'Write Image" as it said, selected the iso file I downloaded, it wrote the cd, and when I put the cd back in the drive to look at it, Vista tells me to insert a disk, so I think it's not valid.
 
I have no idea what is wrong with this process.

Can you post the name of the iso file and how big it is?  

You did follow the correct steps.  Although there's obviously lots that can go wrong, I don't think it's your fault.  If the iso is the appropriate size, then I would try burning it again to another blank disk.

It should mount and read fine in Vista once you burn it.  Once you can do that, try booting from it.

---

### Post by 73ckn797 on 2009-07-10
> **New2Linux8 said:**
> No, but I used 4x speed. not the slowest, but slow. It finished "normally".
 
Maybe because the drive is a CD-RW/DVD-R ?  The program isn't giving the option of making the disk a CD-R... or is it doing that anyway?  Not sure. But still, it should be able to read what it wrote.

That was slow enough so scratch that idea!!

---

### Post by New2Linux8 on 2009-07-10
> **az said:**
> Can you post the name of the iso file and how big it is? 
 
You did follow the correct steps. Although there's obviously lots that can go wrong, I don't think it's your fault. If the iso is the appropriate size, then I would try burning it again to another blank disk.
 
It should mount and read fine in Vista once you burn it. Once you can do that, try booting from it.
 
 
 
Actually, I renamed the part before the first dash in the file name. 
 
The new name = ubuntu-9.04-desktop-i386.iso
 
The size shown in Windows = 715,732KB
The size shown in DOS = 732,909,568

---

### Post by b@sh_n3rd on 2009-07-11
Hey I just remembered something. I saw in a different thread (can't remember what it was) where someone had a problem booting the LiveCD. In that case he was using a CD-RW and apparently a CD-RW is no go for Linux. God only knows why. Bottom line is, are you using a CD-RW by any chance? Any luck on trying a normal CD-R? I used Nero 6 that came with my DVD-RW to burn my Ubuntu disks. It worked ok. Oh and 4x is good, I've done it at that speed too. Hope this helps...

---

### Post by New2Linux8 on 2009-07-13
> **b@sh_n3rd said:**
> Hey I just remembered something. I saw in a different thread (can't remember what it was) where someone had a problem booting the LiveCD. In that case he was using a CD-RW and apparently a CD-RW is no go for Linux. God only knows why. Bottom line is, are you using a CD-RW by any chance? Any luck on trying a normal CD-R? I used Nero 6 that came with my DVD-RW to burn my Ubuntu disks. It worked ok. Oh and 4x is good, I've done it at that speed too. Hope this helps...
 
Am I allowed to resume this after 2 days? Was away for a while.
 
The issue above may be significant but I'm not convinced ... I'm using a DVD-R / CD-RW but creating a READ-ONLY DISK! ... the default formatting option has to be changed before writing. I know it creates a good CD-R (not always true for CD-RW !! )
 
The reason I'm not convinced is because Vista could not read the disk after it was created with the utility, but if burned with Vista, it can. I think it has to do with the hidden or system file "desktop.ini" ... which of course, if it's in the way, may screw up a bootable format (I have no idea how a CD is made bootable, tho I used to write bootstraps for 5-1/4 inch floppies when they were used in PDP-11's).
 
Is there a way to use a utility to create the folders/files on my hard drive, then burn it all the the CD using Vista?

---

### Post by az on 2009-07-13
> **New2Linux8 said:**
> Am I allowed to resume this after 2 days? Was away for a while.
 
The issue above may be significant but I'm not convinced ... I'm using a DVD-R / CD-RW but creating a READ-ONLY DISK! ... the default formatting option has to be changed before writing. I know it creates a good CD-R (not always true for CD-RW !! )
 
The reason I'm not convinced is because Vista could not read the disk after it was created with the utility, but if burned with Vista, it can. I think it has to do with the hidden or system file "desktop.ini" ... which of course, if it's in the way, may screw up a bootable format (I have no idea how a CD is made bootable, tho I used to write bootstraps for 5-1/4 inch floppies when they were used in PDP-11's).
 
Is there a way to use a utility to create the folders/files on my hard drive, then burn it all the the CD using Vista?

Here is the standard for bootable CDROM:
[http://en.wikipedia.org/wiki/El_Torito_(CD-ROM_standard](http://en.wikipedia.org/wiki/El_Torito_(CD-ROM_standard))

Basically, the hidden file you describe has nothing to do with creating a bootable disk.  The iso image is the iso9660 filesystem along with the bootable image all wrapped in one.  You cannot even access the bootable part from the mounted cd image.  

I don't know why this is not working for you.  But the problem is not with the ISO image format.  You don't need to play around with files.  You need to find out why your burner is not making the disk properly out of the iso file.

---

### Post by New2Linux8 on 2009-07-13
> **az said:**
> Here is the standard for bootable CDROM:
[http://en.wikipedia.org/wiki/El_Torito_(CD-ROM_standard](http://en.wikipedia.org/wiki/El_Torito_(CD-ROM_standard))
 
Basically, the hidden file you describe has nothing to do with creating a bootable disk. The iso image is the iso9660 filesystem along with the bootable image all wrapped in one. You cannot even access the bootable part from the mounted cd image. 
 
I don't know why this is not working for you. But the problem is not with the ISO image format. You don't need to play around with files. You need to find out why your burner is not making the disk properly out of the iso file.
 
 
OK, so tell me if I got this right... as I thought from step 1, since the iso file is an image of the CD, it should be copied to the CD as a sector-by-sector copy, with sector 0 of the file going to sector 0 of the CD (or other base as in the 9660 spec), not as a file and not as its expanded folders/files.
 
If that's the case, I know of no way that Vista wil do that kind of copy. That would explain why it doesn't work.
 
***  JUST TRIED A NEW CD, USED CDBurnerXP to copy an iso file, and it seems to have worked.
 
The CD is readable by Vista, and it appeared with the option to either copy it or boot it.  It has  wubi.exe  in the root directory, and it has the first few folders named as
 
.disk
casper
dists
install
 
etc.

---

### Post by optikal1 on 2009-07-13
Bingo!!!
 
Now go and boot your other machine with this CD.

---

### Post by 73ckn797 on 2009-07-13
> **New2Linux8 said:**
> OK, so tell me if I got this right... as I thought from step 1, since the iso file is an image of the CD, it should be copied to the CD as a sector-by-sector copy, with sector 0 of the file going to sector 0 of the CD (or other base as in the 9660 spec), not as a file and not as its expanded folders/files.
 
If that's the case, I know of no way that Vista wil do that kind of copy. That would explain why it doesn't work.
 
***  JUST TRIED A NEW CD, USED CDBurnerXP to copy an iso file, and it seems to have worked.
 
The CD is readable by Vista, and it appeared with the option to either copy it or boot it.  It has  wubi.exe  in the root directory, and it has the first few folders named as
 
.disk
casper
dists
install
 
etc.

Good to hear you have made progress. Let us know how it goes from here.

---

### Post by az on 2009-07-13
> **New2Linux8 said:**
> OK, so tell me if I got this right... as I thought from step 1, since the iso file is an image of the CD, it should be copied to the CD as a sector-by-sector copy, with sector 0 of the file going to sector 0 of the CD (or other base as in the 9660 spec), not as a file and not as its expanded folders/files.
 
If that's the case, I know of no way that Vista wil do that kind of copy. That would explain why it doesn't work.
 
I'm glad you got it working.

When you download the iso from ubuntu.com, you are shown this message:

"Learn how to create a CD from your newly downloaded file: https://help.ubuntu.com/community/BurningIsoHowto"

And that explains how to do it using InfraRecorder, a free application for windows. Most other burning applications like Nero or Roxio have the option of burning an iso to disk.

---

