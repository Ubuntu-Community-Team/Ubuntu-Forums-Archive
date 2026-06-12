---
title: "Vista won't let me access a NTFS partition"
date: 2008-09-30
forum: General Help
---

### Post by alej on 2008-09-30
Funny how Vista won't let me access a NTFS partition which I created using Vista sometime back.
 
Funnier still howUbuntu has no problem reading it, copying in it, deleting and so on
 
Yet the funniest is that this bloatware called Vista forces does a chkdsk everytime I boot and at that time it is able to acces de NTFS partition (It even grabs the correct Partition LABEL) but then, once booting is finished, Disk Manager tells me the drive format is RAW hence making it impossible to access...
 
Any idea why this might happen?
 
As for me I'm happier stupid Vista is forcing me to quit it and seriously think about scrapping dual boot alltogether....

---

### Post by prshah on 2008-09-30
> **alej said:**
> Yet the funniest is that this bloatware called Vista forces does a chkdsk everytime I boot and at that time it is able to acces de NTFS partition (It even grabs the correct Partition LABEL) but then, once booting is finished, Disk Manager tells me the drive format is RAW hence making it impossible to access...
 

Open a terminal (Applications-Accessories-Terminal) and post the output of ```
sudo fdisk -l
``` It may be that your NTFS partition type is either wrong or mislabled. Ubuntu will happily open it up anyway if you specify the mount type as ntfs(-3g) but Vista may not be so forgiving.

---

### Post by alej on 2008-10-02
> **prshah said:**
> Open a terminal (Applications-Accessories-Terminal) and post the output of ```
sudo fdisk -l
``` It may be that your NTFS partition type is either wrong or mislabled. Ubuntu will happily open it up anyway if you specify the mount type as ntfs(-3g) but Vista may not be so forgiving.

here it is
alejandro@alekubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006fc9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       14470       14593      996030   83  Linux
/dev/sda2               1       14469   116222211    5  Extended
/dev/sda5            4742       14469    78140128+   7  HPFS/NTFS
/dev/sda6               1        2675    21486843   83  Linux
/dev/sda7            2676        4499    14651248+  83  Linux
/dev/sda8            4500        4741     1943833+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56d2f91c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7724    62037416    7  HPFS/NTFS
/dev/sdb2            7724       13903    49637376    7  HPFS/NTFS
/dev/sdb3           13904       14593     5542425    7  HPFS/NTFS

I believe the partition which doesn't want to be read is /dev/sdb2

Indeed ubuntu has no problem at all opening it... just fidgety Vista won't manage... even though it checks it through before starting up, recognizes the label, yet later through Disk Manager won't show up any of that info..

thanks for your help and interest

---

### Post by alej on 2008-10-02
allright, I've just noticed something curious... (running intrepid ibex at the moment alpha 6 or beta (it is the 2nd of october afteralll))

besides NTFS drives not automounting when ubuntu loads up, once I click on them and they become available, this particular drive shows a message in the open folder window of nautilus which says;

These files are on a Picture CD 


have a feeeling the problem is related with this... 

but I have no idea how to proceed.

any suggestions?

---

### Post by caljohnsmith on 2008-10-02
Maybe you have a problem with your sdb HDD's partition table; it couldn't hurt to check if there is a problem, it will only help. When you are in Ubuntu, first enable all your repositories in System > Prefs > Software Sources, and then download and run testdisk with:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select the sdb HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

---

### Post by alej on 2008-10-03
> **caljohnsmith said:**
> Maybe you have a problem with your sdb HDD's partition table; it couldn't hurt to check if there is a problem, it will only help. When you are in Ubuntu, first enable all your repositories in System > Prefs > Software Sources, and then download and run testdisk with:
```
sudo apt-get install testdisk
sudo testdisk
```After starting testdisk with the above command, choose "no log", select the sdb HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

Here is what I get after a quick check and a further deeper one

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdb - 120 GB / 111 GiB - CHS 14594 255 63

