---
title: "grub / windows / multi-hd issue"
date: 2008-11-14
forum: General Help
---

### Post by csmaster2005 on 2008-11-14
Ok, I have a semi-strange case. Essentially, I have 6 hard drives.... 4 setup in a raid-5, 1 for windows, 1 for ubuntu.
I had ubuntu installed a while ago, reformatted windows, and obviously grub was gone. I recently decided to re-install ubuntu entirely, hoping it'd automatically bring back grub, but that didn't work, and computer just booted windows (which, I think, is because my bios booted the windows drive first... I wasnt sure how to change it in award bios).
 
The 160gb drive is my windows drive
the 120gb drive is my ubuntu drive

I decided to use the following post:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

And followed the directions in the first section, which didn't work, then did what was specified in 'Overwriting the Windows bootloader'
The 2 key things to note are: 1. I didn't mount a boot, since I dont think I have one. 
Secondly, when I ran the command
```

sudo grub-install --root-directory=/mnt/root /dev/hde

```

I specified hde (my windows drive) and NOT sdf (where ubuntu is), since I wanted to override THAT drives boot information.

Anyways, after that I rebooted, and got a 'grub error 21' issue. But now I'm repetitively getting a 'grub harddisk error' when I boot up. I can't boot either windows nor ubuntu now.

Can anyone please give me some guidance?

Also, one note: I'm booting using windows liveCD for now...

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x724eb51c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      109443   879095808    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92dbbd4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36482   293033984    7  HPFS/NTFS

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92dbbd47

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36482   293032960    7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x724eb517

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      109443   879098880    7  HPFS/NTFS

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x115b115b

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       19457   156286976    7  HPFS/NTFS

Disk /dev/sdf: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a001815

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       13995   112414806   83  Linux
/dev/sdf2           13996       14593     4803435    5  Extended
/dev/sdf5           13996       14593     4803403+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

---

### Post by caljohnsmith on 2008-11-14
So you have no way of changing your BIOS to boot your Ubuntu drive? That would be the most ideal so that you can keep your drives independent of each other. If that is not a possibility, then you can install Grub to the MBR of the sde Windows drive and have it point to the Ubuntu drive for Grub's boot files, but in order to do that, ideally you have to know which drive Ubuntu is in the BIOS boot order; otherwise you will have to simply try all 5 possible combinations, since Ubuntu could be 2nd, 3rd, 4th, 5th, or 6th in the BIOS boot order if the Windows sde drive is 1st.

Another option that I would recommend is using "Grub4DOS" inside of your Windows partition, because then you can keep your drives independent of each other; if something happens to the Ubuntu partition/drive, you will still be able to boot Windows. If you do the method above where you install Grub to the MBR of the Windows drive and have it point to the Ubuntu drive for Grub's boot files, then if anything happens to the Ubuntu partition/drive, you most likely won't be able to boot at all. It's up to you though; let me know if you want help with either option and I can give you more specifics. :)

P.S. Are you using Vista or XP? If you are using Vista, instead of using Grub4DOS, you can use "[EasyBCD]("http://neosmart.net/dl.php?id=1")" to simply add Ubuntu as a boot option in your Vista boot menu.

---

### Post by d-man97 on 2008-11-14
You're getting a grub error, that's good. So, you have grub installed on the MBR of the drive your BIOS is booting to. What you need to do now, is find the linux / partition from within grub.

Grub can use UUID instead of the (hd4,2) notation.
While in the LiveCD, run:
```
ls -l /dev/disk/by-uuid
```
Noting the UUID of the partition Linux is on. For me, it is a separate /boot partition, but Linux adds symbolic links to your boot files, so you don't have to point it to /boot, it will find them from / just fine.

