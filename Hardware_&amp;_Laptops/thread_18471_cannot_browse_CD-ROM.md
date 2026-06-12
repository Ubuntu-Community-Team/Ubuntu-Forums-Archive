---
title: "cannot browse CD-ROM"
date: 2005-03-07
forum: Hardware &amp; Laptops
---

### Post by Tubuntu on 2005-03-07
I cannot browse cd-drive, it just say cannot mount drive. 

If I insert audio cd then it start playing music, but I cannot look what files is in there. 

There is no CD-Drive icon on desktop when cd is inserted

I just changed cd-drive so could it be some linking problem? (Changed position in ide cable)
 Is there any command to check where cd-rom is (hdb,hdc.hdx)?

---

### Post by bored2k on 2005-03-07
[QUOTE=Tubuntu]I cannot browse cd-drive, it just say cannot mount drive. 

If I insert audio cd then it start playing music, but I cannot look what files is in there. 

There is no CD-Drive icon on desktop when cd is inserted

I just changed cd-drive so could it be some linking problem? (Changed position in ide cable)
 Is there any command to check where cd-rom is (hdb,hdc.hdx)?[/QUOTE]
 Mounted devices usually go to 
> /media/

So maybe its somewhere there, try > nautilus /media/cdrom0/

---

### Post by Tubuntu on 2005-03-07
nautilus /media/cdrom0/ 
Not working  :(   It shows only empty folder, no files. (show hided files option is on)

---

### Post by h88 on 2005-03-18
Sorry to bump an old message (relatively) but I have the exact same problem. I didn't try Audio CDs, but I cannot broswe any other CD through my USB external CD-ROM (bear in mind that I installed ubuntu using it)

Thanks in advance!

[font=1]Did you manage to solve it, Tubuntu[/font]

---

### Post by Tubuntu on 2005-03-18
[QUOTE=h88]Sorry to bump an old message (relatively) but I have the exact same problem. I didn't try Audio CDs, but I cannot broswe any other CD through my USB external CD-ROM (bear in mind that I installed ubuntu using it)

Thanks in advance!

[font=1]Did you manage to solve it, Tubuntu[/font][/QUOTE]

When I was playing with IDE cables it changed  mountpoints, so that was my own mistake. 

Have you connected other usb devices?

Have you check where is your usb cd-rom located? Is it same mounting place what is in the fstab? 
Have you upgraded to hoary? then it changes it usb mounting places..
 (yes, I had also that problem..But hey, its good for learning to have problems ;) )

Hope some genius could could help you h88...

---

### Post by BriLarks on 2007-04-21
Hi, 
[LEFT]  I seem to be having the same problem as you guys. I have an internal cdrom drive in a DELL XPS M1710 and I'm using Ubuntu 6.10- the Edgy Eft.. I can play and rip cds using Rythombox and KAudioCreator but I can't view any files on the CDrom. When I try I get the following error message 

"cdda:///dev/scd0" is not a valid location."

Some of the things I've unsuccessfully tried to do to solve it are.

I've set the privileges on /dev/scd0 to 777

I did find another [vaguely related posting]("http://ubuntuforums.org/showthread.php?t=283131") in the forums and as sudo I managed to mount and umount the cdrom.[/LEFT]

[INDENT]mount /media/cdrom0
mount: block device /dev/cdrom is write-protected, mounting read-only
umount /media/cdrom0[/INDENT]

Which does allow me to see the data on the disc and play the Mov file. But because it is mounted I have to un-mount it to remove the disc. Also having to bring up the command line every time I want to see the data on a cdrom is a bit irritating. There has to be a better way. 

My fstab has the following line in it for the cdrom.

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

So if you could let me know how what progress you've made with this that would be ace.

Cheers,

BriLarks

---

### Post by LiamTreacy on 2007-08-19
I'm bumping this thread because I have the same problem with Xubuntu 7.04 on a Dell Optiplex GX260. I can use the CD-ROM drive in all the usual ways but double clicking on the desktop icon of an AUDIO CD brings up the "cannot mount" message.

---

### Post by lofftjm on 2007-09-21
I have the same problem too...

---

