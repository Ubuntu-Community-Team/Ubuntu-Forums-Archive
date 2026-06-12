---
title: "[SOLVED] dual boot help needed!"
date: 2008-07-18
forum: General Help
---

### Post by rohee on 2008-07-18
I am brand new to Ubuntu and I need some help! I installed Ubuntu onto a win xp pro machine.  I manually configured partitians, etc. and at the boot loader selection I chose win xp professional as the choice.  Ubuntu installed fine, I rebooted and the boot menu comes up.  the choices are ubuntu, etc. the last choice to arrow down to is window xp professional.  when i highlight that and hit enter if flips quickly to 'starting up grub loader stage 2' and quickly goes back to initial boot menu.  I cannot get it to boot into xp.  can someone give me specific instructions on how I can correct this.  thanks very much.  Please email me at <snip> with details on what to do.  Thanks again.

---

### Post by cdtech on 2008-07-18
Are you running one hard drive for both?

Can you post your /boot/grub/menu.lst ? You just may need to set the drive correctly such as the way I have mine.

```
title		Windows Vista
root		(hd1,0)
savedefault
chainloader	+1
```

Mine is set for the second drive.

---

### Post by rohee on 2008-07-18
I have two hard drives on my pc.  On the drive that xp is on (C) i had a second partition and that is where I loaded ubuntu. My second hard drive is simply a data storage drive for pics, documents, etc.

---

### Post by rohee on 2008-07-18
Can you give me the steps to post my /boot/grub/menu.lst

---

### Post by falcon61102 on 2008-07-18
Open up your terminal by going to Applications>Accessories>Terminal.  Then type:
```
sudo gedit /boot/grub/menu.lst
```

When prompted, enter your user password.  This will then open up a text editor and display menu.lst.  You can copy that directly to here.

---

### Post by rohee on 2008-07-18
Thanks Falcon, I am at where I type my password but when i type password in blinking cursor just sits blinking and does not enter password.  Any idea what is going on here.  I hate to be a pain on this.

---

### Post by cdtech on 2008-07-18
It wont show you typing the password but it will open up a text editor as super user.

---

### Post by falcon61102 on 2008-07-18
Your password is being typed, it just doesn't display anything for security reasons.  Type your password and press enter.  And it's no problem.

---

### Post by rohee on 2008-07-18
I can't get it to do anything further. When I hit enter it says 'sorry try again'.  dark blinking cursor.  Cursor does not move as i type in password.

---

### Post by falcon61102 on 2008-07-18
The cursor won't move.  Type that line of code in.  Hit Enter.  Type your password. Hit Enter.  That should open the text editor.

---

### Post by rohee on 2008-07-18
ok, i got it to go.  let me try to make the change suggested and see what happens.

thks

---

### Post by falcon61102 on 2008-07-18
Also, once you get the menu.lst file copied, go back to your terminal and type:
```
sudo fdisk -l
```
And post the results.  Note that "-l" is a dash and lower case L.  That command will list all of the partitions on your computer.

Based on the information from that and the copy of your menu.lst, we should be able to show you what to change to get XP running again.

---

### Post by rohee on 2008-07-18
Here is what I have changed. I restarted and while Win xp is now at the top, the Ubuntu choice is what highlight still defaults to. when I arrow up to xp and hit enter it will not boot into xp but go back to boot menu with ubuntu choice highlighted.

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic
root=UUID=743ba17f-4169-4696-a989-23edc3d29dfb ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic
root=UUID=743ba17f-4169-4696-a989-23edc3d29dfb ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet


any suggestions on how i can get it to boot into xp?

---

### Post by rohee on 2008-07-18
Here is some more info u requested.

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x00600060

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10211    82019826    7  HPFS/NTFS
/dev/sda2           10212       14436    33937312+  83  Linux
/dev/sda3           14437       14946     4096575   82  Linux swap /
Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x6921fbc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14357   115322571    7  HPFS/NTFS
/dev/sdb2           14358       19457    40965750    f  W95 Ext'd (LBA)
/dev/sdb5           14358       19457    40965718+   7  HPFS/NTFS
mike@mike-desktop:~$

---

### Post by falcon61102 on 2008-07-18
Post the output of:
```
sudo fdisk -l
```

This will allow us to see the order of your HD partitions which is what the GRUB uses to load them.  The GRUB may be skipping your XP partition because it knows it cannot load it, once you fix your menu.lst, it should default to loading XP.

OK... disregard this... it was slow in updating forum...

---

### Post by falcon61102 on 2008-07-18
It appears that you menu.lst is correct.  What may have happened when you trying the different installs, you may have overwritten your windows boot loader.  When you select the windows partition, can you see any text or errors that flash on the screen before it returns to the GRUB?

---

### Post by rohee on 2008-07-18
Yes, when i choose xp to boot i get a flash that says: starting up grub loading stage2 and then it flashes back to initial boot menu

---

### Post by rohee on 2008-07-18
Falcon, I really appreciate you taking your  time in helping me get this straightened out.

---

### Post by cdtech on 2008-07-18
It does look like the grub list is ok. I personally would fix the MBR in windows and reinstall grub. It does look as though the MBR was overwritten.

