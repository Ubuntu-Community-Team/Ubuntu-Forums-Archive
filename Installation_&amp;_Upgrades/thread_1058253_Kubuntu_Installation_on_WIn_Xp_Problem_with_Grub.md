---
title: "Kubuntu Installation on WIn Xp Problem with Grub"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by Feidias on 2009-02-02
Dear Ubuntu friends,

I have installed Kubuntu 7.10 on an external drive disk, on a laptop using Windows XP. 

The problem is that I can't boot Windows XP without having the 
external disk plugged on the USB drive.

I have installed the Startupmanager and I have given priority to Windows but without the external disk connected, I can't boot my system.It says 

Grub Loading please wait... Error 21 

How can can I boot Windows XP when I don't have my external drive disk connected on my laptop?

Thank you.

---

### Post by dstew on 2009-02-02
You have installed the grub boot loader in the hard disk MBR (Master Boot Record) and configured it to look on the external drive for its stage2 and menu.lst files. You will have to put these files on the Windows hard disk (and re-install grub to look there) if you want to get a grub menu and boot Windows without the external disk attached.  Or, you could put grub on the external drive MBR only (and repair the hard disk MBR with the Windows recovery console). Then, you would need to make your BIOS boot the external drive when you wanted to use Kubuntu.

---

### Post by Feidias on 2009-03-19
Hello again! Thank you for your response!
Unfortunately I could not fix this issue and because I need to use my laptop I am a little bit worried to try.

How do I install GRUB on windows? On which directory? Is it going to be any problem if I have installed them both on external drive disk and laptop's disk? I mean, is there any possibility my laptop not starting? And actually..., Windows recovery console is the alternate of GRUB?

One more problem is that after I have installed Kubuntu I can t run BIOS. How does it run?

Thanks again

---

### Post by dandnsmith on 2009-03-19
If your laptop has just the one partition (apart from a recovery partition, possibly) and it is formatted as NTFS (highly likely, especially if you didn't do the install, then you have a problem - last time I looked, GRUB cannot boot using an NTFS partition, so copying the files or attempting to install GRUB won't work.

What you have to do, in this case, is to save the grub bootloader which is currently in the first partition of the HDD of the laptop, copy it to the Windows partition as an 'ordinary' file, restore the Windows bootloader, and then get the Windows bootloader to load linux

1) Copy the bootloader:
 dd bs=512 count=1 if=/dev/sda2 of=*ordinary_file*
make this copy where you can get to it from Windows later
2) Restore the Windows bootloader - for this you need access to the recovery console to run the command:
 fixmbr
3) from Windows (into which you should now be able to boot), you need to copy the saved grub bootloader to a file (say grubboot.lin)
and make an entry in boot.ini like:
 C:\grubboot.lin="Linux GRUB"
at the end, to get to the grub stuff on the external drive

I hope this helps - I know it can work, as I was restoring the PC on which I'm posting this 2 days ago.

---

### Post by Feidias on 2009-03-19
thank you for your instant reply.

I hope the laptop won't halt!

1) Actually, where is the GRUB bootloader file?Is it on the 1st HDD but on which place? How do I have access on that?You mean I must find it through Linux? In this case I have the problem that my laptop disks are unmounted and i can't read something on them. 
So is it Ok to place it ( if i finally find it...:) ) on a USB stick? 

2) If I am going to just run the fixmbr it will fix the bootloader?

3)You say "you need to copy the saved grub bootloader to a file (say grubboot.lin)
and make an entry in boot.ini like:
C:\grubboot.lin="Linux GRUB"
at the end, to get to the grub stuff on the external drive" 
a)you mean to change the name of the bootloader to grubboot.lin?
b)how can I make the entry in boot.ini-you mean to open the file and write this line "C:\grubboot.lin="Linux GRUB"" at the end?
Does this command means that it is going to Boot from the external drive?

thanks again

---

### Post by dandnsmith on 2009-03-19
> **Feidias said:**
> 
1) Actually, where is the GRUB bootloader file?Is it on the 1st HDD but on which place? How do I have access on that?You mean I must find it through Linux? In this case I have the problem that my laptop disks are unmounted and i can't read something on them. 
So is it Ok to place it ( if i finally find it...:) ) on a USB stick? 

The bootloader carries its own memory of where to boot from, as far as I can tell. Yours will, until you remove/overwrite it, be in the first block of the HDD (the one which was the boot device before you installed ubuntu), and it would be fine to put the file on a USB stick for transfer.
> 
2) If I am going to just run the fixmbr it will fix the bootloader?

Yes - it specifically overwrites the bootloader with a new XP bootloader.
> 
3)You say "you need to copy the saved grub bootloader to a file (say grubboot.lin)
and make an entry in boot.ini like:
C:\grubboot.lin="Linux GRUB"
at the end, to get to the grub stuff on the external drive" 
a)you mean to change the name of the bootloader to grubboot.lin?
b)how can I make the entry in boot.ini-you mean to open the file and write this line "C:\grubboot.lin="Linux GRUB"" at the end?
Does this command means that it is going to Boot from the external drive?

When you execute the dd command, the output, as I indicated, gets written to a simple file, the name of which is in the of=... parameter.
This block represents the bootloader and master partition table (amongst other things). The boot.ini file in the NTFS filesystem for your Windows is the one to modify with the added line (there is a fancy way under Windows (by going for Properties of My Computer under the Advanced Settings) , but you may have to use a text editor). It should boot to the external drive, as was intended.
Please DONT put this as the first block of the USB drive - it just wouldn't work, and would mess up any partition table you had there!

---

