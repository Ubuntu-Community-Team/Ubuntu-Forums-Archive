---
title: "Ubunta / Vista  Dual Boot"
date: 2008-09-20
forum: General Help
---

### Post by Jamtarts on 2008-09-20
It's my first post, sorry if it's in the wrong area?

I've been using ubuntu on my laptop for a while now, and very impressed.  I therefore decided to install it on my desktop to make a dual boot with vista using the second drive.

I then proceeded to boot up but neither would load at all.  Now I realise i should have checked this before i started but previous installs of Red Hat etc have always configured a boot manager.  I mistakenly assumed this would too.

Is there any way I can install a boot manager or similar to restore the 2 drives, or am i going to have to do a complete new install of both systems again 

thanks in advance and sorry if this should be in another thread

---

### Post by fooman on 2008-09-20
ubuntu should have installed the grub bootloader.  if you installed ubuntu onto the second disc....did you configure the bios to boot from the second disc?  maybe you just need to change the boot order in the bios?

if not that,  then grab your cd and give this a try:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Sef on 2008-09-20
How did you partition the hard drive?

---

### Post by Jamtarts on 2008-09-21
Thanks for the replies guys, sorry for the delay in getting back,

I'm just going to try the recovery tutorial just now,

My drives are 2 separate drives, vista is on a 500gb drive and i installed Ubuntu on a 250gb drive.  I'd selected automatic partioning (I think).

Ideally i want to use Ubuntu as my main OS and just use windows for games and some work stuff.  I do have a lot on the vista drive i don't want to lose, most of it is backed up if i have to reinstall it but i'd rather keep it if possible.

thanks again

---

### Post by Jamtarts on 2008-09-21
Just a thought, as it is a fresh Ubuntu Install on the drive, would reinstalling it again using different settings remedy the problem?

---

### Post by hellokitty1001 on 2008-09-21
[http://sikh.myminicity.com/tra](http://sikh.myminicity.com/tra)

---

### Post by Jamtarts on 2008-09-21
made a wee bit progress, i swapped drives over in the bios set up and Ubuntu loads no problem now, i get a menu of OS's but when i select Vista it still won't load, i'll just keep messing with it and see if i can get it to boot,

---

### Post by caljohnsmith on 2008-09-21
> **Jamtarts said:**
> made a wee bit progress, i swapped drives over in the bios set up and Ubuntu loads no problem now, i get a menu of OS's but when i select Vista it still won't load, i'll just keep messing with it and see if i can get it to boot,
Since you can boot into Ubuntu OK, how about posting:
```
sudo fdisk -lu
cat /boot/grub/menu.lst

```
Then we can help you boot Vista if you would like some help.

---

### Post by Sef on 2008-09-21
> sudo fdisk -lu


Please note that is a small L after the dash (-).

---

### Post by TeXtonyx on 2008-09-21
Jamtarts wrote: "Just a thought, as it is a fresh Ubuntu Install on the drive, would reinstalling it again using different settings remedy the problem?"

In XP one used to use the Recovery console to fixmbr which repairs the MBR.

[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)
This explains how in Vista, bootrec.exe is now used to repair the MBR, which will allow you to boot Vista.

[http://support.microsoft.com/kb/919529](http://support.microsoft.com/kb/919529) Explains the bootloader BCD 
Use Bootsect.exe to restore the Windows Vista MBR and the boot code that transfers control to the Windows Boot Manager program. To do this, type the following command at a command prompt: 
Drive:\boot\Bootsect.exe /NT60 All 
In this command, Drive is the drive where the Windows Vista installation media is located.

Tex: It is quite possible to reinstall grub to the MBR to the second hard 
drive which is likely labeled sdb or hdb, the first is labeled sda or hda.
But it will be easier for you to delete and then reinstall Ubuntu. 
During the install pay attention, there is a screen which appears after you have made your choice to install Ubuntu sdb your second hard drive.
This screen shows an Advanced button to click on. Click on it and select 
from the dropdown choices to install grub to your second hard drive, sdb,
which will put grub into the MBR of the second drive-- I think the problem
was that the default install if you click proceed rather than Advanced, is
that grub is installed into the MBR of Vista which means Vista can't boot 
up in a standalone fashion. This is important because you might decide to
remove Ubuntu which means your MBR in your first drive, if you installed
grub there to the MBR, is removed when you uninstall Ubuntu. That leaves
you unable to boot Vista until you restore its MBR again. So that is why
I think at this stage, you should make Vista standalone now, its own MBR.
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) This program is called EasyBCD, and it 
will let you add Ubuntu to the Vista boot loader menu. It is comforting
to know you can boot both OS from either OS. Suppose your XP drive dies
with the grub installed to its MBR. Now you have to take steps to fix it
so that Ubuntu will still boot. By installing grub separately to the 2nd
drive you can still boot it by swapping drives in Bios. I think that 
installing grub to first sector of the Ubuntu boot partition, an option 
also available under Advanced, is good in XP, but loses appeal in Vista.

Something to try is going into Bios and change the boot order of the two
drives. Usually the first drive is set to boot first. You can reverse the 
order in Bios so that the Second drive is set to boot first. You can try
that now, remember to change them back if this method doesn't help. Also 
try reversing the boot order of the drives if for some reason the method I
outlined in the above paragraph doesn't pan out. To enter Bios setup, tap
on key which is often mentioned during early bootup, perhaps Delete.

---

### Post by Jamtarts on 2008-10-01
Hi guys,
sorry for the delay getting back, i've had the flu and not been on pc.

just to let you know, i ended up installing Ubuntu on the main 500gb drive that windows is on, and i'm using the 250 gb drive as a spare drive, 

I reckon it was a windows problem but to be honest i can't really say i missed windows and decided i was having more fun with ubuntu,

so both my laptop and desktop are now fully windows free hehe,

thanks again for your help

Richard

---

