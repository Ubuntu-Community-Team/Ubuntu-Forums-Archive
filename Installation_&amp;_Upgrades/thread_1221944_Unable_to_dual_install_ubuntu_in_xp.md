---
title: "Unable to dual install ubuntu in xp"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by rishi saxena on 2009-07-24
hi friends,
i am new to this forum and trying to install ubuntu 8.04 version on my laptop first time.My model is -hp dv5 1102 TU using wubi.

i have xp installed in my "C" drieve ad i want to install ubuntu in my "D" drive.It starts well copies files from cv and restarts.
When my pc boots it give me two option to choose from xp or ubuntu
but when i choose ubuntu it shows me loading for few minutes and then gave this error-

/************************************************** *********
udevd-event[1559]: run_program: '/sbin/modprobe'
[26.514655] SGI XFS with ACLS,security attributes,realtime,large block numbers, no debug enabled.
[26.514652]SGI XFS Quota Management subsystem
[26.520598]JFS: nTxBlock = 8192, nTxLock = 65536
(initramfs)
************************************************** ************/

when i tried to run it with live cd it gave me the same error as well but i have seen this forum threads and lot of guys have installed ubuntu in my HP model .

plz someone give solution of this problem.

Thanks

---

### Post by Ratscallion on 2009-07-24
You're installing a previous version of Ubuntu. Try downloading and installing 9.04 (the latest version).. However, that does look as if it's something about your HardDrive... How much space have you got and what did you allocate for the installation?

---

### Post by jerrrys on 2009-07-24
8.04 LTS is supported to 2011, even though some call it old, its ubuntu's highly stable version.  that being said...

you need to get the live cd working first before moving on.  you may be dealing with a bad burn.  did you burn at low speed(4 to 6x)?  did you do a checksum/check cd to verify?

---

### Post by Ratscallion on 2009-07-24
True, I do agree it's an LTS, but it hasn't got the latest updates (like latest driver things ie cups)

---

### Post by raymondh on 2009-07-24
I think OP's dilemna is wubi-related and not the ubuntu iso file.

1.  Back-up your files.
2.  Try to defrag windows first.
3.  Run the CD installer again, making sure you allocate more than 5GB.

See [wubi guide]("https://wiki.ubuntu.com/WubiGuide#Cannot%20access%20the%20CD") for possible tips/troubleshooting.  

What version WUBI are you using .... the newest?

---

### Post by jerrrys on 2009-07-24
maybe [raymondhenson]("http://ubuntuforums.org/member.php?u=769495"), but he did say he could not run the live cd and...

your right [Ratscallion]("http://ubuntuforums.org/member.php?u=736316")

---

### Post by Ratscallion on 2009-07-25
Yeah... he did say that it was an attempted partition, not wubi.

---

### Post by rishi saxena on 2009-07-27
hi guys
thanks for ur views.
Now i have taken new kubuntu 9.04 cd to boot it live and
now this this it gets booted i think ubuntu 8 was having 
old drivers.

My DV5 laptop came with preinstalled vista which i removed it and intalled xp.
Now i have 4 drives.
When i tried to install kubuntu on my D:  partition after sucessfully  reconizing my hard disk it showed me 4 options

**some 7.8 mb of unpartitioned sapce
1.something/dev1/  30GB(MY XP is there in this partition)
2.something/dev2/  10GB(FRee for Kubuntu)
3.something/dev3/  100GB(DATA)
4.something/dev4/  100GB(DATA)

i choose specifiy partition manually and choose dev2.It was by defayult showing "do not use this partition" which i changed to use this partion and i specified file format as NTFS cause all my partitions were NTFS but after that i was not going forward showing me error that ROOT directory is not defined.

So i canceled my setup and restarted me pc just to find out that now my xp is not booting and showing me an error that i have some file missing.

Then i again restarted my pc from live cd of kubutu which showed all my drives BUT in middle of this LIGHT gets disconnected and my laptop which was running on live cd restarted.when i again booted it from live cd i came to know that it was not sowing my partitions and throwing error saying that i have some kind of read/write sata error in my hd and i have to manully solve it by booting in xp and runnnig command fdisk/f.

But the problem is that now my laptop is not booting from my xp cd.i am stuck in middle of nothing.

what i do plzzzzzzz help me i am unable to do anything.:cry:
Sorry for this long post.:confused:

---

