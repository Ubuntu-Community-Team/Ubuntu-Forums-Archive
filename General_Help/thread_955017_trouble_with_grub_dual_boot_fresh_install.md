---
title: "trouble with grub dual boot fresh install"
date: 2008-10-21
forum: General Help
---

### Post by millreefmellon on 2008-10-21
Hello,

I can't reach Windows xp through grub.  I have installed ubuntu on a computer that is new except for one old hard drive.  On the old drive is windows xp.  On the new drive is ubuntu.

When I installed ubuntu, the boot sequence went cddvd drive, then new drive, then old drive.  Ubuntu installed beautifully on the new drive.  When I restarted, however, I would not go to grub but only to a black screen with a blinking dash in the upper left corner.  

I altered the boot sequence to cddvd drive, then old drive, then new.  That fixed that problem.  Grub came up, and one of the options was to load ubuntu.  Down the page was Windows XP.  Selecting that option did not work.

Looking at grub's menu.lst, I see that the Debian installer automatically added an entry for a non-linux OS on /dev/hdb1.  It reads as follows:

title  Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

Grub's device.map file says the following:
(hd0) /dev/hdb
(hd1) /dev/sda

When I run fdisk -l, it returns the following information:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eba09

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29743   238910616   83  Linux
/dev/sda2           29744       30401     5285385    5  Extended
/dev/sda5           29744       30401     5285353+  82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd94fd94f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7298    58621153+   7  HPFS/NTFS
/dev/sdc2            7299        7311      104422+  83  Linux
/dev/sdc3            7312       14596    58516762+  8e  Linux LVM


The 250 GB drive is the new drive.  The 120 GB drive is the old drive.

Finally, in Grub's menu.lst, the following lines appear after ## ## End Default Options and before ### Debian automagic kernels list:

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f0c83dae-89c2-48a2-ba9a-ddc6bb24528e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f0c83dae-89c2-48a2-ba9a-ddc6bb24528e ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet


Though I've read many of the excellent posts and tutorials on editing grub for dual booting from two hard drives, I'm quite confused about how to edit Grub to permit me to load the Windows XP system from time to time.  In particular, I'm quite confused by all the different designations of the drives.  Would someone help me to sort this out and provide instructions for fixing this?

A last concern I have is that if Grub boots from the old and slower  drive where Windows is, then Ubuntu on the new and faster drive will only work as fast as the old drive.


Thanks for any help I receive,

millreefmellon

---

### Post by tuxxy on 2008-10-21
This post maybe useful to resotre/install GRUB to the correct location.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by caljohnsmith on 2008-10-21
Since your Ubuntu entries in the Grub menu use (hd1,0), that means Grub must be installed itself to the MBR (Master Boot Record) of your other Windows drive, sdc; we also know that since you said you have your BIOS set to boot your Windows drive on startup. That means that the Grub entry you have that uses (hd0,0) should be correct. When you tried to boot Windows from the Grub menu, what exactly happened? Did you get any Grub errors? Or Windows errors maybe?

---

### Post by millreefmellon on 2008-10-21
> **tuxxy said:**
> This post maybe useful to resotre/install GRUB to the correct location.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Thanks for the link.  I found /boot/grub/stage1 on (hd1,0), which is, according to Grub's device map file, /dev/sda, which is the new 250GB drive.  So it seems that Grub is in the correct location.

Any further thoughts?

Thanks,

mfh

---

### Post by meierfra. on 2008-10-21
> Any further thoughts?

How about answering caljohnsmith's questions?

---

### Post by millreefmellon on 2008-10-21
When I boot Windows from the Grub menu, the following happens.  I go to a screen which reads as follows at the start: 

Please select the operating system to start:
Microsoft Windows XP Professional
Kubuntu
Use the up and down arrow keys to move the highlight to your choice
Press ENTER to choose
For troubleshooting and advanced startup options for Windows, press F8.

If I highlight and choose Windows, I briefly see the Windows splashscreen and its loading, then the screen goes dark and the computer goes back and begins to restart itself, bringing me back to Grub once again.  The same thing happens if I press F8.  I go to a Windows Advanced Options Menu.  One of the options is: Start Windows Normally.  I'm then returned to the previous screen.  I choose Windows, and the cycle repeats.

Kubuntu appears in part because on my previous computer, I had Kubuntu on another drive.  But that drive died.  I replaced it and the rest of the hardware except the hard drive with Windows on it.

As far as Grub's being installed to the old Windows drive, I just found that /boot/grub/stage1 is on (hd1,0), which is the new Ubuntu drive.  See my reply just above to tuxxy.

If I were to speculate, it would be that I have grub now installed on both drives.  It's on the old drive from the old installation of kubuntu.  And it's on the new drive with the new Ubuntu installation.  But I know I don't know what I'm talking about. 

