---
title: "Jaunty + USB NTFS HDD = Missing files"
date: 2009-06-29
forum: Hardware
---

### Post by frankstrudel on 2009-06-29
Hi

I backed up my /home folder onto an NTFS USB HDD while I installed a clean Jaunty installation over Hardy. Hardy had no problems with the NTFS HDD, but it has taken a number of attempts to get Jaunty to mount it at all. Now it has mounted it, the backup folder appears empty (although it is there, and other folders and files on the hdd are there). I believe everything is there, though, due to the way that the size of the HDD is 1000.2 GB, there is 770.8GB free, and the other folders add up to 92.5GB. That's 136.9GB missing, which is about right.

So can anyone explain why this folder is supposedly empty, please? Preferably, could anyone offer a solution?

I've tried the obvious checking if it is hidden with .<filenames>, and checked the properties of the folder but neither have come up trumps. Disk usage analyzer demands that the folder isn't there, but concurs that there is unaccounted space on the drive.

Thanks for your help.

PLEASE tell me my backup isn't lost forever... :cry:[-o<:-({|=

---

### Post by muglikar on 2009-06-29
Hello brother,
                    I have turned to Linux hoping it will solve my problem that my hard drive which is receiving a msg regarding my USB Hard Disk "This device cannot start. (Code 10)"

I have chosen Ubuntu due to recoomendation by a frnd and his advocacy that Ubuntu has huge support and that he has not faced any prob whatsoever whne he used Ubuntu.

I think the problem is because I reinstallled XP sp2, which in turn I did because the HD was running well on my Dell Laptop but its not working on my Desktop...

Another prob is that scrolling on my desktop CRT monitor has suddenly become discrete after I reinstalled XP sp2...

I cant change my Monitor's refresh rate...Earlier I could change it from 60 Hz to 85Hz...

DO U THINK UBUNTU WILL SOLVE THESE PROBLEMS FOR ME?

---

### Post by hxcgrunger on 2009-06-29
I've got the same problem. turned on my computer this morning and my 500gb WD USB NTFS HDD has almost all of the files missing. All the files left visible add up to ~250GB while my system tells me that 454GB is being used. I have checked for hidden files (.<filename>) and yielded nothing. I never had any mounting trouble with it though. However, possibly the weirdest thing is that if I go to /media/disk/ it shows /downloads /images and /system volume information, though if I go to /media/disk/music/ it shows all the sub-folders within my music folder located on the main drive. :confused: any explanation woulld be appreciated.

---

### Post by frankstrudel on 2009-06-30
> I have turned to Linux hoping it will solve my problem that my hard drive which is receiving a msg regarding my USB Hard Disk "This device cannot start. (Code 10)"
...Another prob is that scrolling on my desktop CRT monitor has suddenly become discrete after I reinstalled XP sp2...
...I cant change my Monitor's refresh rate...Earlier I could change it from 60 Hz to 85Hz...

Ubuntu will definitely allow for more configuration options on the monitor front. USB flash drives certainly have great support under ubuntu, i assume because they are FAT formats. However, as i said in my original post, NTFS was a bit tricky (although, reading about, it may just be that this HDD had problems, cos it generally seems to have good support).

If you would like to keep XP, may I suggest trying SP3 (although, having given up dual booting over a year ago, I'm not an expert at MS XP)? Otherwise, you may wish to try dual-booting ubuntu and XP first. If the reason you want certain refresh rates is certain computer games, you may wish to check their compatibility with WINE first, to make sure ubuntu wouldn't just give you more of an issue. :-)

Hope your problems get solved,

Frank

---

### Post by frankstrudel on 2009-06-30
We now have two people with the problem and one looking into ubuntu, but no-one with a clue of what the cause of the problem is, or crucially how to solve it. Help! Help! Save the life of my files!

[-o<

Bump!

---

### Post by frankstrudel on 2009-06-30
I tried the HDD on an XP machine, but no luck; Unknown device. Couldn't find any drivers for it, completely confused it. Unless anyone can think of anything else by tomorrow, I'm going to try defragging it, but I'm loath to do that cos I can't help but feel I'm going to lose the hidden data completely.

---

### Post by frankstrudel on 2009-06-30
(That is, if i can find a way of doing that from ubuntu...)

---

### Post by frankstrudel on 2009-07-01
After looking closely through the non-backup folders that survived on the HDD, I have come across this:

```

/media/disk/System Volume Information/_restore{E7F69C40-4F29-42A6-9437-9A760C446D46}/RP10/change.log
```

and 

```
/media/disk/System Volume Information/MountPointManagerRemoteDatabase
```

The only references to these that I can find are from XP, but as I have only used this external HDD on ubuntu, and XP has failed to recognise it as a hard drive (just an unknown entity plugged into the USB), could this be some sort of restore point generated by the hard drive that could save my files?

[-o<

---

### Post by frankstrudel on 2009-07-01
Another possible lead, if i do;

```
ls -la
```

in the folder where my backup should be, i get this error message; 

```
ls: reading directory .: Input/output error
total 0

```

Which may have something to do with it?:-k

Please Help!!![-o<:cry:

---

### Post by frankstrudel on 2009-07-01
This is definitely an input/output error. What does that mean and how do i fix it?

---

### Post by hxcgrunger on 2009-07-02
I have discovered after running ls that two of the files written to the directory can't be accessed due to a Input/Output Error. I think this is what's causing nautilus to not display the majority of the directory. However if I try to remove it or access it in any way I simply get an I/O error. Anyone know how to remove it?

---

### Post by frankstrudel on 2009-07-06
bump

---

### Post by frankstrudel on 2009-07-08
Would it help to start a new thread somewhere, with I/O error in the title?

---

### Post by hxcgrunger on 2009-07-11
If you do post the link to the new post here.

---

### Post by frankstrudel on 2009-07-11
I've given up atm, having retrieved most of my dear departed files using Photorec.

---

### Post by hxcgrunger on 2009-07-11
Well, this stuff happens i guess.

---

### Post by CupofDice on 2009-10-25
I have this same problem. As explained [here]("http://ubuntuforums.org/showthread.php?p=8166545#post8166545"), my files disappeared on me. Yet the ls-la command below says there are twelve files in that folder in my Home. This is on a desktop.

total 12
drwxr-xr-x 2 cupofdice cupofdice 4096 2009-10-25 22:28 .
drwxr-xr-x 3 cupofdice cupofdice 4096 2009-10-25 22:33 ..
-rw------- 1 cupofdice cupofdice   70 2009-10-25 22:28 .directory

Edit: I installed XP in virtualbox, and after a lot of b****ing with Vbox and user groups and usbs, I am now taking my files from my ext hd onto my XP and will move them to my internal hd that way.

---

### Post by zhongfu on 2011-10-24
> **hxcgrunger said:**
> I've got the same problem. turned on my computer this morning and my 500gb WD USB NTFS HDD has almost all of the files missing. All the files left visible add up to ~250GB while my system tells me that 454GB is being used. I have checked for hidden files (.<filename>) and yielded nothing. I never had any mounting trouble with it though. However, possibly the weirdest thing is that if I go to /media/disk/ it shows /downloads /images and /system volume information, though if I go to /media/disk/music/ it shows all the sub-folders within my music folder located on the main drive. :confused: any explanation woulld be appreciated.
Well...
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

---