---

### Post by falcon61102 on 2008-07-18
Ok... I'm still thinking that you had overwritten the windows boot segment when trying previous installs.  It's fixable.  The easiest way I can think of would be to fix your Windows loader and then, if necessary, reload the GRUB.  Let me explain the steps and it will sound clearer.

Boot from a Windows XP disk and go through the recovery menu to restore the MBR.  That should do it.

Restart your computer and let it boot from the HD.

If it boots directly to WinXP then all you need to do is reinstall the GRUB.  If it boots to the GRUB, test both the XP and Ubuntu links to make sure they work and edit the menu.lst if necessary.

To reinstall the GRUB, boot from your liveCD and then open up a terminal.

Type:
```
sudo grub
```

That will load the grub program.  Then type:

```
find /boot/grub/stage1
```
That should give you an output such as (hd0,1)  Use that output in the next two lines.

```
root (hd0,1)
```
Then
```
setup (hd0,1)
```

That should reinstall your GRUB so that when you boot up it goes right to the GRUB.

And no problem, I just hope this helps.

---

### Post by falcon61102 on 2008-07-18
cdtech, you see anything I'm missing or a quicker/easier way to do that?

---

### Post by cdtech on 2008-07-18
I can't see anything out of the ordinary. It's not hard to fix the MBR of your windows OS, just use the install disk. Once you have that fixed check to see if it boots right into windows, then we can repair the grub boot loader.

---

### Post by falcon61102 on 2008-07-18
Yeah, it's pretty straight forward.  I just didn't know if there was a shorter way.

---

### Post by rohee on 2008-07-18
I repaired MBR from windows cd and the same problem still continues. I cannot boot into xp.  Any other suggestions?

---

### Post by cdtech on 2008-07-18
That should have re installed the MBR for windows and seeing as how your primary drive is the only one with a boot sector that should have let you back into windows.

give me a sec.........

---

### Post by falcon61102 on 2008-07-18
Exactly what happens when you start up your computer now?

Does it go to the GRUB?

---

### Post by rohee on 2008-07-18
Yes, it goes into Grub and the xp choice is at the top, unbuntu next, etc.  Xp is highlighted, I hit enter and I get quick flash which says 'starting up
            Grub loading stage2'
and then flashes back to my grub menu with xp choice highlighted.

---

### Post by cdtech on 2008-07-18
Good point falcon. All he should have now is a bootable windows drive with a partition with a non bootable Ubuntu OS.

---

### Post by cdtech on 2008-07-18
> **rohee said:**
> Yes, it goes into Grub and the xp choice is at the top, unbuntu next, etc.  Xp is highlighted, I hit enter and I get quick flash which says 'starting up
            Grub loading stage2'
and then flashes back to my grub menu with xp choice highlighted.

The MBR was not repaired from what you just said. hmmmm....

---

### Post by rohee on 2008-07-18
If I highlight ubuntu and hit enter it goes right into ubuntu with no problems.

---

### Post by falcon61102 on 2008-07-18
Ok, you just need to reinstall your grub now.

Boot from your live cd and follow the code that I posted earlier and it should reinstall your GRUB which got partially overwritten when you installed the windows MBR.

---

### Post by rohee on 2008-07-18
windows told me the mbr was repaired when I went thru the process. Should i do that again and see what happens?

---

### Post by falcon61102 on 2008-07-18
I think the Windows MBR fix did work.  

I think the problem was that he had two or three installs of the GRUB in different places, one of them being the MBR.  Now that he has overwritten that one, he needs to point the good GRUB install towards the Windows boot loader.  By reinstalling the GRUB, it should automatically do that for him, if not he will have to edit the menu.lst.  I hope that makes sense.

---

### Post by rohee on 2008-07-18
ok, i will reinstall grub and get back shortly with results. thanks

---

### Post by cdtech on 2008-07-18
I think falcon is right on this one...

---

### Post by falcon61102 on 2008-07-18
Just make sure when you run the:
```
find /boot/grub/stage1
```
Use the output of that in the next line even if it doesn't match what I wrote in the code.

---

### Post by falcon61102 on 2008-07-18
Unfortunately when I first started messing with Ubuntu, I went through something similar.  

At times a set up like this can be beneficial.  For instance:  I have my laptop which is a dual boot Vista/Ubuntu and then I have an external HD with Ubuntu on it.  

My GRUB on my laptop lists all three installs.  I have a second GRUB on the External HD so that I can plug it in to any computer and boot from that drive and load Ubuntu.  When its plugged into my laptop, I boot straight to my hard drive and it bypasses the GRUB on the external.  

It was a pain to setup and get working right, but it's great because now I have an install of Ubuntu I can take anywhere but when I plug it into my computer, I don't have to do anything special to load it.

---

### Post by rohee on 2008-07-18
well, i successfully installed grub (it told me i succeeded) but exactly the same problem continues. xp will not boot. same flash, same message, etc.   I am requesting a papal blessing on my computer.....    anything else to do?  or check?  or redo?

---