### Post by Ratscallion on 2009-07-27
First of all, watch your spelling, please. Secondly, can you boot into Safe Mode? You could then go for the chkdsk /f in Safe Mode (or tell it to do it at boot following the on screen instructions. Command Prompt (run -> cmd) and type in there chkdsk /f. If you've done all this and still no change, then try a System restore.

---

### Post by davidw19125 on 2009-07-27
> **rishi saxena said:**
> hi friends,
i am new to this forum and trying to install ubuntu 8.04 version on my laptop first time.My model is -hp dv5 1102 TU using wubi.

i have xp installed in my "C" drieve ad i want to install ubuntu in my "D" drive.It starts well copies files from cv and restarts.
When my pc boots it give me two option to choose from xp or ubuntu
but when i choose ubuntu it shows me loading for few minutes and then gave this error-

/************************************************** *********
udevd-event[1559]: run_program: '/sbin/modprobe'
[26.514655] SGI XFS with ACLS,security attributes,realtime,large block numbers, no debug enabled.
[26.514652]SGI XFS Quota Management subsystem
[26.520598]JFS: nTxBlock = 8192, nTxLock = 65536
(initramfs)
************************************************** ************/

when i tried to run it with live cd it gave me the same error as well but i have seen this forum threads and lot of guys have installed ubuntu in my HP model .

plz someone give solution of this problem.

Thanks
Hi I'm new to this OS but I think what your problem is you installed the software to the wrong place D drive on windows is were all of your back up files are to do a reinstall of windows xp and you don't want to ever save anything to d drive.
 What you want to do when you install the Ubuntu is install it to C drive first start windows then when windows is running at your desktop put the ubuntu disk in the cd drive. then tell it to install it to run inside windows.
 But first I try to get the ubuntu software off the D drive before you do the install good luck.

                                                                                                                        david19125

---

### Post by Ratscallion on 2009-07-27
> **davidw19125 said:**
> Hi I'm new to this OS but I think what your problem is you installed the software to the wrong place D drive on windows is were all of your back up files are to do a reinstall of windows xp and you don't want to ever save anything to d drive.
 What you want to do when you install the Ubuntu is install it to C drive first start windows then when windows is running at your desktop put the ubuntu disk in the cd drive. then tell it to install it to run inside windows.
 But first I try to get the ubuntu software off the D drive before you do the install good luck.

                                                                                                                        david19125

That's Wubi!  The Windows based UBuntu Installer, or Wubi for short. Just download Wubi from [http://wubi.sourceforge.net](http://wubi.sourceforge.net) and put that, and the iso, in the same folder. Or, if you have a CD, put that in while Windows is running.

---

### Post by rishi saxena on 2009-07-29
> 
My DV5 laptop came with preinstalled vista which i removed it and intalled xp.
Now i have 4 drives.
When i tried to install kubuntu on my D: partition after sucessfully reconizing my hard disk it showed me 4 options

**some 7.8 mb of unpartitioned sapce
1.something/dev1/ 30GB(MY XP is there in this partition)
2.something/dev2/ 10GB(FRee for Kubuntu)
3.something/dev3/ 100GB(DATA)
4.something/dev4/ 100GB(DATA)

i choose specifiy partition manually and choose dev2.It was by defayult showing "do not use this partition" which i changed to use this partion and i specified file format as NTFS cause all my partitions were NTFS but after that i was not going forward showing me error that ROOT directory is not defined.

So i canceled my setup and restarted me pc just to find out that now my xp is not booting and showing me an error that i have some file missing.

Then i again restarted my pc from live cd of kubutu which showed all my drives BUT in middle of this LIGHT gets disconnected and my laptop which was running on live cd restarted.when i again booted it from live cd i came to know that it was not sowing my partitions and throwing error saying that i have some kind of read/write sata error in my hd and i have to manully solve it by booting in xp and runnnig command fdisk/f.

But the problem is that now my laptop is not booting from my xp cd.i am stuck in middle of nothing.

what i do plzzzzzzz help me i am unable to do anything.
Sorry for this long post.


hi friends

i cannot boot in safe mode cause it is not recognizing my OS and saying no OS to boot.And i dont want to install KUBUNTU which is not showing my partitions (which it was showing before crashing while runningkubuntu from live cd)instead showing one complete physical partition ans showing errors in drive.

How can i install xp and get back my partitions back????:confused:
So that this time i can install kubuntu inside windows using wubi.

i don't want to loose my data on my drive.

plz help mp:(

---