Reboot and at the grub menu (hit Esc to see it if needed) edit the top-most Linux command by hitting 'e'. Edit the top-most line again by hitting 'e'. Change it from the (hdX,#) to "uuid  <UUID-of-drive>" (my grub menu uses 2 spaces, but the menu.lst file uses a tab, probably just need some white space). Hit 'Esc' to get back to the menu and hit enter to boot!

---

### Post by d-man97 on 2008-11-14
And, yes, caljohnsmith is correct. Since you are running RAID, I assume you need your Windows partition in working order.

Install grub4dos on your windows' drive MBR to boot windows & linux.
Install grub on your linux drive MBR to boot windows & linux too.

If anything happens to either MBR, you can still boot into both.
If anything happens to either of your drives, the other OS will still be intact.
But, this also assumes you can change your BIOS boot drive, which you were apparently having problems doing.

---

### Post by csmaster2005 on 2008-11-14
d-man 97: I'm not sure why having a raid should affect anything, and also I don't think I can get to the grub menu, since grub itself seems to be having issues loading. Here's the output of ls -l /dev/disk/by-uuid, not sure what to do with it:
```

ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-11-14 02:33 0c2924c7-67c8-4411-8827-038ccdfb61d3 -> ../../sdf1
lrwxrwxrwx 1 root root 10 2008-11-14 02:33 9709a606-97e1-47b3-9c16-0bfd417eeab4 -> ../../sdf5
lrwxrwxrwx 1 root root 10 2008-11-14 02:33 C66AB94E6AB93BCD -> ../../sde1
ubuntu@ubuntu:~$ 

```
caljohnsmith:
no, I couldn't figure out how to get it to boot the ubuntu drive. I think it's because my raid drives are all SATA, but the windows and ubuntu drives are IDE and share 1 IDE cable, and the ubuntu one is the slave one I tihnk.

Regardless, I think what I tried before was installing grub to the windows drive, but that resulted in the error noted above, so I wasn't sure what went wrong.

As for what you mentioned regarding knowing which order the ubuntu drive is in bios boot.... why do I need that? I thought what I did before (from that link I mentioned) I specified that ubuntu is on (hd5,0) and told grub that ubuntu was there, and to install grub to the windows mbr, which gave the error.

I'm running windows vista. I think the ubuntu drive already has grub installed on it, from when I installed ubuntu yesterday, , so if we can just get whatever is on the windows drive to list both of them, then if the windows drive ever fails, the ubuntu one should still be bootable without me having to go install grub again.

So, your call as to what I should do. I just hope all my windows files are ok :)

---

### Post by caljohnsmith on 2008-11-14
> **csmaster2005 said:**
> 
As for what you mentioned regarding knowing which order the ubuntu drive is in bios boot.... why do I need that? I thought what I did before (from that link I mentioned) I specified that ubuntu is on (hd5,0) and told grub that ubuntu was there, and to install grub to the windows mbr, which gave the error.
Yes, that unfortunately was most likely the problem; when you install Grub to the MBR of a drive different than the drive the Grub boot files are on (like you tried to do), then you have to know which drive Ubuntu is in the BIOS boot order, because on start up, Grub sees the order of drives as the BIOS boot order, not how the drives are ordered in /dev once you boot into Ubuntu. If you have only two drives, then the directions in that tutorial work since Ubuntu can only be the second drive in the BIOS boot order if you install Grub to the MBR of the other drive; but having more than 2 drives means that tutorial will not necessarily work. 
> **csmaster2005 said:**
> 
I'm running windows vista. I think the ubuntu drive already has grub installed on it, from when I installed ubuntu yesterday, , so if we can just get whatever is on the windows drive to list both of them, then if the windows drive ever fails, the ubuntu one should still be bootable without me having to go install grub again.

So, your call as to what I should do. I just hope all my windows files are ok :)
Since you have Vista, I would recommend first trying that EasyBCD program I linked to in my previous post to add the Ubuntu Grub boot sector to your Vista boot loader. If you are lucky, it will work, but it may not work since you have more than two drives; again, it all depends on how your drives are ordered in the BIOS boot order. Here is a tutorial of how to use it to add Ubuntu to the Vista boot menu:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

To use that tutorial, you first have to install Grub to the boot sector of your Ubuntu partition, and you can do that with:
```
sudo grub
grub> root (hd5,0)
grub> setup (hd5,0)
grub> quit
```
If that doesn't work, then I would definitely recommend Grub4DOS; it is easy to install and use, and you can easily boot Ubuntu and Vista from it. Or if you want to just go with Grub4DOS without messing with EasyBCD, let me know, and I can give you specifics of how to install it.

