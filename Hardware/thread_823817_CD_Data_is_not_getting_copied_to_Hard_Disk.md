---
title: "CD Data is not getting copied to Hard Disk"
date: 2008-06-09
forum: Hardware
---

### Post by gpt.ankur on 2008-06-09
hi,

I have recently installed ubuntu 8.04. Whenevr i try to copy any CD or DVD to my hard disk i get error saying 
"there was an error copying the file into /media/Data/mpegav.
Details:
Error reading from file: Input/output error"

Here Data is my mounted windows drive. as i have dual OS with windows vista i tried to copy same disc in windows and it gets copied without giving any error.so i think there has to be some problem with my linux installation only.

Can anyone tell me what can be the possible cause for this.

Thankx in advance.
Ankur

---

### Post by pytheas22 on 2008-06-09
It could be a problem with permissions.  Try copying as root (if you don't know how, ask).

You could also try copying to somewhere on your Ubuntu partition first (e.g. your desktop) and then from there copy over to the Windows partition.

---

### Post by gpt.ankur on 2008-06-09
Hi,

I tried your suggestion "copying using root user access on my user desktop(linux) partition."

but still i am having the same problem.

---

### Post by pytheas22 on 2008-06-09
Can you copy any files (not just from a CD, but from anywhere on your hard drive) into the Windows partition when it's mounted under Ubuntu?

---

### Post by gpt.ankur on 2008-06-09
yes....i am able to copy from windows partition to linux ,from linux to windows partition,linux/windows partition to external hard disk,external hard disk to windows/linux partition....only when i have to copy from cd/dvd i am facing this issue.

---

### Post by gpt.ankur on 2008-06-09
As i was trying to figure out more specific problem....i found out most of the cd/dvd are movies disk.which was not even playing with vlc/mplayer. but when i tried to copy from data cd i was able to copy.

so can anyone help me with how can i copy any movie cd/dvd to hard disk in linux.

---

### Post by pytheas22 on 2008-06-09
I assume that the disks are encrypted, which explains why Ubuntu can't play them.  You have to install the software to deal with protected disks (for philosophical and legal reasons Ubuntu doesn't include this by default):
```

sudo apt-get install ubuntu-restricted-extras
```

Then see if you can copy.  If it still doesn't work, please give more information on how you're trying to copy...are you exploring the CD in Nautilus (the graphical file browser) and trying to drag and drop files onto the hard drive?

---

### Post by gpt.ankur on 2008-06-10
i have installed ubuntu-restricted-extras but still i am not able to copy/play.

for copying i am exploring the CD in Nautilus copy with right click then going to desktop and pasting with right click. also i tried copying with cp command in terminal but i am getting same error only.

---

### Post by pytheas22 on 2008-06-10
What if you copy a file from the CD to your Ubuntu desktop, and then from your desktop, you copy that same file over to the Windows partition?  In other words, it would be something like (from terminal):
```

cp /media/cdrom0/file ~/Desktop/file
cp ~/Desktop/file /media/disk
```

this would work, right?

---

