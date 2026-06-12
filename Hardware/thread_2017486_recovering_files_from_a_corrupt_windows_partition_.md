---
title: "recovering files from a corrupt windows partition (bad sector)"
date: 2012-07-05
forum: Hardware
---

### Post by thelahana on 2012-07-05
Hi,
Recently my win7 installation crashed due to bad sectors on the drive and it wouldnt boot. I booted the pc by using a ubuntu 11.10 live USB to recover my files. My disk has two partitions, one is for music and films named data and the other is for the windows installation named OS. In ubuntu, i was able to access the DATA partition without any trouble and i backed them up. But the OS partition is unmountable and i need to recover some files from OS as well. I tried force mounting it but to no avail. Im pretty new to ubuntu and I would very much appreciate any help. 

One method i tried:
```

sudo /bin/bash
mkdir /media/disk
mount -t ntfs-3g /dev/sda1 /media/disk -o force
```

Thanks

---

### Post by ahallubuntu on 2012-07-05
Check the S.M.A.R.T. status of the drive.  What are you really dealing with in terms of hard drive failure?  Try the Parted Magic Linux CD (google for it) - boot that and check SmartControl and see what you get.  (You can also use Parted Magic for mounting partitions and recovering files.)  In Ubuntu, you could install GSmartControl to get the same thing.

Look for Attributes that are highlighted in red in SmartControl.

If you have hundreds of bad sectors, you may have a tough road ahead.  If you have just one pending sector error, I'd probably run chkdsk /f by booting a Windows 7 DVD on it first.

---

### Post by thelahana on 2012-07-05
Disk Utility in Ubuntu showed 25 bad sectors. I will try your advice and post the outcomes.

---

### Post by msammels on 2012-07-05
As ahallubuntu suggested I would boot into the Windows 7 DVD first and run:

```
chdsk /f
```

After you have finished with S.M.A.R.T. however, your hard drive may be on its way out.

---

### Post by thelahana on 2012-07-05
I tried running a cmd screen with a recovery usb stick:
```
chkdsk /f 
```
returned:
```

The type of the filesystem is NTFS
Cannot lock current drive
Windows cannot run disk checking on this volume because it is write protected

```

```
chkdsk /f C:
```
returned:
```

Volume label is System Reserved
256 file records processed
0 bad sectors

```

This was a 170GB partition with around 30GB empty space and drive name was OS

I tried
```
dir C:
```
returned:
```

Volume in drive C is System Reserved
Volume serial number is A262-4E3B
Directory of C:\
File not found

```

while 
```
dir D:
```
returns normal resuslts.

In the Windows 7 installation window i couldnt even reach the recovery options, it would only show the cursor on windows background. I tried "install now" option and that wont even load. I then tried the USB stick on my roommates PC and it worked wonders, all the codes returning expected outputs.

I'm in a very bad situation right now and I would greatly appreciate any help.

Thanks in advance.

---

### Post by christyni on 2013-02-08
Hi friend,

Just relax; it is possible to recover files from hard drive after crash having bad sectors by making use of best file recovery tool. Few days back, when I was wondering [how to restore files on Windows 7]("http://www.filerecoverytools.org/windows-7.html"), I tried this tool which helped me to get back all my lost files. This software also recovers files lost due to virus attack, formatting, accidental deletion etc. Just click here to [download]("http://www.filerecoverytools.org/download/filerecoverytools-windows.exe") and try the software.

Best of luck,
Christin

---

### Post by Mark Phelps on 2013-02-08
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