EDIT: I just realized, to use EasyBCD you first need to boot into Vista, which you can't do any more. To boot into Vista you would have to boot your Vista Install CD and run:
```
bootrec /fixmbr
```
I think that's another good reason to just use Grub4DOS, which is what I would use if I were you. :)

---

### Post by csmaster2005 on 2008-11-14
alright, since you're recommending just doing it, can you please give me directions on what to do to setup grub4dos? :)

thanks again for all the help!

---

### Post by caljohnsmith on 2008-11-14
Yes, as you can see from my previous post, I was sort of thinking out loud and finally concluded that Grub4DOS is probably your best bet; sorry I wasn't just more clear up front. :)

Anyway, to install Grub4DOS, here are the steps:
[LIST=1]
[*]Download the Grub4DOS 0.4.4 package to your Ubuntu desktop from [here]("http://download.gna.org/grub4dos/grub4dos-0.4.4-2008-07-21.zip").
[*]Open a terminal, do the following commands, and stop immediately if for some reason you get an error from any command:
```
sudo mkdir /mnt/sde1 /mnt/sdf1
sudo mount /dev/sde1 /mnt/sde1
sudo mount /dev/sdf1 /mnt/sdf1
cd ~/Desktop
unzip grub*.zip
cd grub*
sudo cp grldr /mnt/sde1/.
sudo cp /mnt/sdf1/boot/grub/menu.lst /mnt/sde1/.
sudo dd if=grldr.mbr of=/dev/sde bs=440 count=1
sudo dd if=grldr.mbr of=/dev/sde skip=1 seek=1
```
[*]Next modify your menu.lst:
```
gksudo gedit /mnt/sde1/menu.lst
```
And add the following entry at the end of the file for Vista:
```
title Windows Vista
root (hd0,0)
chainloader +1
```
Also, you will need to modify your Ubuntu entries in the menu.lst to use "root (hd1,0)" instead of the "uuid" line used in Intrepid, similar to:
```

title		Ubuntu 8.10, kernel 2.6.27-7-generic
[COLOR="Blue"]root            (hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```
Note that (hd1,0) is an educated guess since we don't know yet whether Ubuntu is actually the second in the BIOS boot order, which is (hd1); we may have to change that.
[/LIST]
Just a small caveat: make sure to copy and paste all the commands, especially the dd commands since those can be dangerous if you make even a small typo. Also, please post the output of all the above commands so I can make sure everything went OK. 

If all goes well and you don't get any errors, reboot, and let me know how far you get. :)

---

### Post by csmaster2005 on 2008-11-14
hmm, I got a problem with the mount... when I started running the above commands, I got the following error, then stopped. Awaiting your response :)

By the way, thanks again for all the help!
```

ubuntu@ubuntu:~$ sudo mkdir /mnt/sde1 /mnt/sdf1
ubuntu@ubuntu:~$ sudo mount /dev/sde1 /mnt/sde1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sde1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sde1 /mnt/sde1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sde1 /mnt/sde1 ntfs-3g force 0 0
ubuntu@ubuntu:~$ sudo mount /dev/sdf1 /mnt/sdf1

```

---

### Post by caljohnsmith on 2008-11-14
OK, that's not a problem, just do:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sde1
```
And then try mounting sde1 again and continuing with the rest of the directions. Let me know if you run into any more problems. :)

---

### Post by csmaster2005 on 2008-11-14
ok that worked.

I've started doing all the commands, and when I got to adding the entry at the end of the file...

I found this already in the end of the file:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sde1
title		Windows Vista/Longhorn (loader)
root		(hd4,0)
savedefault
makeactive
map		(hd0) (hd4)
map		(hd4) (hd0)
chainloader	+1


```

Is that supposed to be there? Or do I need to remove that and put what you gave me? Or just put what you gave me at the end of the file, after that?