### Post by rohee on 2008-07-18
when i changed the menu lst earlier, and moved xp to the top, is there any special way to save the changes?  I simply went to file tab and hit 'save' which i assume was the way to do it.

---

### Post by falcon61102 on 2008-07-18
Post your menu.lst again, lets see if anything changed.  Also, if it wouldn't be too much of a hassel, reinstall the GRUB and post the output of each line that you went through.  Sometimes it says it was successful but it didn't go where you wanted it to.

---

### Post by falcon61102 on 2008-07-18
That's the way to save it... as long as you opened it as a super user (using sudo command) it will save, otherwise it will give you an error.

---

### Post by rohee on 2008-07-18
question:  i just looked at the sudo menu lst. and the xp option is now at the top. where is says   root    (hd0,0) is there.  Should it be (hd0,1) ?  That is what showed up when I redid the GRUB.  all the other choices on the menu have (hd0,1)

---

### Post by falcon61102 on 2008-07-18
No, the ones that show up in the GRUB is for your Ubuntu partition.  If XP is your first partition on the drive, then it is correct.  To check this type:
```
sudo fdisk -l
```
if /dev/sda1 is NTFS then it is most likely your XP partition.  Post it up here and I'll let you know.

---

### Post by rohee on 2008-07-18
here it is;

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x00600060

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10211    82019826    7  HPFS/NTFS
/dev/sda2           10212       14436    33937312+  83  Linux
/dev/sda3           14437       14946     4096575   82  Linux swap /
Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x6921fbc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14357   115322571    7  HPFS/NTFS
/dev/sdb2           14358       19457    40965750    f  W95 Ext'd (LBA)
/dev/sdb5           14358       19457    40965718+   7  HPFS/NTFS
mike@mike-desktop:~$

---

### Post by falcon61102 on 2008-07-18
The menu.lst is correct in listing it as (hd0,0).  Grub starts counting with 0 so (hd0,0) translates to first hard disk, first partition.

Have you tried installing GRUB?  If you can, post the output of the install here.  It may not be completely installing right.

---

### Post by rohee on 2008-07-18
will redo and post , be right back

---

### Post by rohee on 2008-07-18
here it is,

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,1)

grub> root (hd0,1)

grub> setup (hd0,1)
 Checking if "/boot/grub/stage1" exists... yes  Checking if "/boot/grub/stage2" exists... yes  Checking if "/boot/grub/e2fs_stage1_5" exists... yes  Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not
fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not
fatal)
 Running "install /boot/grub/stage1 (hd0,1) /boot/grub/stage2 p /boot/grub/menu .lst "... succeeded Done.

grub>

---

### Post by falcon61102 on 2008-07-18
Ok, do it again except use:
```
setup (hd0)
```
as the last step.  You shouldn't see any lines that failed then.

---

### Post by rohee on 2008-07-18
ok, i will post it when done.

---

### Post by rohee on 2008-07-18
here is what showed up,,,,

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,1)

grub> root (hd0,1)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes  Checking if "/boot/grub/stage2" exists... yes  Checking if "/boot/grub/e2fs_stage1_5" exists... yes  Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p
(hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub>

---

### Post by rohee on 2008-07-18
i will try to reboot from xp and see what happens

---

### Post by rohee on 2008-07-18
same problem continues, nothing changed

---

### Post by falcon61102 on 2008-07-18
The only thing I can think of is that the other installs you tried have corrupted your boot sector of Windows.  You have reinstalled both compents required for a succesful boot but something else is keeping it back.  It should have been an easy fix... lol.  

My recommendation is to use the Super Grub Disk.  It's a liveCD that you can boot from and it will help you get things fixed.  I've never used it so I don't the details but from what I've read around here, it works well.

Here's the link:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Let me know how that works out for you.  I'm interested in what's still holding it up from booting.

---

### Post by rohee on 2008-07-18
Can the super grub disk be downloaded and burned onto a cd or do u have to order it?

---

### Post by falcon61102 on 2008-07-18
You can download it for cd, floppy, or USB drive... links to download are in upper right hand corner of page.

---

### Post by cdtech on 2008-07-18
You can find it here::.
[[COLOR="DarkRed"]super grub[/COLOR]]("http://www.supergrubdisk.org/")

---

### Post by rohee on 2008-07-19
Hey,  Good morning,

I ended up burning my image back onto C drive and restored windows to where it was before I installed ubuntu.  Can you tell me where I can get specfic instructions on how to properly install ubuntu where I want to dual boot xp and ubuntu?

I have two hard drives.  Drive C has windows which is in separate partition. I have second partition on drive C now.  When I get to partition section of ubuntu should I use manual or guided?

A site with pictoral instructions on how to install would be great.

---

### Post by rraj.be on 2008-07-19
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

Hope this helps.

---

### Post by rohee on 2008-07-19
Thanks!

---

### Post by rraj.be on 2008-07-19
> **rohee said:**
> Thanks!

If you want to thank anyone you can click the medal icon at the bottom of the coprresponding post.

Further post further doubt's in new post's.Dont post all your doubts in a single thread.This will help the response to your question's.:)

Mark the thread as solved if your  problem is solved.

---