### Post by gpt.ankur on 2008-06-10
i am already trying the same way :(.

this was not working.....

i am currently updating my linux system.might be that can help with this.

also i am reinstalling restricted-extra package.

will post here after that the if the problem gets resolved.

---

### Post by Takmadeus on 2008-06-10
I have exactly the same problem..... which hints me that it is not the drive, but a bug in ubuntu itself.... plus I tried other live distros and they did not have this problem :(

[http://ubuntuforums.org/showthread.php?p=5157617](http://ubuntuforums.org/showthread.php?p=5157617)

---

### Post by pytheas22 on 2008-06-11
Takmadeus,

Can you copy data from a CD to your Linux partition, and then from the Linux partition to the Windows partition?  I think that the other poster is saying he can't do that, although he can copy other files from the Linux partition to the Windows partition without a problem.  If this is the case for both of you, then it points to some characteristic of the files on the CD that prevents them from being copied, not the fact that you're copying from a CD.  Can you list the files on the CD that you're trying to copy?  e.g. do:
```

ls -al /media/cdrom0
```

(or whichever name your CD is assigned; it may not be cdrom0).

---

### Post by gpt.ankur on 2008-06-11
Hi,

after reinstalling restricted extras...nd restarting my system i am able to copy from all the DVD's i tried.i don't have cd on which i originally tried(as that was of my friends which i returned back to him). but i suppose there should not be any problem now coz i tried with 4-5 dvd's and are are getting copied.

CD which i was not able to copy was a VIDEO CD  which contains mpegav folder. this folder was the one i was trying to copy.

Thankx to pytheas22 for valuable help.

---

### Post by Takmadeus on 2008-06-18
well.... i tried fully reinstalling ubuntu and got the same thing again, tried gpt.ankur's method (reinstalling restricted extras) but I had no luck whatsoever :(

---

### Post by Takmadeus on 2008-06-18
Tried reinstalling ubuntu-restricted-extras but still no luck.... have the same problem even after doing a full reinstall. Weird thing is that windows and dreamlinux do not show this problem, so it must be something happening in ubuntu.

Gosh, this is frustating...

---

### Post by Takmadeus on 2008-06-18
Tried reinstalling ubuntu-restricted-extras but still no luck.... have the same problem even after doing a full reinstall. Weird thing is that windows and dreamlinux do not show this problem, so it must be something happening in ubuntu.

Gosh, this is frustating...

---

### Post by pytheas22 on 2008-06-18
Takmadeus,

Sorry to hear you're still having trouble.  Tell me please whether or not you're able to:

1. copy data from your Ubuntu partition on your hard disk to your Windows partition (i.e. no CD involved).

2. copy data from a CD to your Ubuntu partition (i.e. no Windows partition involved).

That will help me figure out what's wrong.

---

### Post by Takmadeus on 2008-06-19
Number 2 would be it....

I hope you can help me, this inability to copy from dvds is very annoying :(

---

### Post by pytheas22 on 2008-06-19
> Number 2 would be it....

Alright, so then you CANNOT copy from your Ubuntu hard drive partition to your Windows partition?

Also, can you watch DVDs in Ubuntu?

It might be the case that the DVD is copyright-protected and therefore is trying to prevent you from copying data.  You could try installing dvdrip:
```

sudo apt-get install dvdrip
```

and see if you can pull the video off that way.

---

### Post by Takmadeus on 2008-06-20
no no no, I cannot copy from dvd to hard disk

copying from ubuntu to windows is fine.

Videos are simple avi or wma files, not movie discs.

Could be a faulty derive? how could I find that out in windows?

---

### Post by pytheas22 on 2008-06-20
> Could be a faulty derive? how could I find that out in windows?

I guess just see if you can browse the DVD in Windows and copy files from it.

Can you watch DVDs in Ubuntu, and can you see your files on the DVD?  If so, then it's not likely that the drive is bad, although it's still possible.  But if you have ubuntu-restricted-modules installed, you should be able at least to watch DVDs.

---

### Post by keiser_soze on 2008-07-31
> **pytheas22 said:**
> I guess just see if you can browse the DVD in Windows and copy files from it.

Can you watch DVDs in Ubuntu, and can you see your files on the DVD?  If so, then it's not likely that the drive is bad, although it's still possible.  But if you have ubuntu-restricted-modules installed, you should be able at least to watch DVDs.
i have same problem

i cannot copy from my dvd writer to my ubuntu partition. dvd or cd same problem. 

i wanna burn and same problem again, input/output error. 

how can i do that?? please help..

---

### Post by kdorf on 2008-07-31
Follow the instructions on [this page]("https://help.ubuntu.com/community/Medibuntu"). There is a section on playing DVDs if you scroll down far enough. Once you have done that, you should be good to go.

---

### Post by milesinnz on 2008-08-11
pretty sure I have the same problem. crazy, if i run dvdisaster it reads though the whole dvd with no errors - so can't be DVD/CD drive, must be something to do with the AVI file itself?

my dvd with one avi file on was created from a windows system. it fails approx 20% of the way through.

---

### Post by cioccolato on 2008-08-15
I have the same problem... I cannot read DVD encrypted or not encrypted. In Windows there are no problems. :(

---

### Post by eumetaxas on 2008-08-15
Hi!
Kind Have the same problems.
Burned a DVD disc with **avi movies** at a friend's windows machine  - checked there and works fine.
in ubuntu and hardy i can browse the dvd ok but i can only play some parts from some of the movies and when tried to copy too my hard disk got the **Input/output error**.
thanx in advance for your help

---

### Post by Takmadeus on 2008-08-16
Don't worry.... I filed a bug in Launchpad. now, you could join and report the bug so it gets more attention :)

Here's the address

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/253473](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/253473)

Help me help us :)

---

### Post by cioccolato on 2008-08-16
there is already a bug report open: see here:
[https://bugs.launchpad.net/bugs/228624](https://bugs.launchpad.net/bugs/228624)

---

### Post by Takmadeus on 2008-08-16
SOLVED! after digging in launchpad, I found that:

In GRUB menu you press "e"

Add this line to the end of the boot options (the ones that end with ro quiet splash)

    all_generic_ide=1

Boot and it will all be fixed

Note: this works in most configurations with this problem, yet there are still some that won't be fixed by this

---

### Post by eumetaxas on 2008-08-20
thanx for the post but unfortunately did not work with me,
thanx anyway!

---

### Post by Takmadeus on 2008-08-20
I hope you find the solution soon ;)

---

### Post by a.dehqan on 2008-11-21
In The Name Of God
hello

I'll be so thankfull guide me
I have the same problem with copying .DAT files from video cd to my hard disk (both ubuntu and windows partitions).
And yet i have problem .
But i can copy e.g mp3 files from cd to my desktop .
8.04 hardy

regards dehqan

---

### Post by pytheas22 on 2008-11-21
a.dehqan: can you copy the .dat files under Windows?  Does this problem occur with every CD or have you only tried one?

Unless the copying works under Windows, I'd suspect that the video CD that you're copying from is encrypted, or at least the .dat files on it are.

---

### Post by a.dehqan on 2008-11-22
In The Name Of GOd
Hello

Thanks alot for you'r attention .
CDs are ok and they are not corrupted .
Other VCDs are tested .
package ubuntu-restricted-extras is installed.
Yes.windows already could copy this files .
and CDROM is ok because there is not anyproblem with other CDs .

regards dehqan

---

### Post by pytheas22 on 2008-11-22
a.dehqan: can you try copying from the command-line and post any error messages that you get?

To copy, you should first open a terminal and type:
```

cd /media/cdrom0
```

(Depending on how many CD drives you have and how they are mounted, you may need to replace 'cdrom0' above with 'cdrom1' or 'cdrom2', etc.  If you can't figure it out, let me know.)

Then, to see a list of the files on your CD, type:
```

ls
```

To copy a file from the CD to your hard disk, you would use a command like:

```
cp filename destination
```

So for example, if you wanted to copy a file named 'video.dat' to your desktop, you would type:
```

cp video.dat ~/Desktop
```

I know this may be confusing if you've never used the command line before, so don't hesitate to ask more questions if you don't understand these commands.  It would be very useful to see what the command line says when you try to copy these files, however.

---

