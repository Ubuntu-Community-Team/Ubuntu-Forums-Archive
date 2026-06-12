---
title: "windws cant acess partition"
date: 2008-08-04
forum: General Help
---

### Post by antstu on 2008-08-04
Hi, sorry if this has been posted somewhere else but after looking for 2hrs i have to ask for help:


I had 3 NTFS partitions on my HDD: C: was vista, D: was Data and T: was recovery from HP.

I made D smaller to install Ubuntu, which went fine. Both systems are able to start and work ok, except that Vista can't find D anymore while Ubuntu can(even use the files on it)

In Windows management console looks like this(sorry for the german:):
[IMG]http://i36.tinypic.com/2z7lyj4.gif[/IMG]

I cannot assign a letter or modify the former D partition anyhow.
what can i do to use it again in windows?

forgot to say: in drive management this former D partition only appears in this lower pane(picture above) but not in the listing above. there only C, T and the linux partition appear.

---

### Post by cariboo on 2008-08-04
If you want to get rid of the partition, just right click on it and select delete. Windows can not read any file systems other then the ones microsoft produces.  You can use a program like this:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

or this:

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/) 

to access your files on an ext3 formatted partition.

Jim

---

### Post by antstu on 2008-08-04
hi,

no i dont want to get rid of it. i want the D partition to have a drive letter again so i can access it on windows....as mentioned i can access it perfectly in linux.
I know if i right-click the letter-less partition theres an option to do it but it doesn't work. it seemst to have sth to do with the fact that the drive doesn't show up in the list above in drive management.

---

### Post by x1a4 on 2008-08-04
Hi,
If the file system is ext2 use FS-Driver, if ext3 use the Linux Reader (see cariboo907's post) otherwise contact microsmeg and tell them to add support for other file systems.

---

### Post by mc4man on 2008-08-05
What does the 'partition' show from the linux side? It's probably still ntfs. Did you resize it in vista or from linux?, if from linux your partition table in vista is now incorrect.

---

### Post by antstu on 2008-08-05
the file system should still be NTFS since it was created by vista long before i installed ubuntu. (dual system)

C, D and T are all ntfs, but since i installed ubuntu windows cant "see" D anymore(see picture i posted). it has no drive letter and i cant assign one to it in drive management in windows.
D was not created by linux thus no ext2 or 3. 

It is accessible through ubuntu though and the files can be read.
but i want them to be accessible in vista again.

---

### Post by antstu on 2008-08-05
I resized D to free up space for ubuntu but i did it in vista already.

ubuntu states that it is a NTFS drive

---

### Post by antstu on 2008-08-05
please guys, I'm running out of ideas. 

Can i somehow restore my partition table so it works for windows again. 

at work it is more important than ubuntu so i don't care that much if i lose linux. i cant try it another time. 

thanks

---

### Post by x1a4 on 2008-08-05
Remove the Linux file system and format it as NTFS.  Or, you can format it as FAT32, which is visible by both Linux and Windows.  Although Linux will not run on a FAT file system.

---

### Post by antstu on 2008-08-05
i would really like to keep my files on that drive. 
ant it is ntfs, thats at least what ubuntu's drive manager says.

or do you mean i should delete the linux-partition to get back access to my D?

if i get rid of ubuntu now i cant access my files on d.

---

### Post by antstu on 2008-08-05
I ran TestDisk to see if I can do sth and it shows me this:

[IMG]http://i33.tinypic.com/2467sli.gif[/IMG]

1 is C, where Vista is and it works fine
2 is the lost drive I want to have back
3 is my T drive with HP-Recovery data, it works fine
4 and 5 are for Linux


So it is there but Windows lost the drive letter and can't access it anymore. Ubuntu can mount it without problems which is great but not of useful if i want to use both systems.

Please give me some advice.

---

### Post by mc4man on 2008-08-05
> do you mean i should delete the linux-partition to get back access to my D
Absolutely don't do that, atm it's your only access to 'lost partition' and if you don't restore vista's bootloader then you'll have nada.

If you install gparted from synaptic you could run it and post screen like you did from disk management in earlier post.
What's strange is in the your first post it shows 4 primary partitions and 659mb free space (unusable), and no linux swap.
In the testdisk it shows 3 primary and 1 extended with a logical (linux)


how much do you need the recovery partition? (do you have a vista disk?)

how much space would you need to copy the files you want to save?

Out of curiosity when you installed ubuntu did you get a warning about having no swap?

---

### Post by antstu on 2008-08-05
hi thanks for the quick reply,
i disabled swapping for ubuntu in gparted, thats the free space
gparted also shows the lost partition as NTFS and as mentioned, ubuntu can mount it. i would need about 70GB to backup D, i already did it with important stuff, but i hoped it would be the last thing to do.
dont have a recovery disk. i could burn one though. just need to find out how.
there was however a problem during installation of ubuntu....i wasnt in front of the screen all the time but when i came back the screen was black with white lines of error messages running and numbers counting up 

i resized D to free up space for ubuntu in win already but maybe it took more than i wanted it to have.

---

### Post by mc4man on 2008-08-06
as per last com 
1st. shows my first drive (xp, gutsy), 2nd my 2nd drive (hardy)
The advantage of ending on an extended is you can make multiple logical drives and create/delete at will with no impact on the Os's vs. being locked in at 4 primaries

---

### Post by antstu on 2008-08-29
unbelievably my patition just appeared again in windows. as good as new. i didnt do anything cause i wanted to wait until i have an external drive to backup.

---

