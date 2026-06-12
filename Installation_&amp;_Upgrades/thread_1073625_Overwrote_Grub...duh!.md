---
title: "Overwrote Grub...duh!"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by alexisantonakis on 2009-02-18
Hi,

I was trying to recover some data from a second HDD using the ddrescue command and accidentaly set it to restore to the HDD on my laptop...this has now overwrote a substantial amount of data on my laptop's HDD and I can no longer boot up.

Is there a way to undo the ddresuce command and if so how..I can;t even get into a terminal shell.
Failing that is there a way to repair/reinstall Ubuntu without loosing data? If nothing else if I can recover the data in my home, /var/www and Mysql (can;t remember the path to this one) directory then that should be sufficient.

Thanks
Alexis

---

### Post by kestrel1 on 2009-02-18
You can use the Live CD to recover your data as long as the partitions are still intact.
If you want to restore grub to see if you can boot up have a look at this link:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
Scroll down the page & use the command line way to restore Grub.

---

### Post by alexisantonakis on 2009-02-18
Thanks, downloading the live CD now and will see what happens.

---

### Post by caljohnsmith on 2009-02-18
Once you have your Live CD, how about opening a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -l
```
That show us if you actually overwrote the partition table, which sounds likely. If fdisk doesn't show any partitions, then to recover your data, I would recommend first trying "testdisk" to see if it can find any intact partitions on that HDD to restore. To use testdisk, just download the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions (if any) seem to be your lost partitions. We can work from there if you want.

---

### Post by alexisantonakis on 2009-02-18
Thanks for that...it does appear I still have the partitions intact...trouble is how do I output the results of the fidsk?

I mean I get bring it up on the affected computer, but how can I export it to say a thumb drive? Or even the clipboard?

---

### Post by caljohnsmith on 2009-02-18
> **alexisantonakis said:**
> Thanks for that...it does appear I still have the partitions intact...trouble is how do I output the results of the fidsk?

I mean I get bring it up on the affected computer, but how can I export it to say a thumb drive? Or even the clipboard?
I think if you go under the Places > Removable Media menu on the Ubuntu desktop, you can access your thumb drive there. When you do the fdisk command in the terminal, you can highlight it and copy/paste it to a text editor for example (Applications > Accessories > Text Editor); from there you could save it to your thumb drive. You can also do the same when you testdisk in the terminal.

---

### Post by alexisantonakis on 2009-02-18
Thanks, I know what I was doing wrong...CTRL+C and not CTRL+SHFT+C...learn something new everyday..thanks

Here is the output of fdisk:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006f351

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   300495824   150247881   83  Linux
/dev/sda2       300495825   312576704     6040440    5  Extended
/dev/sda5       300495888   312576704     6040408+  82  Linux swap / Solaris


Are you saying I should also run testdisk on it as well?

---

### Post by caljohnsmith on 2009-02-18
Do you remember exactly what was the dd_rescue command you used orginally? If you could post that, that would give us a better idea of what might have been overwritten. But the good news is your sda drive's partition table seems to be just fine, so how about trying:
```
sudo mount /dev/sda1 /mnt && ls -l /mnt
```
And please post the output. Also do:
```
nautilus /mnt/home &
```
And use the nautilus browser that comes up to go through your home directory for example to see if everything looks like it is there or not. Let me know how that goes.

---

### Post by alexisantonakis on 2009-02-18
Hi,

Here is the output

ubuntu@ubuntu:/dev$ sudo mount /dev/sda1 /mnt && ls -l /mnt
total 113787
-rw-r--r-- 1 root root  424317 2008-02-12 10:39 abi-2.6.22-14-generic
-rw-r--r-- 1 root root  422667 2008-05-01 17:59 abi-2.6.24-17-generic
-rw-r--r-- 1 root root  422667 2008-05-29 02:39 abi-2.6.24-18-generic
-rw-r--r-- 1 root root  422667 2008-08-21 04:46 abi-2.6.24-19-generic
-rw-r--r-- 1 root root  422781 2008-07-28 18:03 abi-2.6.24-20-generic
-rw-r--r-- 1 root root  422838 2008-10-22 03:12 abi-2.6.24-21-generic
-rw-r--r-- 1 root root   75311 2008-02-12 10:39 config-2.6.22-14-generic
-rw-r--r-- 1 root root   80071 2008-05-01 17:59 config-2.6.24-17-generic
-rw-r--r-- 1 root root   80071 2008-05-29 02:39 config-2.6.24-18-generic
-rw-r--r-- 1 root root   80049 2008-08-21 04:46 config-2.6.24-19-generic
-rw-r--r-- 1 root root   80073 2008-07-28 18:03 config-2.6.24-20-generic
-rw-r--r-- 1 root root   80062 2008-10-22 03:12 config-2.6.24-21-generic
drwxr-xr-x 2 root root    1024 2008-10-28 15:41 grub
-rw-r--r-- 1 root root 7725402 2008-02-21 16:39 initrd.img-2.6.22-14-generic
-rw-r--r-- 1 root root 7725188 2008-02-13 17:47 initrd.img-2.6.22-14-generic.bak
-rw-r--r-- 1 root root 8071583 2008-06-03 06:31 initrd.img-2.6.24-17-generic
-rw-r--r-- 1 root root 8035920 2008-05-08 16:01 initrd.img-2.6.24-17-generic.bak
-rw-r--r-- 1 root root 8071919 2008-06-04 18:00 initrd.img-2.6.24-18-generic
-rw-r--r-- 1 root root 8071929 2008-06-04 18:00 initrd.img-2.6.24-18-generic.bak
-rw-r--r-- 1 root root 8074846 2008-08-26 22:06 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 8074555 2008-07-16 16:24 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root 8074774 2008-08-06 19:40 initrd.img-2.6.24-20-generic
-rw-r--r-- 1 root root 8074695 2008-07-29 15:40 initrd.img-2.6.24-20-generic.bak
-rw-r--r-- 1 root root 8073664 2008-10-28 15:41 initrd.img-2.6.24-21-generic
-rw-r--r-- 1 root root 8075805 2008-08-26 22:06 initrd.img-2.6.24-21-generic.bak
drwx------ 2 root root   12288 2007-12-07 19:03 lost+found
-rw-r--r-- 1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root  823535 2008-02-12 10:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root  905012 2008-05-01 17:59 System.map-2.6.24-17-generic
-rw-r--r-- 1 root root  905012 2008-05-29 02:39 System.map-2.6.24-18-generic
-rw-r--r-- 1 root root  905170 2008-08-21 04:46 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root  905283 2008-07-28 18:03 System.map-2.6.24-20-generic
-rw-r--r-- 1 root root  905617 2008-10-22 03:12 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root 1764536 2008-02-12 10:39 vmlinuz-2.6.22-14-generic
-rw-r--r-- 1 root root 1921944 2008-05-01 17:59 vmlinuz-2.6.24-17-generic
-rw-r--r-- 1 root root 1921528 2008-05-29 02:39 vmlinuz-2.6.24-18-generic
-rw-r--r-- 1 root root 1921464 2008-08-21 04:46 vmlinuz-2.6.24-19-generic
-rw-r--r-- 1 root root 1920664 2008-07-28 18:03 vmlinuz-2.6.24-20-generic
-rw-r--r-- 1 root root 1920760 2008-10-22 03:12 vmlinuz-2.6.24-21-generic



When I run the Nautilus command it says it cannot find /mnt/home.



As for ddrescue

If memory serves me I typed:
ddrescue /dev/sdb1 /dev/sda1

The exact paths might not be correct but it was the secondary drive first and the primary drive second...I did no other options

Thanks for all your help on this btw, I really appreciate it

---

### Post by caljohnsmith on 2009-02-18
Ooooh, ouch. It looks like your sda1 Ubuntu install was at least partially overwritten with a boot directory that you copied from the other drive. That means about your only chance of recovering your files would be to use a data mining tool like "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")". Photorec will go through the entire partition sector-by-sector and try to recover every single file it can find. So it can be a long process, and also it is a lot of trouble to go through all the recovered files, because they often have generic names with no extensions if photorec can't also recover the original file name. In addition, you will need a partition/drive at least as large as your sda1 partition to save all the recovered files to. So if you want to give it a try, you can do:
```
sudo apt-get install testdisk
sudo photorec /dev/sda1
```
Let me know how it goes if you give it a try.

---

### Post by alexisantonakis on 2009-02-18
Ok, will give it a go, got nothing to loose.

I notice that I can specify certain file types to recover...as I don;t have another disk to write to, I was thinking of trying to recover the files to a thumb drive...trouble is in photrec I can't locate where it is located..I cannot access the media directory.

Something else I've been thinking about..if I do a re-install (is there a repair option?) of Ubuntu, will it automatically overwrite all the existing data? I was thinking, if I set up a different user, and as 90% of the files were stored in the user folder, could I then access the files that way? A long shot I know, but I;m trying to think of everything.

Many thanks

---

### Post by caljohnsmith on 2009-02-18
> **alexisantonakis said:**
> Ok, will give it a go, got nothing to loose.

I notice that I can specify certain file types to recover...as I don;t have another disk to write to, I was thinking of trying to recover the files to a thumb drive...trouble is in photrec I can't locate where it is located..I cannot access the media directory.

Before you run photorec, you could cd into the media directory with:
```
cd /media
sudo photorec /dev/sda1
```
And then photorec will by default save the files to the media directory, but you of course would want to specify whichever directory in the media directory that has your thumb drive mounted as the place to save the files. 
> **alexisantonakis said:**
> 
Something else I've been thinking about..if I do a re-install (is there a repair option?) of Ubuntu, will it automatically overwrite all the existing data? I was thinking, if I set up a different user, and as 90% of the files were stored in the user folder, could I then access the files that way? A long shot I know, but I;m trying to think of everything.

Many thanks
Doing a reinstall will unfortunately just wipe out the existing data even further. I think photorec is probably your best bet for recovering your files at this point. Good luck and let me know how it goes. :)

---