also, just for the record, here's my outputs so far
```

ubuntu@ubuntu:~$ sudo ntfsfix /dev/sde1
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sde1 was processed successfully.
ubuntu@ubuntu:~$ sudo mount /dev/sde1 /mnt/sde1
ubuntu@ubuntu:~$ sudo mount /dev/sdf1 /mnt/sdf1
mount: /dev/sdf1 already mounted or /mnt/sdf1 busy
mount: according to mtab, /dev/sdf1 is already mounted on /mnt/sdf1
ubuntu@ubuntu:~$ cd ~/Desktop
ubuntu@ubuntu:~/Desktop$ unzip grub*.zip
Archive:  grub4dos-0.4.4-2008-07-21.zip
   creating: grub4dos-0.4.4/
  inflating: grub4dos-0.4.4/bootlace.com  
  inflating: grub4dos-0.4.4/ChangeLog_GRUB4DOS.txt  
   creating: grub4dos-0.4.4/chinese/
  inflating: grub4dos-0.4.4/chinese/grldr  
  inflating: grub4dos-0.4.4/chinese/grub.exe  
  inflating: grub4dos-0.4.4/config.sys  
  inflating: grub4dos-0.4.4/COPYING  
  inflating: grub4dos-0.4.4/default  
  inflating: grub4dos-0.4.4/Get_Source_of_This_Build.txt  
  inflating: grub4dos-0.4.4/grldr    
  inflating: grub4dos-0.4.4/grldr.mbr  
  inflating: grub4dos-0.4.4/grub.exe  
  inflating: grub4dos-0.4.4/grub.pif  
  inflating: grub4dos-0.4.4/hmload.com  
  inflating: grub4dos-0.4.4/menu.lst  
  inflating: grub4dos-0.4.4/README_GRUB4DOS.txt  
ubuntu@ubuntu:~/Desktop$ cd grub*
ubuntu@ubuntu:~/Desktop/grub4dos-0.4.4$ sudo cp grldr /mnt/sde1/.
ubuntu@ubuntu:~/Desktop/grub4dos-0.4.4$ sudo cp /mnt/sdf1/boot/grub/menu.lst /mnt/sde1/.
ubuntu@ubuntu:~/Desktop/grub4dos-0.4.4$ sudo dd if=grldr.mbr of=/dev/sde bs=440 count=1
1+0 records in
1+0 records out
440 bytes (440 B) copied, 0.0135628 s, 32.4 kB/s
ubuntu@ubuntu:~/Desktop/grub4dos-0.4.4$ sudo dd if=grldr.mbr of=/dev/sde skip=1 seek=1
17+0 records in
17+0 records out
8704 bytes (8.7 kB) copied, 0.000402683 s, 21.6 MB/s
ubuntu@ubuntu:~/Desktop/grub4dos-0.4.4$ gksudo gedit /mnt/sde1/menu.lst

```

---

### Post by caljohnsmith on 2008-11-14
You can go ahead and replace your current Vista entry in your menu.lst with the one I gave. It looks like from the output of all those commands everything has gone smoothly, so when you reboot, you should at least get the Grub4DOS menu and be able to boot Vista. If booting Ubuntu doesn't work, let me know, and we can work from there. :)

---

### Post by csmaster2005 on 2008-11-14
thanks caljohnsmith!! Worked like a charm, and got both systems booting.

Now, time to figure out how to get ubuntu to run dual screens with my radeon card... ;)
I appreciate all your help!

---

### Post by caljohnsmith on 2008-11-14
That's great news, and you're certainly welcome; I'm really glad you have Vista and Ubuntu booting OK now. One last thing I wanted to mention is that you may want to create a symbolic link to the Vista menu.lst so that the menu.lst will automatically get updated when you get kernel upgrades; that way you don't have to manually copy/paste the boot stanzas into the Vista menu.lst when you get a kernel upgrade. In other words, if you put Vista's partition in your /etc/fstab so it gets automatically mounted on start up, then you can symlink to its menu.lst with:
```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo ln -s [COLOR="Blue"]/media/sde1[/COLOR]/menu.lst /boot/grub/menu.lst
```
Where the Vista partition is mounted on /media/sde1, but you can change that to whatever you want. Anyway, cheers and have fun with your OSes. :)

---

