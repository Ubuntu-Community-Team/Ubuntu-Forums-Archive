---
title: "Cant install Ubuntu Mint"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by kookai9 on 2009-08-20
Cant install Mint or Ubuntu either from the Usb stick.I keep getting an error that maybe the Dell mini 9may be to hot or the disc is dirty and I'm sure its neither.I burned the iso to the stick with the image installer reccomened here & then heard of an tried Ubootin but am getting the same Error.Can anyone help?

---

### Post by dstew on 2009-08-20
Can you boot the USB stick, and get an opening installation menu?

---

### Post by kookai9 on 2009-08-20
Im gettin errno 5  Input/outputerror
I get to choose which country i live in and keyboard layout and it  starts to write it to the hard drive but stalls about half way

---

### Post by snowpine on 2009-08-20
I recommend:

1. Completely reformat the USB stick (so you're starting with a blank slate)
2. Download the linux distro of your choice in .iso format (NOT .img)
3. Check the MD5SUM of the .iso ( [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) )
4. Follow the Unetbootin instructions carefully, step by step: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Post back if you get stuck, letting us know specifically which step is problematic, and copy & paste any error messages. Good luck!

---

### Post by kookai9 on 2009-08-20
Should I format as fat 16 or 32 or even ntfs?
Thanks for the suggestions

---

### Post by snowpine on 2009-08-20
> **kookai9 said:**
> Should I format as fat 16 or 32 or even ntfs?
Thanks for the suggestions

I personally use ext2 but I think maybe fat32 works as well... what does the Unetbootin site say to do? They would know better than I. ;)

---

### Post by presence1960 on 2009-08-20
> **snowpine said:**
> I recommend:

1. Completely reformat the USB stick (so you're starting with a blank slate)
2. Download the linux distro of your choice in .iso format (NOT .img)
3. Check the MD5SUM of the .iso ( [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) )
4. Follow the Unetbootin instructions carefully, step by step: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Post back if you get stuck, letting us know specifically which step is problematic, and copy & paste any error messages. Good luck!

+1

MD5SUM very important, if your iso is corrupted then you will never install. also see this [thread]("http://ubuntuforums.org/showthread.php?t=1207755&page=2") for that error. Just be aware of a mispelling in the command in step #4. it should be this:
```
ubiquity --no-migration-assistant
```
I used it once successfully on a machine that kept giving that error for CD & USB install. I can't remember if I needed to preface the command with sudo or not. Try it without sudo first and see what happens.

---

### Post by kookai9 on 2009-08-25
I reformatted to fat32 with the Hp tool and windows built in tool also just incase,yet I cant get either Ubuntu or mint to install from the stick .Unetbootin puts them on the stick but i'm still getting [Errno 5] .Is it possible for Usb sticks to be damaged ? I would have expected unetbootin to have not been able to burn the image if this was the case. Its driving me nuts;as I have a brick for a netbook if I cant get it to work.

---

### Post by presence1960 on 2009-08-25
> **kookai9 said:**
> I reformatted to fat32 with the Hp tool and windows built in tool also just incase,yet I cant get either Ubuntu or mint to install from the stick .Unetbootin puts them on the stick but i'm still getting [Errno 5] .Is it possible for Usb sticks to be damaged ? I would have expected unetbootin to have not been able to burn the image if this was the case. Its driving me nuts;as I have a brick for a netbook if I cant get it to work.

Did you choose "try ubuntu without any changes"? When the desktop loads open  a terminal and run this command ```
ubiquity --no-migration-assistant
```

I can't remember if you need sudo to preface the command or not. try it first without sudo and see what happens.

---

### Post by kookai9 on 2009-08-25
Yes presence1960 ; it dosnt work using that command either.I dont want to buy an external optical drive just to do an install ,knowing my luck with linux in anycase it woulnt work or the drivers wouldnt be supported.

---

### Post by kookai9 on 2009-08-26
Been doing more google-ing and cant belive the amount of Errno 5's  out there yet there seems to be no one solution.Some people have downloaded repeately and burned to loads of different brand cds/dvds and got it eventuall working.
I cant belive that so many of the distro's can have this problem in theis day and age ;the 1 thing that always gets suggested is check the Md5 which is never corrupted it seems in relation to errno 5, its almost a decade that Windows xp came out but at least it worked ,its almost 6 years now trying various versions of linux [3 of ubuntu] and still cant get it installed; how can 1 learn the command line if 1 cant get it installed. There have been some suggestions that it may be related to corrupted ram memory , i know of memtest86 in windows but dont know whats used in linux .Is there an alternative in linux ?

---

### Post by dstew on 2009-08-26
When you try to boot the USB stick, do you get an opening menu? Can you get a "Live CD" system going from the stick?

EDIT: If the USB stick "Live CD" system is working, you can add the memory test feature: See [this How-To]("http://rudd-o.com/new-projects/portablelinux/documentation/questions-and-tips/how-do-i-run-memtest86-from-my-usb-drive")

---

### Post by kookai9 on 2009-08-26
Strangely when i go to install  evertime it says 9.04 is already installed so i have gone back a few times to the boot screen to boot from the harddisk but it goes no further .The old version that  came originally has been overwritten or damaged from trying to install with unetbootin  or just getting to the 57% install stage and then getting the errno 5 error!

---

### Post by dstew on 2009-08-26
So, do you get a normal "Live CD" system running from the USB stick? Do you only get problems when you try to install?

---

### Post by kookai9 on 2009-08-27
Well once it does fail fromt the stick ,& I get the error message so I go ahead and click ok to confirm acknolowledgement of the error then I get the live Usb version form which I can browse the internet  and open a few apps, buts its only the live version not  the fully installled OS!

---

### Post by dstew on 2009-08-27
> its only the live version not the fully installled OS!I know, I just wanted to see if the USB stick is generally working, and it appears to be, because the Live CD system works.

The error (errno 5) is only a general indication of an input-output error. It is not specific enough to say what the problem is. It could be that you have some memory modules that are not fast enough to keep up with the demands of the software that writes the files to the disk. It could be some bad sectors on the disk. It could be your USB system is not fast enough to keep up with the software for disk transfer.

Since the USB stick appears to be OK, I would do the memory test. If you installed some new memory recently, maybe take out the new memory and try to install again. It is not the amount of memory that gives the error, but the speed of the memory. Any new memory that is not matched well with your system may cause the problem. See my previous post about checking the memory.

You can also check the hard disk for errors using the fsck program from the Live CD. If the hard disk partition you are installing to is /dev/sda1, then you can do ```
sudo fsck -r /dev/sda1
```

---