The harddisk (120 GB / 111 GiB) seems too small! (< 125 GB / 117 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  HPFS - NTFS          14592 254 63 15282 254 61   11084849

But I still can't understand why this is happening... and how ubuntu has no problem operating this partition and Vista refuses....

---

### Post by TeXtonyx on 2008-10-03
But I still can't understand why this is happening... and how 
ubuntu has no problem operating this partition and Vista refuses....

TeX: My qualifications: I have the same birthday as Donald Knuth at Stanford. 
In the good old days we had floppy drives. When a floppy drive got
old, then it still might write to the floppy, and read it later, but that
floppy often would not work or be readable on a new precise floppy drive.

I used to write code for webpages and of course test them with both Netscape
Navigator and Internet Explorer. From time to time a webpage would display
properly in one browser but not in the other. I used to say 'bad browser' to
the browser which objected to the code. In hundreds of times, there was only
once that the recalcitrant browser contained an error, rather than my code 
contained an egregious error. The browser that displayed bad code was too
lax in its enforcement of coding syntax. Appearances can be deceiving.

For many years Linux could not write to a NTFS partition without causing
corruption. I think it was just in 2007 that the ntfs3g driver worked well 
enough to be highly reliable but not perfect. Once in awhile I come across
reports that their NTFS drives were corrupted by Linux writing to them 
over a long period of time, like a year. I think it is pretty hard to 
attribute a definite cause over that time period. But in *principle* not
all expressions in one language are translatable to another language 
unless every symbol in one language is contained in the other. That is
why macros and complex equations will never be automatically translated
from Word to OpenOffice. My point is that you can tell which OS isn't 
doing what you want, but you can't tell which OS is at fault, the cause
is as 'subtle as the Lord' (Pais/Einstein). False cause is a major logical 
fallacy, pervasive in Ubuntu interpretation, an example of which is that
Newton gravity works locally, but fails in the larger universal scheme.
There is a brilliant professor who created SysInternals so of course MS
hired him to be a chief scientist. He said the computers problems have
causes but that doesn't mean we necessarily can discover those causes.
This is why computer technicians deserve big bucks in the coming fell times. 
:) Realize the joys of indistinguishability manifest in the unknowable!

---

### Post by caljohnsmith on 2008-10-03
So according to testdisk, you definitely have a problem with that NTFS partition. Do you have any kind of HDD diagnostics CD that came with that HDD? I would definitely run some HDD diagnostics tests on that HDD just to make sure you don't have a failing HDD. If you don't have a CD that came with the HDD, you can downlooad the [Ultimate Boot CD]("http://www.ultimatebootcd.com/") and use that; it has lots of HDD diagnostic programs on it. And in the meantime, I would suggest you back up any important data on that HDD just to play it safe at this point. Let me know how it goes.

---