### Post by Feidias on 2009-03-20
Hello again.

Excuse me but I am new to Linux and I don't understan a lot of things...

I have a problem trying to copy the bootloader.

First of all on my laptop I have these partitions/disks:

sdb1 156G ( I have access on that)
sdc1 1G which isthe USB disk
sda1 which is named as Recovery Partition
sda5 named as VAIO (i don't have access to that)
sda2 named also as VAIO ( no access too)

On sdb1 I can find /boot/grub. 

So, you have proposed me to copy the bootloader with:

dd bs=512 count=1 if=dev/sda2 of=ordinary_file

Where does this command saves the bootloader?
And what gives the ordinary_file? I will find a file called
ordinary_file? Or should I give a filename, and if yes what extention should I give to this filename

Because of /boot/grub is on sdb1, should I run:

dd bs=512 count=1 if=/dev/sdb1 of=/sdc1/grubboot.lin   

in order to save it on the USB disk as a grubboot.lin?
 
I get an error on this command.

What is the file size of the bootloader 512MB?And what is the first block of the USB drive where I should not save it?

What should I do?

Thanks again

---

### Post by dandnsmith on 2009-03-20
OK, I'll try to answer those:

The HDD you're booting from is /dev/sda (the resident HDD)
The bootloader you want is in the first block (this is what overwrote your original bootloader), so you do:
*dd bs=512 count=1 if=/dev/sda of=grubboot.lin*
and you perform it from 'a convenient position' (looks like somewhere on sdb1, or you can use sdc1, but the path depends on where they are mounted - I'd guess that you might want of=/media/sdc1/grubboot.lin).

The resulting file (grubboot.lin) will be in the folder (directory) from which you issued the command. You can use *cp* to copy it where you want, or do it with the file browser.

The position of /grub/boot is irrelevant to this, as we're not proposing to change anything there.

Once you have this saved file, where you will be able to reach it from Windows, you can do the recovery console thing to restore the Windows bootloader to sda (only it doesn't get referred to that way, and the fixmbr will perform on the resident HDD - make sure you don't have the external disk plugged in).

Next you boot up Windows (and there will be no sign of linux as yet), copy the grubboot.lin to the system disk (C:\ probably), and do that edit to the Windows boot.ini.

Now, when you next boot, you should see the grub entry as an alternative (which will only work if the external drive is plugged in).

Hope that hits the points well enough - I know just how scary it can be, doing these operations of which you have no knowledge.

---

### Post by Feidias on 2009-03-22
It worked!!
 
Dear dandnsmith, Thanks a LOT!!! You were very descriptive.

The problem I had was with the Win recovery console which on pre installed systems doesn't recognise the administration password so there should be a kind of a registry set.

Thanks again!!!

Feidias

---

### Post by Feidias on 2009-03-23
Hello again.

I have one more problem while I was experimenting with Ubuntu.

I don't know If I ll have to make a new thread, I ll put it here because it is related with the previous.
Actually,...
I have tried to install [COLOR="Red"]ubuntu-8.10-server-i386.iso[/COLOR], on an other external drive disk on the previous laptop.

When I have been asked where to install GRUB i didn t install on MBR but I have installed it on one of the partitions the  (hd0,1).

The problem is that GRUB is loaded again when I have plugged the external drive disk.
On the other hand I can't load Windows, it goes to GRUB stage 2 and restarts GRUB stage 1.2
Also, ubuntu is loaded on a console .

 I have tried Windows Recovery Console "fixmbr" but nothinng happened.

I have tried to write the grubboot.lin file to an external USB  with the command:

dd bs=512 count=1 if=/dev/sda of=/media/sdc1/grubboot.lin

and I take the message:

/dev/sda permission denied

Another person I have asked was able to load multiple LINUX editions on a hard drive disk.How is that possible?

How can I restart Windows and fix this problem?

I hope you will see this message

---

### Post by Feidias on 2009-03-24
I have done some progress. 
I have installed the gnome desktop and I can see only 2.5 GB from my Windows VAIO disk (why?).

Now I have 2 options from the information I have concentrated from the Forum and WEB:

OPTION 1
To configure the /boot/grub/menu.lst setting the default value from "0" which is now to "1" to run windows.

OPTION 2
To configure fixboot- fixboot c:

The thing is that now I have at least UBUNTU running. Is there 

any possibility chosing one of the 2 options not to be able to 

run Windows and Ubuntu?

Your opinion is priceless

Thanks

---

### Post by Feidias on 2009-03-26
Hi!

I have finally manage to reboot my system on Windows and on previous Kubuntu system.

I have run from the recovery console of windows: "fixboot c:"
and I came back to the previous settings, with 3 choices:
Windows
Recovery Console
Linx GRUB for the Kubuntu in the other disk

Unfortunately because I couldn't find the boot file for UBuntu server I suppose  now I a I ll have to make again the installation again to the other Hard drive disk.

But where should I install GRUb?

---

### Post by dandnsmith on 2009-03-26
I've had a spot of bother with my internet connection, which stopped me getting back for progress..

That error with the "dd if=/dev/sda " permission looks like you're operating without enough privilege. You can fix this by putting it as "sudo dd ...", which will ask for your password (probably) and then do it.

Where to install grub now - put it somewhere it won't mess things up, and not on an NTFS partition. I cannot recall discussing the detail of your HDD layouts, so won't try to get more specific (so, **not[/n] (hd0) and [b]not** (hd0,1) [where I think youre Windows is]).

---

### Post by Feidias on 2009-03-31
I ve fixed it, now it is ok.
Your tips were valuable.
Thanks again

---