Any further thoughts?

Thanks,
 
mfh

---

### Post by millreefmellon on 2008-10-22
> **meierfra. said:**
> How about answering caljohnsmith's questions?

I did my best to do so in the next post.

---

### Post by caljohnsmith on 2008-10-22
Well if you are getting as far as the Windows boot menu, then it is almost certain you have a Windows problem and not a Grub problem at this point. It would be good to check if your boot.ini is correct, so boot up your Live CD, open a terminal, and do:
```
sudo mount /dev/sdc1 /mnt
cat /mnt/boot.ini
```
And post the results of that. Next, if you have your Windows XP Install CD, I would boot that up, go to the "recovery console" and first run:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors. Reboot, try Windows again, and let us know if anything changed about Windows' booting behavior. You might have to resort to a Windows Repair from your Win Install CD, but try the above first and report the results.

---

### Post by millreefmellon on 2008-10-22
OK, when I ran: 

sudo mount /dev/sdc1 /mnt

I got back the message:
mount: special device /dev/sdc1 does not exist

However, from the Gnome desktop, I was able to reach the drive and find the file boot.ini.  It reads as follows:

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

c:\wubildr.mbr="Kubuntu"


I reached the drive by going Places, Home Folder, and down the left column of that window appears 60.0 GB Media.  When I open that, I find Microsoft files, including boot.ini.

  Next, I booted my Windows XP Install CD, went to the recovery mode, and ran:

chkdsk /r

It ran for a long time, and reported the following:
found and fixed one or more errors on the volume

I tried to run Microsoft from the Grub menu once again, but unfortunately Microsoft shut down during loading once again.

I do now get a screen that begins as follows:

"We apologize for the inconvenience, but Windows did not start successfully.  A recent hardware or software change might have caused this . . . ."

And it is true that I changed hardware.

I should add that to my surprise I found an ubuntu folder with some kubuntu files in it.  I suspect this is from a botched attempt to save my old computer in which this old drive once was.

I really appreciate your helping me with this. I myself can't make heads or tails of the boot.ini file.

Best, 

mfh

---

### Post by caljohnsmith on 2008-10-22
Were you ever able to boot Windows from the old drive on that computer before installing Ubuntu? If not, I think the only thing you could could do besides reinstalling Windows would be to do a "Windows Repair" from your Windows XP Install CD. When you boot up the Windows Install CD, if you choose the "install Windows" option, then after that it will give you a chance to choose "repair Windows." I don't think there is much else you can do short of hacking some Windows system files manually. Let me know how it goes.

---

### Post by millreefmellon on 2008-10-22
Yes, I was able to boot Windows from that drive.  In my old computer, I had that drive and another.  On the other drive, I had Ubuntu.  When the computer started, I got a Grub screen allowing me to choose Ubuntu (the default) or XP.  I rarely went to the XP side, but it worked when I did.

Then the Ubuntu drive died.  In trying to fix things, I managed to delete my kernels.  Then I discovered I had a hardware problem with the drive itself.  The whole machine was 6 or 7 years old, and it seemed cheaper to replace the other stuff too, (except the cool case).  But I kept the old XP drive because I had had no problems with it, and I thought I could use it at least for backup purposes.

I'll give "Repair Windows" a try.  But do you know how Windows is with seeing a new motherboard, processor, ram, and external drives?  Do you know if I am able just to reinstall Windows if repair fails?  Or do I have to pay them money and buy a new install because my machine broke?

Did the boot.ini file seem OK?

Best,

mfh

Once again, thanks.  I deeply appreciate your patience and help.

---

### Post by caljohnsmith on 2008-10-22
Your boot.ini file is fine except still having that line at the end for the Ubuntu Wubi installation (you could delete it, but it may be a moot point if you do a repair or reinstall). Do you still have your Windows product key for that Windows on that old drive? That's probably your only hope, because without that you can't do a Windows repair nor a complete reinstall. If you do have it, then you could go for the Windows Repair and see if that works. It's also going to get messy because you will have to contact Microsoft or something so that you can get updates for Windows on your new hardware, because your Windows product key will be associated with your old setup (assuming you received updates from Microsoft over the internet). So even if you can repair/reinstall Windows, in order to get SP2/SP3 and all the other updates, you might be stuck. But good luck and let me know how it goes. :)

---

### Post by millreefmellon on 2008-10-22
I tried "Repair Windows".  It goes for a while.  It copies files, does some reconfiguring, then it starts to install devices and about five minutes in to what it says is a 39 minute process, it crashes.

I don't still have the product key.  And I don't want to deal with Microsoft.

So . . . .

Goodbye to all that!

And many, many thanks for your help.

Best,

mfh

---