### Post by TeXtonyx on 2008-10-03
[http://searchenterprisedesktop.techtarget.com/generic/0,295582,sid192_gci1276029,00.html](http://searchenterprisedesktop.techtarget.com/generic/0,295582,sid192_gci1276029,00.html)
"Your data is incredibly important. As such, it is important to have system functions that keep your computer in tip-top shape. Chkdsk is one of the most valuable tools included in Windows XP. Chkdsk scans your hard drive for errors, bad blocks and sectors, and can help determine the general health of your PC. The Chkdsk F function takes Chkdsk a step further, helping you to automatically fix problems on your system."

[http://searchenterprisedesktop.techtarget.com/generic/0,295582,sid192_gci1276030,00.html](http://searchenterprisedesktop.techtarget.com/generic/0,295582,sid192_gci1276030,00.html)
In addition to using the command-line version of Chkdsk, you can run Chkdsk from My Computer or Windows Explorer.

   1. Click Start, and then click Computer.

   2. Right-click the volume you want to check, and then click Properties.

   3. Click the Tools tab, and then click Check Now. ...

TeX: This might fix the problem before resorting to (downloading) a cd, although
UBCD4Win is a highly recommended rescue cd.  Chkdsk can take a few hours to complete.
To correct disk errors from a command line, type:

chkdsk DriveLetter: /f /r
You would substitute the the problematic partition Drive letter assuming it has one.
Click on start -> Acessories then right click "Command Prompt" and choose
"Run as administrator" -> accept the UAC prompt by clicking ok or entering
your password. -> at the prompt type "chkdsk /f" (without the quotes) and
when prompted to run at next reboot type Y and press enter. after that,
simply close the command prompt, and reboot your computer normally (do not
try to run safe mode!) this should allow chkds to run normally on startup.
TeX: The method just above defaults to C:\ so use the correct drive letter.

---

### Post by alej on 2008-10-03
> **TeXtonyx said:**
> [http://searchenterprisedesktop.techtarget.com/generic/0,295582,sid192_gci1276029,00.html](http://searchenterprisedesktop.techtarget.com/generic/0,295582,sid192_gci1276029,00.html)
"Your data is incredibly important. As such, it is important to have system functions that keep your computer in tip-top shape. Chkdsk is one of the most valuable tools included in Windows XP. Chkdsk scans your hard drive for errors, bad blocks and sectors, and can help determine the general health of your PC. The Chkdsk F function takes Chkdsk a step further, helping you to automatically fix problems on your system."

[http://searchenterprisedesktop.techtarget.com/generic/0,295582,sid192_gci1276030,00.html](http://searchenterprisedesktop.techtarget.com/generic/0,295582,sid192_gci1276030,00.html)
In addition to using the command-line version of Chkdsk, you can run Chkdsk from My Computer or Windows Explorer.

   1. Click Start, and then click Computer.

   2. Right-click the volume you want to check, and then click Properties.

   3. Click the Tools tab, and then click Check Now. ...

TeX: This might fix the problem before resorting to (downloading) a cd, although
UBCD is a highly recommended rescue cd.  Chkdsk can take a few hours to complete.
To correct disk errors from a command line, type:

chkdsk DriveLetter: /f /r
You would substitute the the problematic partition Drive letter assuming it has one.
Click on start -> Acessories then right click "Command Prompt" and choose
"Run as administrator" -> accept the UAC prompt by clicking ok or entering
your password. -> at the prompt type "chkdsk /f" (without the quotes) and
when prompted to run at next reboot type Y and press enter. after that,
simply close the command prompt, and reboot your computer normally (do not
try to run safe mode!) this should allow chkds to run normally on startup.
TeX: The method just above defaults to C:\ so use the correct drive letter.

Well, first of all thanks for the literature in your previous post, it was very entertaining yet at times I felt I was loosing touch with reality...... but thanks for the allegory/explanation of why I have such a corruption in my partition.

Considering your second post I just wanted to point out that Vista is doing a chkdsk on that drive everytime I boot it up. Maybe the /f flag will make it more thoroughly and it may even fix something... even though I'm gonna first follow the previously given suggestion (for reasons of order)... I'll let you guys know both results when I get through with them.... i.e. tomorrow morning...

In any case thank you guys for your interest and patience (speciallly with those detailed instructions using Vista which might be clarifying for someone else who might find himself in this situation)

---

### Post by TeXtonyx on 2008-10-03
"Considering your second post I just wanted to point out that Vista is doing a chkdsk on that drive everytime I boot it up. Maybe the /f flag will make it more thoroughly and it may even fix something..."

Yes, the /F stands for fix and without it I don't think chkdsk ever fixes any problems. 
UCBD(4Win) can be complicated and there is a UCBD4Win forum. I'm assuming
that a Windows problem will be best attended to by the repair disk designed for Windows. 
It comes in two flavors.

---

### Post by alej on 2008-10-04
Allright, still no luck at all... 

1st proposed solution: Disk Utilities....  My computer is a damned HP dv9343eu laptop. I say damned because I hate the locked-up HP-Phoenix BIOS which doesn't allow you much versatilty, and because until kernel 2.26.27, it has been a painstaking task to get it work properly with Linux (acceptably the wireless bcm4312 card also played it's share)... but let's get back on track.

The Window Utilities I downloaded from seagate for my Seagate drives is unable to start up (I get a disturbing german written message which closes the utility). So no luck there...

Hence I had to try chkdsk P: /R /R which went all the way through without reporting anything special... It took around 1 hour for a half filled 60 GB disk.... i even rebooted to Vista and went through the chkdsk that popped up

I'm back in step one... Ubuntu reporting the drive is a Picture CD (yet fully able to operate it) while Vista detects the drive, chkdsk reads the drive lable without any problem yet Disk Manager seems unable to do just that... No access in Vista as always...


So now I'm gonna try checking out if booting to the HP_RECOVERY drive has some Disk utility and if not I'll try burning one of the ISO utils you guys name before...

I'll keep you all updated...

Thanks yet again for your time...

EDIT ; yes I did mean to say chkdsk P: /F /R

---

### Post by TeXtonyx on 2008-10-04
"Hence I had to try chkdsk P: /R /R which went all the way through 
without reporting anything special... It took around 1 hour for a 
half filled 60 GB disk.... i even rebooted to Vista and went 
through the chkdsk that popped up."

You are testing to see if we are paying attention, right?! The
switches are /f /r not /r /r. Unlike in Linux I don't think that
the caps matter. I think that it's odd that Vista runs chkdsk
every time. Photo CD I think is a cd with Kodak software. Do you
own any Kodak program that could write to your hard drive? Anyway,
I think it is time to make a backup while Linux can still access
any important files since Vista can't, with Ubuntu. 

Then if it really becomes important to access P: from Vista, you
can delete the partition. Then from Vista you can recreate the
partition from the unallocated space created by the deletion and
then format it and give it a drive letter from Vista. Vista has
no excuse for not reading the partition then. Then copy the files
that you backed up to the newly formatted partition. If somehow
the same problem occurs again, maybe it is one of the files that
has been restored which has odd properties. The backup should
work for data files, images, docs, music etc. This suggestion is
a sort of last resort except for the backup, if all else fails,
and it is critical, rather than convenient, that Vista reads P: 
Good Luck, sorry I don't have a more constructive suggestion.

---

### Post by alej on 2008-10-05
> **TeXtonyx said:**
> 

You are testing to see if we are paying attention, right?! The
switches are /f /r not /r /r.

LOL, so sorry for my carelesness.. I added an edit line to my previous post.... 

> **TeXtonyx said:**
>  Do you
own any Kodak program that could write to your hard drive? 

None.. neither in ubuntu nor in Vista.....   

> **TeXtonyx said:**
>  This suggestion is
a sort of last resort except for the backup, if all else fails,
and it is critical, rather than convenient, that Vista reads P: 
Good Luck, sorry I don't have a more constructive suggestion.

You don't need to be sorry. Thanks ever so much for your suggestions, help and time, it should be me who should say sorry for being such a pain.... Indeed I fear your last suggestion is the inevitable, yet I am intrigued why Ubuntu is detecting that drive as a Picture CD.... I'm thinking of force mounting at the start that drive to see how ubuntu reads its... I'll keep on posting as I go along... 

Yet again, thankyou all for your help... specially considering this is after all a Vista detected problem and not an ubuntu one...

---

### Post by alej on 2008-10-09
allright... edited /etc/fstab by adding the following lines

# /dev/sdb2
UUID=345E7EA35E7E5E14 /media/PERSONAL               ntfs defaults 0       0

needless to say sdb2 now gets properly mounted on start... 

yet when I open it through nautilus, it still has a note saying this is a picture CD... 

Considering I tried checking out if there was a HDD Utility in the HP_RECOVERY partition with no success,  I believe  I've got nothing left to do.... 

Yet I still wonder why nautilus is telling me this is a Picture CD drive.... 

any suggestions?

---

