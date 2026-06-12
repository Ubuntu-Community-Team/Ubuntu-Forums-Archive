---
title: "Installing grub2 bootloader in fd0"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Rumpty on 2009-10-29
I wanted to install grub2 bootloader in fd0 during the installation, but that wasn't allowed, so didn't install it anywhere. No problem, I have now booted into Karmic by other means.

Created grub.cfg by running sudo update-grub2, and now I would like to install the bootloader in fd0. Is the command the same as grub1, <setup fd0> or is it different? Just wanted to play safe by checking about this command.

---

### Post by drs305 on 2009-10-29
The normal command is:
```

sudo grub-install /dev/sda

```
I haven't played with fd0

There is also the switch "--root-directory=DIR" which you might be able to use should G2 not be happy with fd0.

---

### Post by Rumpty on 2009-10-30
Thanks drs305.

 The "normal" command didn't work. I tried adding the fd0 to the device.map (not exactly sure of the format of this with a floppy drive) but still no joy.

I'll have to research that switch you mentioned.

---

### Post by JBAlaska on 2009-10-30
Try this [HowTo](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

---

### Post by Rumpty on 2009-10-30
I think that HowTo is strictly for the old (I'll always remember you. Sniff) grub, not for grub2.

---

### Post by Herman on 2009-10-30
:D There's a really cool new command that comes with GRUB 2 which replaces about a dozen or so other commands and it's designed specifically for automatically making an .iso file with GRUB 2 in it or a GRUB 2 floppy disc image!

I haven't tried the floppy disc option yet as I don't use floppy discs so much anymore, I'm getting too many 'dud' disks, I think the quality has gone down or I'm not able to source a decent brand.

I can say that the grub-mkconfig command is great for making an .iso image for burning to a CD though! If we use the --overlay=/boot/grub option it'll give us our own GRUB Menu complete with splashimage if we have one too. 
```
grub-mkrescue --overlay=/boot/grub GRUB2CD.iso
```Maybe we can get together and figure our how to use the same command with the right options for creating a floppy disc image.
Is anyone interested?

I'm not sure but I think we need to include the --image-type=TYPE option and --emulation=TYPE option if we want to make a floppy disc image.
Maybe like:
```
grub-mkrescue --overlay=/boot/grub --image-type=floppy --emulation=eltorito GRUB2.img
```That was only a guess, maybe I'm wrong but I'll start playing with that and see if I can get it to work ...

... anyone else wanna join in and help? :D

EDIT, Silly me, emulation type is for CD-ROM only, we don't need that for making a floppy, this seems to do something good judging by the terminal feedback, 
```
grub-mkrescue --overlay=/boot/grub --image-type=floppy GRUB2.img
```Can anyone make a floppy disc and try it out to confirm that it really works?  :)

To make the copy the image file to the floppy disc one would use a command like the following,
```
[FONT=Bitstream Vera Sans Mono]dd if=[/FONT]GRUB2.img[FONT=Bitstream Vera Sans Mono] of=/dev/fd0[/FONT]
```

---

### Post by JBAlaska on 2009-10-30
> **Rumpty said:**
> I think that HowTo is strictly for the old (I'll always remember you. Sniff) grub, not for grub2.

Well Yea, but since your booting off a FD why would it matter if your using grub or grub2..I mean like all the config stuff is on the FD and it will still point to the same drive/partition..or am I wrong, since I haven't booted from a FD since Win95 CD install lol.

---

### Post by Rumpty on 2009-10-31
> **Herman said:**
> :D There's a really cool new command that comes with GRUB 2 which replaces about a dozen or so other commands and it's designed specifically for automatically making an .iso file with GRUB 2 in it or a GRUB 2 floppy disc image!

EDIT, Silly me, emulation type is for CD-ROM only, we don't need that for making a floppy, this seems to do something good judging by the terminal feedback, 
```
grub-mkrescue --overlay=/boot/grub --image-type=floppy GRUB2.img
```Can anyone make a floppy disc and try it out to confirm that it really works?  :)

To make the copy the image file to the floppy disc one would use a command like the following,
```
[FONT=Bitstream Vera Sans Mono]dd if=[/FONT]GRUB2.img[FONT=Bitstream Vera Sans Mono] of=/dev/fd0[/FONT]
```

That procedure worked fine Herman, made the Grub2 floppy disc.

Must try to bring myself up to speed regarding what can be done from the grub prompt!

---

### Post by Herman on 2009-10-31
> That procedure worked fine Herman, made the Grub2 floppy disc.
Must try to bring myself up to speed regarding what can be done from the grub prompt!:D Alright! Thanks for letting me know. 
Yes, it's mainly just a matter of knowing what commands to type.

It's certainly a lot easier to make your GRUBII CD or floppy disk than it used to be with GRUB Legacy. Just one or two commands replace quite a series of commands that were needed to do the same thing with GRUB Legacy.

Some useful links on GRUBII are here, (just in case you're interested),

[GRUB2 Pages]("http://members.iinet.net/%7Eherman546/p20.html") 

[GNU GRUB 2 Manual]("http://grub.enbug.org/Manual") - (under construction)

[Grub 2]("https://wiki.ubuntu.com/Grub2") - Ubuntu Wiki

[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") - drs305 - Ubuntu Web Forums
      
      [GRUB 2 Introduction]("http://ubuntuforums.org/showthread.php?t=1285897") - ranch hand - Ubuntu Web Forums

---

### Post by agrimstad on 2009-11-24
This **item** ([http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_Floppy_Disc]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_Floppy_Disc")) worked for me.

The result, however, is a bit more primitive than dropping into the command shell when you boot from your hard drive(s). I use lvm over raid for my various partitions, except that I have a separate raid partition not using lvm for /boot. The command shell sees all this and so booting from it is fairly straightforward. Here's what I do:

grub> set root=(md0)
grub> insmod /grub/linux.mod
grub> linux /vmlinuz-2.6.31-14-generic root=/dev/mapper/vg0-root
grub> initrd /initrd.img-2.6.31-14-generic
grub> boot

When booting from the floppy, the raid, mdraid, and lvm modules are not automatically loaded, so the first job--to avoid extra typing--is to load them.

This amounts to something like this:

grub> insmod (hd0,1)/grub/raid.mod
grub> insmod (hd0,1)/grub/mdraid.mod
grub> insmod (hd0,1)/grub/lvm.mod

and then proceeding as above.

What I haven't been able to get working is a command something like this:

grub-mkrescue --modules=raid,mdraid,lvm --overlay=/boot/grub --image-type=floppy /tmp/grub_two.dsk

grub-mkrescue doesn't report errors very well and, for whatever reason, ignored my --modules argument.

I wonder if anyone has yet worked this problem out.

---

### Post by oldtraveler on 2009-11-24
> 
Originally Posted by Herman View Post
There's a really cool new command that comes with GRUB 2 which replaces about a dozen or so other commands and it's designed specifically for automatically making an .iso file with GRUB 2 in it or a GRUB 2 floppy disc image!

EDIT, Silly me, emulation type is for CD-ROM only, we don't need that for making a floppy, this seems to do something good judging by the terminal feedback,
Code:

grub-mkrescue --overlay=/boot/grub --image-type=floppy GRUB2.img

Can anyone make a floppy disc and try it out to confirm that it really works?

To make the copy the image file to the floppy disc one would use a command like the following,
Code:

dd if=GRUB2.img of=/dev/fd0

That procedure worked fine Herman, made the Grub2 floppy disc.


Why am I getting No such device or address when I try to make the floppy disk?

phil@phil-desktop:~$ grub-mkrescue --overlay=/boot/grub --image-type=floppy GRUB2.img
Overlaying /boot/grub
1440+0 records in
1440+0 records out
1474560 bytes (1.5 MB) copied, 0.0235827 s, 62.5 MB/s
phil@phil-desktop:~$ dd if=GRUB2.img of=/dev/fd0
dd: opening `/dev/fd0': Permission denied
phil@phil-desktop:~$ sudo dd if=GRUB2.img of=/dev/fd0
[sudo] password for phil: 
dd: opening `/dev/fd0': No such device or address
phil@phil-desktop:~$

---

### Post by drs305 on 2009-11-24
> **oldtraveler said:**
> Why am I getting permission denied when I try to make the floppy disk?

Are you putting "sudo" in front of it?
```

sudo dd if=GRUB2.img of=/dev/fd0

```

---

### Post by oldtraveler on 2009-11-24
> **drs305 said:**
> Are you putting "sudo" in front of it?
```

sudo dd if=GRUB2.img of=/dev/fd0

```
Used sudo.  Then tried using a different floppy.  It was written to.  

Still no joy.  When booting from the new floppy I am greeted with sh: grub.

I typed boot.  Got error: no loaded kernel. 

Where do I go from here?

---

### Post by agrimstad on 2009-11-24
> **oldtraveler said:**
> Used sudo.  Then tried using a different floppy.  It was written to.  

Still no joy.  When booting from the new floppy I am greeted with sh: grub.

I typed boot.  Got error: no loaded kernel. 

Where do I go from here?

You have to issue some grub commands before you finally type boot. It sounds like you've never used grub's command shell before. It's not too friendly. I posted an example of what I did to get Ubuntu to boot earlier in this thread.

---

### Post by oldtraveler on 2009-11-24
> **agrimstad said:**
> You have to issue some grub commands before you finally type boot. It sounds like you've never used grub's command shell before. It's not too friendly. I posted an example of what I did to get Ubuntu to boot earlier in this thread.
I tried using your grub commands, but when I got to the second one - grub> insmod /grub/linux.mod - I got an error saying no such disk.  Also got errors with the 3rd and 4th grub commands.

---

### Post by agrimstad on 2009-11-24
> **oldtraveler said:**
> I tried using your grub commands, but when I got to the second one - grub> insmod /grub/linux.mod - I got an error saying no such disk.  Also got errors with the 3rd and 4th grub commands.

As I said, it's not user friendly.

I suspect what's happening is that whatever defaults grub2 has don't correspond to your disk partitioning scheme.

If you only have one hard drive and both / and /boot are on its first partition, which is probably a pretty common situation, I think the insmod command would be something like:

grub> insmod (hd0,1)/boot/grub/linux.mod

---

### Post by oldtraveler on 2009-11-24
I have two internal drives with an XP OS on the first disk and the Ubuntu OS on the 2nd disk at hdb5.

---

### Post by agrimstad on 2009-11-24
> **oldtraveler said:**
> I have two internal drives with an XP OS on the first disk and the Ubuntu OS on the 2nd disk at hdb5.

You know, learning grub stuff starting with grub 2 isn't the easiest way to go about it.

It sounds as if your linux (ubuntu) installation is then on (hd1,5). Your various partitions visible to grub should be shown when you issue the ls command. (You did read the manual, right?) So, assuming then that (hd1,5) is right--it showed up when you did

grub> ls

Then you could try:

grub> set root=(hd1,5)

To verify that this is correct--and I assume that / and /boot are on the same partition--do:

grub> ls /boot

You should see the grub directory.

grub> ls /

If you see your kernel and initrd image there, you're cooking with gas. The sequence is probably:

grub> insmod /boot/grub/linux.mod
grub> linux /vmlinuz-... root=/dev/hdb5

"..." is the rest of the kernel image file name.

grub> initrd /initrd-...
grub> boot

If you want to boot windows from the grub shell, you'll have to ask somebody else.

---

### Post by drs305 on 2009-11-24
If the previous suggestions don't work in loading a module, try this:

At a grub or grub-rescue prompt:
Even after setting the correct root, in my experiments with Grub 2 to add a module I had to run the complete path, such as:
> insmod (hd0,1)/boot/grub/linux.mod

---

### Post by oldtraveler on 2009-11-24
I have tried both #18 and #19 above.  grub> ls shows several partitions on both disks such as hd1,5 etc.,but still no joy.  "File not found" for everything after that.

Start Up Manager made an easy floppy for grub in 9.04, but this new grub2  doesn't create a similar floppy.

---

### Post by agrimstad on 2009-11-24
> **oldtraveler said:**
> I have tried both #18 and #19 above.  grub> ls shows several partitions on both disks such as hd1,5 etc.,but still no joy.  "File not found" for everything after that.

Are you saying that:

grub> ls (hd1,5)/
grub> ls (hd1,5)/boot/grub
etc.

show nothing? Beats me.

> Start Up Manager made an easy floppy for grub in 9.04, but this new grub2  doesn't create a similar floppy.

Well, of course, grub2 is rather unfinished at this point. All this agony isn't exactly surprising.

---

### Post by agrimstad on 2009-11-25
> **oldtraveler said:**
> I have tried both #18 and #19 above.  grub> ls shows several partitions on both disks such as hd1,5 etc.,but still no joy.  "File not found" for everything after that.


After some thought, it occurred to me that one should start from first principles when nothing seems to work, except grub> ls

Since ls works, grub2 is seeing your hard drives.

What I would do is use grub to explore them and try to find the grub directory. Drop the assumption that we're dealing with hdb5. I mean do something like this:

grub> ls
(hd0,1) (hd0,2) ... (hd1,1) (hd1,2) ...

grub> ls (hdx,y)/
grub> ls (hdx,y)/boot
grub> ls (hdx,y)/boot/grub

for all x and y. I would expect a lot of errors, since this is a shotgun approach. But, if you really do have ubuntu with grub installed on it on one of the hard drives that grub sees, you should hit on it.

Good luck.

---

### Post by oldtraveler on 2009-11-25
Following your instructions for:

grub> ls (hdx,y)/
grub> ls (hdx,y)/boot
grub> ls (hdx,y)/boot/grub

and using (hd1,5)

your first command gives "lost + found/ var/ etc/ media/  and so on".

your second command gives "grub/ System.map-2.6.31-14-generic and so on".

your third command gives "device.map 915 resolution.mod and so on".

Since command #2 shows my Ubuntu OS, my inexperienced eye says to me that grub has found the OS, but has not yet been given the correct command to boot it.

---

### Post by drs305 on 2009-11-25
> **oldtraveler said:**
> Following your instructions for:

grub> ls (hdx,y)/
grub> ls (hdx,y)/boot
grub> ls (hdx,y)/boot/grub

and using (hd1,5)

your first command gives "lost + found/ var/ etc/ media/  and so on".

your second command gives "grub/ System.map-2.6.31-14-generic and so on".

your third command gives "device.map 915 resolution.mod and so on".

Since command #2 shows my Ubuntu OS, my inexperienced eye says to me that grub has found the OS, but has not yet been given the correct command to boot it.


Specifically, does command 1 show /boot (it apparently does)
Does command 2 show vmlinuz.... and initrd.img...  i.e. it has files vmlinuz... and initrd.img... and the folder grub?
Does command 3 show grub.cfg

---

### Post by oldtraveler on 2009-11-25
> **drs305 said:**
> Specifically, does command 1 show /boot (it apparently does) [color=red] YES - among other things[/color]

Does command 2 show vmlinuz.... and initrd.img...  i.e. it has files vmlinuz... and initrd.img... and the folder grub?[color=red] YES - among other things[/color]

Does command 3 show grub.cfg [color=red] YES - among other things[/color]
All are there.

---

### Post by agrimstad on 2009-11-25
> **oldtraveler said:**
> Following your instructions for:

grub> ls (hdx,y)/
grub> ls (hdx,y)/boot
grub> ls (hdx,y)/boot/grub

and using (hd1,5)

your first command gives "lost + found/ var/ etc/ media/  and so on".

your second command gives "grub/ System.map-2.6.31-14-generic and so on".

your third command gives "device.map 915 resolution.mod and so on".

Since command #2 shows my Ubuntu OS, my inexperienced eye says to me that grub has found the OS, but has not yet been given the correct command to boot it.

OK, the penny finally dropped for me. Your first partition is a logical partition and grub is treating it as #5 rather than #1.

So, the magic sequence is almost certainly--famous last words--:

grub> insmod (hd1,5)/boot/grub/linux.mod
grub> linux (hd1,5) /boot/vmlinuz... root=/dev/hdb5
grub> initrd (hd1,5) /boot/initrd ... 
grub> boot

I expect that even this would work:

grub> set root=(hd1,5)
grub> insmod /boot/grub/linux.mod
grub> linux /boot/vmlinuz-2.6.31-14-generic root=/dev/hdb5
grub> initrd /boot/initrd.img-2.6.31-14-generic
grub> boot

Of course, the kernel and initrd numbers have to be the ones you discovered on your system.

---

### Post by oldtraveler on 2009-11-25
> **agrimstad said:**
> OK, the penny finally dropped for me. Your first partition is a logical partition and grub is treating it as #5 rather than #1.

So, the magic sequence is almost certainly--famous last words--:

grub> insmod (hd1,5)/boot/grub/linux.mod [color=red]OK[/color]
grub> linux (hd1,5) /boot/vmlinuz-2.6.31-14-generic root=/dev/hdb5 [color=red]This produces "invalid file name"[/color]
grub> initrd (hd1,5) /boot/initrd ... 
grub> boot

I expect that even this would work:

grub> set root=(hd1,5)
grub> insmod /boot/grub/linux.mod
grub> linux /boot/vmlinuz-2.6.31-14-generic root=/dev/hdb5
grub> initrd /boot/initrd.img-2.6.31-14-generic
grub> boot [color=red]see below for what this produces[/color]

Of course, the kernel and initrd numbers have to be the ones you discovered on your system.
I stopped sequence #1 above when I received the "invalid file name".  

Sequence #2 worked fine and after grub> boot the screen went crazy and got to 
Done.
Begin: Waiting for root file system

     then
Busy Box v 1.13.3  (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)

Enter 'help' for a list of built in commands

(initramfs)

I entered help and got a hundred commands - none of which said boot

---

### Post by drs305 on 2009-11-25
There are times when you need to run something, such as ls, with the the device, but in those cases do not leave a space between the (hd1,5) and the remainder. A command would be typed as:
```

ls (hd1,5)/boot

```
The first list didn't run because the (hd1,5) isn't necessary in the lines, but also the space would have generated the error regardless in this instance.

In the second sequence, check that it is "sdb5" in the linux line.
```

set root=(hd1,5)
insmod /boot/grub/linux.mod 
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/**s**db5 ro
initrd /boot/initrd-2.6.31-14-generic 
boot

```

---

### Post by oldtraveler on 2009-11-26
Joy!


Thanks to agrimstad and to drs305 here is what finally booted to Ubuntu from the floppy:

grub> set root=(hd1,5)
grub> insmod /boot/grub/linux.mod
grub> linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb5
grub> initrd /boot/initrd.img-2.6.31-14-generic
grub> boot

You guys are awesome with your knowledge and to take the time to stick with this.

---

### Post by oldtraveler on 2009-11-26
I'm almost afraid to ask, but if you feel up to it what are the chances of finding the code needed to boot from grub> to my Windows XP OS which is on (hd0,2) i.e. dev/sda2 which is an ntfs partition?

On grub2 bootup it is shown as:

Windows NT/2000/XP (loader)  (on /devsda2)

---

### Post by drs305 on 2009-11-26
> **oldtraveler said:**
> I'm almost afraid to ask, but if you feel up to it what are the chances of finding the code needed to boot from grub> to my Windows XP OS which is on (hd0,2) i.e. dev/sda2 which is an ntfs partition?

On grub2 bootup it is shown as:

Windows NT/2000/XP (loader)  (on /devsda2)

Glad you were able to boot. As far as Windows, does running "sudo update-grub" not find and add Windows to the menu? It should be done automatically. If it isn't found by update-grub, you can make an entry in /etc/default/40_custom.

The normal commands in a Grub 2 menuentry would be the following. Replace the X's with the UUID of sda2. You can get the UUID by running "sudo blkid | grep sda2". Insert just the alphanumeric characters in the UUID section. 

If you plan on typing this in the Grub command line, you don't have to enter the "search" line - just everything between the { }s:
> 
*menuentry "Windows XP" {*
insmod ntfs
set root=(hd0,2)
*search --no-floppy --fs-uuid --set XXXXXX-XXX-XXXX*
chainloader +1
*}*


If you manually add this entry to /etc/grub.d/40_custom, run "sudo update-grub" to get it into the grub.cfg menu.

If XP won't load, you may need to use the XP CD to help restore Windows. Here is the link:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by agrimstad on 2009-12-03
> **oldtraveler said:**
> I'm almost afraid to ask, but if you feel up to it what are the chances of finding the code needed to boot from grub> to my Windows XP OS which is on (hd0,2) i.e. dev/sda2 which is an ntfs partition?

On grub2 bootup it is shown as:

Windows NT/2000/XP (loader)  (on /devsda2)

I took my grub2 boot floppy over to a windows xp computer and booted windows as follows:

```
sh:grub> set root=(hd0,1)
sh:grub> chainloader +1
sh:grub> boot
```

This probably won't work for you, but it's close. The issue is getting the root= line correct and you may have to experiment. Perhaps you'll need to set root to (hd0,2).

By the way, I also booted windows with an older grub1 boot floppy thusly:

```
grub> root=(hd0)
grub> chainloader +1
grub> boot
```

Good luck.

---

### Post by oldtraveler on 2009-12-03
Yes.  That works perfectly - using in my case (hd0,2)  

Thank you.

---

### Post by Browser_ice on 2010-03-05
Isn't there a way not to have to type the commands at the grub2 prompt ?

I did :
grub-mkrescue --overlay=/boot/grub --image-type=floppy GRUB2.img
dd if=GRUB2.img of=/dev/fd0

but when I boot with the floppy, it just brings me into the Grub2 prompt. I don't want to have to type in commands everytime.

---

### Post by JustZisGuy on 2010-05-30
The commands to create a Grub 2 Ubuntu recovery disk / boot floppy are all different in Ubuntu 10.04. I also tried the start up manager and that failed to create a rescue floppy.

After some messing around and searching, this set of commands creates a bootable floppy disk with the current grub boot configuration for 10.04 - which in my case included the boot menu with all of my partitions. 

```

mkdir /tmp/fdroot
mkdir /tmp/fdroot/boot
mkdir /tmp/fdroot/boot/grub
cp /boot/grub/grub.cfg /tmp/fdroot/boot/grub
cd /tmp
grub-mkrescue --output=grub2.img fdroot
sudo dd if=grub2.img of=/dev/fd0

```

The disk this creates does not use a standard file system so it is not possible, as far as I can tell, to edit the boot configuration directly on the disk from another computer.

---

### Post by RachelWoulf on 2010-08-20
Many thanks JustZ 10/4 :)

---

### Post by formerlypoliticalusername on 2010-09-09
hi everyone:sorry because my poor english.I heve installed LinusMint9 and STARTUP-MANAGER allways says Error.Then I installed by Synaptic grub-rescue-pc
###################################################################
GRUB bootable rescue images, version 2 (PC/BIOS version)

This package contains two GRUB rescue images that have been built for use with
traditional PC/BIOS architecture:

 - grub-rescue-floppy.img: floppy image.
 - grub-rescue-cdrom.iso: El Torito CDROM image
###################################################################
then typed in terminal:
  fdformat /dev/fd0
  mkfs -t msdos /dev/fd0
  dd if=/usr/lib/grub-rescue/grub-rescue-floppy.img of=/dev/fd0

then sudo reboot y it worked fine.

---

### Post by drs305 on 2010-09-09
> **aznarwarcriminal said:**
> hi everyone:sorry because my poor english.I heve installed LinusMint9 and STARTUP-MANAGER allways says Error.Then I installed by Synaptic grub-rescue-pc
###################################################################
GRUB bootable rescue images, version 2 (PC/BIOS version)

This package contains two GRUB rescue images that have been built for use with
traditional PC/BIOS architecture:

 - grub-rescue-floppy.img: floppy image.
 - grub-rescue-cdrom.iso: El Torito CDROM image
###################################################################
then typed in terminal:
  fdformat /dev/fd0
  mkfs -t msdos /dev/fd0
  dd if=/usr/lib/grub-rescue/grub-rescue-floppy.img of=/dev/fd0

then sudo reboot y it worked fine.

Thank you for mentioning this *aznarwarcriminal*. There is a lot of Grub2 troubleshooting here on the forums and I think we sometimes forget about this recovery option.

---

### Post by curtis_mccauley on 2011-02-08
drs305: Please help here, if you can.

I have the same problem as Browser_ice, but in my case the the problem is more or less fatal, as I explain below: 

> **Browser_ice said:**
> Isn't there a way not to have to type the commands at the grub2 prompt ?

I did :
grub-mkrescue --overlay=/boot/grub --image-type=floppy GRUB2.img
dd if=GRUB2.img of=/dev/fd0

but when I boot with the floppy, it just brings me into the Grub2 prompt. I don't want to have to type in commands every time.

I cannot type in commands at boot time. I have a headless system. No keyboard. No mouse. No monitor. Just an ethernet connection to the LAN and from there to the Internet. I communicate with this system using RDC for Windows and VNC for Ubuntu, if I need a graphical interface. Otherwise, there is SSH.

Back in the day, we had this great tool called GRUB (now called "GRUB Legacy"). It was comparatively easy to understand and to configure. Just one file, MENU.LST. I could edit it with any text editor. If I wanted, I could create a specific floppy to boot any OS installed on my computer. For example, I could create one floppy that booted my Windows partition by default and another floppy that booted my Ubuntu installation by default. All I had to do was to put the right floppy in the drive. I could even leave the Windows boot loader on my hard drive if I preferred it over GRUB.

Now, with GRUB2, at least in terms of ease of use and configuration, we have taken a great step backward.

My main problem is this: I see no way to create a boot floppy that boots just one OS.

I can, thanks to the package grub-rescue-pc, create a boot floppy disk that will bring up a menu of a variety of operating systems that may or may not be installed in my machine, and for each a generic script to boot that OS. I can pick one with my keyboard from the list on the screen, and hope that the generic script works....

Or at least I could pick one with my keyboard if I had a keyboard attached and a monitor to see what I was choosing.

This is progress?

To be fair, the rescue floppy does sort of work. The rescue floppy has a timeout for user input of about 30 seconds or so. When that time expires, it then starts trying to boot various operating systems that might be installed, until it finds one that boots.

You would think that it would try a linux boot first, given that the rescue disk image is part of Ubuntu, and thus it is more or less likely that Ubuntu is installed somewhere on the host computer.

But, no, the first OS that the GRUB2 rescue disk tries to boot is, of all things, GNU Hurd.

What were they thinking?

Heaven forbid that someone had installed both GNU Hurd and Ubuntu, but for some reason got the GNU Hurd installation screwed up and totally broken. Then, the "rescue" disk would have essentially dumped them on a deserted island.

As it turns out, Linux comes pretty early in the list of OSes that the "rescue" disk tries to boot, either second or third, I think. So getting stranded is not as likely as it might have been otherwise.

Lucky for me, the "rescue" disk does manage to boot my Ubuntu installation, after the delays mentioned above.

Here is my plea, to anyone out there: Do you understand GRUB2 well enough to make a GRUB2 floppy disk that will directly boot (i.e., no trial and error) either (a) my Ubuntu installation or (b) my Windows installation?

If so, please share your knowledge.

Thanks.

---

### Post by drs305 on 2011-02-08
curtis_mccauley,

Welcome to the Ubuntu forums. 

Much of what I know about Grub2 I've learned from experimentation. Unfortunately I have no floppy drives so your project is not something I can play with.

However, since you seem to be able to create a bootable floppy and only have problems with the way the menu is presented, it seems that there should be a solution.

The way I would approach this is to create a folder with all the Grub files you need *and alter the grub.cfg file within the folder/subfolders* to suit your desires. If grub-mkconfig builds the image according to the files within the build folder hopefully it would also incorporate the grub.cfg contents located therein.

The Grub2 manual discusses how to use an "iso" folder content (as an example) to build the image file. I'd refer to that method and see if it applies to your case.  The linked section (3.2) discusses a bootable CD, but I would suspect you can modify the command to apply to the floppy as well. You might also take a look at the previous section (3.1), which discusses creating a floppy.

[http://www.gnu.org/software/grub/manual/grub.html#Making-a-GRUB-bootable-CD_002dROM]("http://www.gnu.org/software/grub/manual/grub.html#Making-a-GRUB-bootable-CD_002dROM")

---

### Post by curtis_mccauley on 2011-02-08
> **drs305 said:**
> curtis_mccauley,

Welcome to the Ubuntu forums. 

Much of what I know about Grub2 I've learned from experimentation. Unfortunately I have no floppy drives so your project is not something I can play with.

However, since you seem to be able to create a bootable floppy and only have problems with the way the menu is presented, it seems that there should be a solution.

The way I would approach this is to create a folder with all the Grub files you need *and alter the grub.cfg file within the folder/subfolders* to suit your desires. If grub-mkconfig builds the image according to the files within the build folder hopefully it would also incorporate the grub.cfg contents located therein.

The Grub2 manual discusses how to use an "iso" folder content (as an example) to build the image file. I'd refer to that method and see if it applies to your case.  The linked section (3.2) discusses a bootable CD, but I would suspect you can modify the command to apply to the floppy as well. You might also take a look at the previous section (3.1), which discusses creating a floppy.

[http://www.gnu.org/software/grub/manual/grub.html#Making-a-GRUB-bootable-CD_002dROM]("http://www.gnu.org/software/grub/manual/grub.html#Making-a-GRUB-bootable-CD_002dROM")
Thanks for the prompt response. I will take a look at creating a bootable CD. If I manage to get it to work, I will post back here.

---

### Post by curtis_mccauley on 2011-02-19
> **curtis_mccauley said:**
> Thanks for the prompt response. I will take a look at creating a bootable CD. If I manage to get it to work, I will post back here.

Not sure whether anyone else has any use for this, but I did find a way to make a custom boot floppy under Ubuntu Server 10.10 amd64. (The technique I used could also be used to make a custom bootable GRUB2 CD.)

I was initially trying to work with Ubuntu Desktop 10.10 amd64, but had to give that up. As I said in my prior message, this system runs headless: i.e., no keyboard, no monitor. I was initially frustrated over networking issues, until I discovered that Ubuntu Desktop does not enable the ethernet ports until AFTER a user has logged into the system. That kills Desktop for any headless configuration. I am sure somebody has a good reason why that should be, but I am at a loss. Does nobody remotely connect to their workstations through VNC (on Ubuntu) or RDC (on Windows)?

So, I switched to working with the Server 10.10 amd64 distribution. SSH access is all I need, really.

Here is what I did to create a custom GRUB2 boot floppy:

I started with the rescue floppy image installed by the package grub-rescue-pc. The floppy image is at: /usr/lib/grub-rescue/grub-rescue-floppy.img.

Embedded in grub-rescue-floppy.img is a generic grub.cfg. What I did was to find where the contents of grub.cfg  were stored within the image. I replaced it with my own custom grub.cfg, padded as necessary to match the size of the grub.cfg I was replacing. My own grub.cfg had only the entries that reflected the operating systems on my computer. (The original had "generic" entries for a bunch of OSes, starting with GNU Hurd at the top.) Then I wrote grub-rescue-floppy.img, as modified, to a floppy using dd, and presto, I had a custom boot floppy.

The time consuming part of this was finding the exact byte range within grub-rescue-floppy.img that contained grub.cfg. It starts at byte offset 79872, with a length of 1635 bytes.

You can display it with the following command:

dd if=/usr/lib/grub-rescue/grub-rescue-floppy.img skip=79872 count=1635 bs=1

A little arithmetic gives the size of each piece:

(1) Offset 0		Length   79872
(2) Offset 79872    Length    1635
(3) Offset 81507    Length 1362333

I padded my custom grub.cfg file with whitespace or comments, so as to have a length of 1635 bytes. Using dd, I created the individual parts:

dd if=/usr/lib/grub-rescue/grub-rescue-floppy.img count=79872 bs=1 of=grf_p1.dat
dd if=/usr/lib/grub-rescue/grub-rescue-floppy.img skip=79872 count=1635 bs=1 of=grf_p2.dat
dd if=/usr/lib/grub-rescue/grub-rescue-floppy.img skip=81507 count=1362333 bs=1 of=grf_p3.dat

Then, I cat'ed the first piece, the custom grub.cfg file, and the third piece, to make a complete image file, burned that image to a floppy, and all is good.

I made one floppy with a grub.cfg to boot windows and another floppy with a grub.cfg to boot linux.

Now I can boot my headless workstation to either Ubuntu or Windows, as necessary, and access it remotely.

To be sure, this is a kludge. But, when distros decide to take away functionality, simply because they think no user should need that functionality any more, those of us who still need it have to find a way around.

I would urge the folks working on Ubuntu not to eliminate functionality just because older hardware is uncool, or whatever. I thought that part of Ubuntu's mission was to make computers available to a wider audience. Some people, like me, still have a use for floppies and other legacy hardware.

---

