---
title: "Dual boot with Win7"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Musket on 2009-10-29
Hi, I am new to Linux so be gentle with me. I have a new install of Windows 7 64 bit and want to do a dual boot. In the past I have always used a different version of windows for the alternative operating system but would like to see what this Linux stuff is all about.    When Karmic Koala is released later today, will a dual boot with that be easy. I have a seperate hard drive that I want to use for Linux. I do not want it on my win7 disk. Any offer of advice would be helpful. I do not want ro risk damaging my installation of win7, It took me a whole day to install all my software and settings. Thanks

---

### Post by Robbartz on 2009-10-29
If you're that worried you could always get 2 drive cradles so that youre Win7 system is on one and the karmic Koala on the other. You can then just remove the Win7 drive from the cradle and insert the other.
 
Drice cradles are very cheap and easy to install.

---

### Post by Lateralis on 2009-10-29
First and foremost, installing Ubuntu onto a hard drive that already has Windows is quite safe.  You won't lose anything from Windows, so long as you don't delete it!  If you're worried about hard disk space or aren't confident in dual booting using the same hard drive, then don't do it even if it is quite straight forward and painless.  And I daresay there are some people here who would help guide you through this process if you wanted it.  

Two alternatives then immediately present themselves.  First is to get the cradle as already suggested.  This means you'd need to disconnect one drive and reconnect the other every time you want to switch operating system.  I've never used these before so I don't know how they work in practice, but I'm guessing that you won't be able to access any files on your Win 7 partition when you're in Linux.  (And also note that Windows doesn't natively recognise anything other than FAT and NTFS filing systems, although there are some programmes that can enable read-write support for these other systems.)  And aside from that, it sounds like a bit of a faff, but again I've never used one so I could be wrong!  

The other way, and the way I use, is to have a second hard drive connected, alongside my Windows drive, and install Linux on the empty disc.  You need to make sure that the BIOS will point to your Linux drive first during boot up so that it will find GRUB (the boot loader software) and give you the choice at boot whether you wish to use Windows 7 or Linux.  In this way, any data - music, videos, documents, photos etc - that are stored in your Windows partition will be accessible in Linux.

---

### Post by wilee-nilee on 2009-10-29
If you decide to dual boot on a single hard drive it is a fairly straight forward process so just ask for help or look for info in the forums. Make sure you try out the live cd without installing to see if everything works generally things do but you want to be sure. Also there is the option of installing inside W7 as a pseudo virtual,(Wubi) this is generally done by people wanting to try out Linux without setting up separate partitions as you would with a dual boot. I would investigate this for doing it in W7 though, like any install you want to make sure the ducks are all in a row. You will see the Wubi icon in the cd portion of the W7. A Wubi install runs a little slower then a dual boot.

---

### Post by theozzlives on 2009-10-29
People make things harder than it is. During the install choose manual, right click on the unused space and choose new. You want a 10-20 GB primary partition, formatted ext3 or 4 with a mount point of /.

Do the same for the unused again. This time, logical, size: double your RAM, and swap.

One last time, primary, whatever space you have left, ext3 or 4, /home.

Finish your install and you'll get a menu to choose Ubuntu or Windows at boot-up.

P.S. Your slave disk will be called "sdb" or something to that effect. Ubuntu don't do letters (C:, D:, etc.) like Windows does.

---

### Post by theozzlives on 2009-10-29
[Here]("http://ubuntuforums.org/showthread.php?t=1244185") is something you might find useful. On 7, it's Users instead of Documents and Settings.

---

### Post by Musket on 2009-10-29
Thanks very much for the assistance. I will give it a go when the latest download goes live.  I don't like the idea of the install inside windows using wubi. I will go for my second hard drive which is 500 gig.

---

### Post by gimcrack on 2009-10-29
All my HDDs are SATA- If I don't want to accidental mess up one of my SATA drives - Say one has Windows on it. I disconnect those HDDs from my motherboard. Install Linux on the connected SATA HDD. After installing Linux. Reconnect the other SATA HDDs.

It's a simple task to do. And it will put your mind at ease.

---

### Post by Lateralis on 2009-10-29
Yes, you can disconnect your hard drive during installation of Linux on a separate hard drive, but then GRUB doesn't see Win 7 - switching between the two operating systems is therefore more of a hassle.  

No matter what you decide to do Musket, there is an entire forum that will help you out at a level that is applicable to you. =)

---

### Post by mab1376 on 2009-10-29
Just set the installation to install grub in the advanced menu in the last window to the drive which Ubuntu is installed and grub-config will take care of the rest during installation.

If you only have on drive it should do everything fine, so ling as you set the install partition correctly (i.e. don't overwrite Win7).


I have Win7 on sda1 and Ubuntu on sdb1, I set Ubuntu to be installed on sdb1 and installed the boot loader on sdb and set my BIOS to boot that drive. It autoconfig'ed the Win7 boot loader as an option automatically.

this is what the grub.cfg entry from Win7 should look like roughly.

```
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f81cef491cef020c
	chainloader +1
}
```

---

### Post by weekend camper on 2009-10-29
I think the key to the OP's post is that he is brand new to Linux and wants to NOT impact his Windoze install.  Valid points, no matter how easy Linux dual booting is for those of us who have done it for years.


OP, the posters are correct above me, dual booting is amazing stable these days.


What I'd suggest to the OP (assuming low OS literacy) is installing Linux to the secondary HDD and ONLY use one HDD at a time.  If 'something' happens to the Linux install, no biggie, you have your Windoze HDD safe and secure.  Get used to Linux before trying a dual boot (but again, there ain't nothing wrong with it from the start).  You can do an auto install for the first times, then try a manual one, to get used to what goes where.




Slightly OT, but if the OP wants Windows to be in charge of the boot, not GRUB2, then check out a program called easyBCD.  You need the beta for Win7/Ubuntu9.10 on GRUB2.

---

### Post by slymi2005 on 2009-10-29
I followed theozzlive's instructions but the computer always boots into windows 7, it appears grub is not even installed. When vista was installed grub always showed up but when I upgraded to windows 7 grub went away. I figured by doing a fresh install of ubuntu 9.10 I would be able to get grub back but this has not been the case.

---

### Post by BlackMaxPhoto on 2009-10-30
Safe, sane and running on this machine as of a few hours ago is run the Win7 install and updates and then install Karmic from Live CD.

... tried Wubi and it locked up on three attempts to get it to run.

Windows 7 Ultimate 32bit and Karmic AMD 32bit

HP Pavillion m8400f, AMD Phenom 9500, 3G RAM, nVidia GeForce 8500


:)

BC

---

