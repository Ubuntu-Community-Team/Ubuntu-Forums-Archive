---
title: "Backup to windows!PLEASE HELP!"
date: 2008-11-18
forum: General Help
---

### Post by m0n3y0n7r335 on 2008-11-18
Ok first off Ubuntu is a great OS i just need more compatibility so i'm returning to windows.

I have a backup of windows stored on a Hammer Drive and im wondering if theres a way to backup to windows also if that cannot be done is there a way to go back to the factory defaults on the computer?if not im screwed over -.- anyways all help is apreciated :)

---

### Post by DGortze380 on 2008-11-18
> **m0n3y0n7r335 said:**
> Ok first off Ubuntu is a great OS i just need more compatibility so i'm returning to windows.

I have a backup of windows stored on a Hammer Drive and im wondering if theres a way to backup to windows also if that cannot be done is there a way to go back to the factory defaults on the computer?if not im screwed over -.- anyways all help is apreciated :)

What are you have compatibility issues with? Maybe we can help. There are very few thing you HAVE to do on Windows.

What do you mean you have a backup? How did you create it? Is is a disk image (.iso), a bit-for-bit copy or the WHOLE drive? Or just a bunch of files?

Do you have a recovery disk?

A Windows Install disk?

A recovery partition that is still intact?

---

### Post by 420shaggy on 2008-11-18
First, is a Hammer Drive a USB thumb drive?  If it is, I believe Windows does not support having an OS installed on removable disks.

  Also, if you want to revert to the factory defaults on the computer (I believe you mean restore Windows and all the drivers, programs etc..) you will need the disks that came with your computer.  So if you have an HP for example, you have to find the Restore disks (or whatever they might be called) and go from there.  If you have lost these disks you might be able to contact your computer's manufacturer and request an additional copy.

---

### Post by m0n3y0n7r335 on 2008-11-18
By hammer drive i mean an 80gig drive that plugs into the USB port when i still have windows i made a backup file and im wondering if i could get windows back from that also my computer didn't come with disks it came with windows vista and only windows vista is it possible for me to get the disks from the manufacture?

---

### Post by DGortze380 on 2008-11-18
> **m0n3y0n7r335 said:**
> By hammer drive i mean an 80gig drive that plugs into the USB port when i still have windows i made a backup file and im wondering if i could get windows back from that also my computer didn't come with disks it came with windows vista and only windows vista is it possible for me to get the disks from the manufacture?

You probably have/had a backup partition.

We still don't know what you mean by 'backup file'. How did you make your 'backup'.

---

### Post by m0n3y0n7r335 on 2008-11-18
oh also i do NOT have a recovery partition i was stupid enough to install w/o it because i heard how so many ppl got double fps on wow i tried it wow barely works...that plus im 13 so try and keep your explanations simple =D ty

---

### Post by m0n3y0n7r335 on 2008-11-18
i made my backup using windows vista backup creater?something like tat lol

---

### Post by m0n3y0n7r335 on 2008-11-18
the recovery drive has a catalog then it says recovery file 1, recovery file 2, recovery file 3,etc

---

### Post by DGortze380 on 2008-11-18
> **m0n3y0n7r335 said:**
> oh also i do NOT have a recovery partition i was stupid enough to install w/o it because i heard how so many ppl got double fps on wow i tried it wow barely works...that plus im 13 so try and keep your explanations simple =D ty

ok. I think you mean you delete every partition on your disk??

Please open a terminal, post the output of df -l

---

### Post by m0n3y0n7r335 on 2008-11-18
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             76066148  29469056  42763584  41% /
varrun                  252932       104    252828   1% /var/run
varlock                 252932         0    252932   0% /var/lock
udev                    252932        52    252880   1% /dev
devshm                  252932        56    252876   1% /dev/shm
lrm                     252932     39780    213152  16% /lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon      76066148  29469056  42763584  41% /home/josh/.gvfs

there you go =)

---

### Post by DGortze380 on 2008-11-18
I think you're out of luck unless you can get a hold of one of these:

1) Recovery Disk from manufacturer 
2) Windows Install Disk


Just to be sure, can you run the following command
sudo apt-get install gparted

Then

sudo gparted

And post a screenshot of what comes up. Don't make any changes yet, just post the screenshot.

---

### Post by m0n3y0n7r335 on 2008-11-19
here is the screenshot 

/home/josh/Desktop/Screenshot.png

---

### Post by m0n3y0n7r335 on 2008-11-19
hmm that didnt seem to work ill attach the screenshot

---

### Post by m0n3y0n7r335 on 2008-11-19
ahh there we go :)

---

### Post by m0n3y0n7r335 on 2008-11-19
also i do have an windows xp install disk my friend loaned it to me and ive got an installation code too so could you run me through the process? ty

---

### Post by m0n3y0n7r335 on 2008-11-19
bump

---

### Post by m0n3y0n7r335 on 2008-11-19
i gave installing the system by myself a shot and the disk said it could not detect a hard drive on your computer please check to see if hard drives are turned on and configurations to hard drive are correct something like that so i tried to run the setup.exe and it says it has an error and must close then i unmounted and remounted and it said something comepletely different

---

### Post by m0n3y0n7r335 on 2008-11-19
ok ive been working for awhile and i cant seem to find the problem some1 please help me!! =(

---

### Post by m0n3y0n7r335 on 2008-11-20
Solved =)

---

