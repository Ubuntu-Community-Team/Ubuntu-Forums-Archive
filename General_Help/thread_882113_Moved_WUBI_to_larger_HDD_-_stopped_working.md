---
title: "Moved WUBI to larger HDD - stopped working"
date: 2008-08-06
forum: General Help
---

### Post by heinz57g on 2008-08-06
installed wubi a few months ago, and was very happy once i had it adjusted, extended, and personalized the way i wanted it to be. including updates, updates, and updates, untill 5 days ago.

took a month or two, but got me right into linux.

now: mirrored the original 120GB HDD into a new 250GB one, with all partitions enlarged proportionally. WIN XP just works fine right from the start, everything was there as before, incl the larger partitions. happy, perfect. easier than i thought it would be (using CASPER 5.0).

UBUNTU also starts, or seems to, but then freezes with UBUNTU sign showing, the bar moving left right left right, and then nothing. it just freezes after about 3 minutes of trying and trying (but HHD access has long stopped).

what goes wrong here? looking at the directories and files from within a WIN file manager shows no obvious difference, everything is there and seems to be the same.

any ideas what to do? new installation is not really an option, to much work went into tweaking it to they way it is (well, should be) now.

any ideas? pls, i am still a unbuntu/linux beginner.

the old HHD is still available. swapping it with the new one, UBUNTU/wubi is back as normal.

greetings   - heinz-

---

### Post by heinz57g on 2008-08-10
is there really nobody around who could tell me what is going wrong here, and why? and how to fix it? do i have to give up UBUNTU just
because of an HDD upgrade?

or is everybody still on holiday? even hints, where to look, who to ask, would help.

greetings      - heinz -

---

### Post by Bora4u on 2008-08-10
Hello Heinz,
it's too easy to solve your problem.
I don't know how you make it with wubi-loader. But i can help you with grub4dos. I am using grub4dos for kubuntu on windows-disk.
1. Download grub4dos
[http://downloads.sourceforge.net/grub4dos/grub4dos-0.4.3.zip?modtime=1192438829&big_mirror=0](http://downloads.sourceforge.net/grub4dos/grub4dos-0.4.3.zip?modtime=1192438829&big_mirror=0)

2.Extract from downloaded grub4dos.zip onyl the file "grldr" to c:\

3.Edit boot.ini on c:\
 in windows-explorer it's hidden file. You must let show "hidden-files" and "protected system-files"
You must make boot.ini writeable. >uncheck in write-protect

4.Add in boot.ini > section [operating systems] following line:
C:\grldr="Grub4Dos"

it looks like:
```

.....
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NoExecute=OptIn
C:\grldr="Grub4Dos"
c:\wubildr.mbr="Kubuntu"

```

5.Make a menulist textfile for grub in c:\
menu.lst

6. Search and open your ubuntu menu.lst in:
media:/sdb1/ubuntu/disks/boot/grub      
    >sdb1 is my disk, your disc can be sdb0.
In this menu.lst you find some lines you must copy them in to c:\menu.lst

7. Your c:\menu.lst must like this:

```

color black/cyan yellow/cyan
timeout 10
default 0

title	Ubuntu 8.04.1, kernel 2.6.24-19-generic
root	(hd1,0)/ubuntu/disks
kernel	/boot/vmlinuz-2.6.24-19-generic root=UUID=03F8F1BD1112C814 loop=/ubuntu/disks/root.disk ro quiet splash
initrd	/boot/initrd.img-2.6.24-19-generic

title	Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root	(hd1,0)/ubuntu/disks
kernel	/boot/vmlinuz-2.6.24-19-generic root=UUID=03F8F1BD1112C814 loop=/ubuntu/disks/root.disk ro single
initrd	/boot/initrd.img-2.6.24-19-generic

title Windows NT/2K/XP
fallback 1
find --set-root /ntldr
chainloader /ntldr

title commandline
commandline

title reboot
reboot

```


**You must change** **(hd1,0)** to your harddisk:
(hd0,0) :1. harddisk, 1. partition
(hd0,1) :1. harddisk, 2. partition
...
(hd1,0) :2. harddisk, 1. partition
(hd1,1) :2. harddisk, 2. partition
(hd1,3) :2. harddisk, 3. partition

Wenn your pc booting, you must select now grub4dos then ubuntu.

I installed Kubuntu with wubi on 2.Harddisk 1.partition. Grub4dos ist better then wubiloader (placed on c:\wubildr).

You can load with grub4dos other linux-live distros on your harddisk. 

I hope you understand me. When you can speak german then can i help maybe better.

Edit:
When you want to use wubiloader then you have to deactivate menu.lst . Just rename it to _menu.lst_

---

### Post by heinz57g on 2008-08-11
bora4u, tks a lot, but this to my mind is FAR to complicated. reading, and re-reading
it, i still have no idea what you are talking about.

this is a WIN XP system, so there is no 'hd0,0' or '/sdb1/' here at all.

WUBI is supposed to be packing the entire UBUNTU system into a container file, to
be placed on any reasonably free NTFS partition, like any other XP files. accessible
and startable with a short menu when the computer starts. 

now tell me why this would work on a 160GB, but **NOT** on a 250GB HDD? when absolutly
everything else works after the transfer?

actually, one observation. right when the UBUNTU sign and bar starts appearing, the
working system (on the 160GB HDD) starts heavy HDD activity, reading in files. the new
250GB system does almost nothing from that point on, the HDD is quiet and NOT being 
accessed at all. or so it seems. partitions etc are all same, they were just mirrored.


greetings     - heinz

PS: your english was fine, thats not the problem, but yes, we could exchange mssgs in 
german (PM), but the people who help me also on this side only speak english.

---

### Post by ago on 2008-08-11
Press esc at boot and select rescue mode for a more verbose output, look for errors, also try post the output of the following commands

cat /proc/cmdline
cat /proc/mounts
cat /proc/partitions

---

### Post by heinz57g on 2008-08-11
ago, when and at which point do is issued those CAT commands?

remember that when UBUNTU starts (UNBUNTU screen and left-right-left bar)
nothing goes anymore. i have to restart computer by turning it off completely.

greetings     - heinz -

---

### Post by heinz57g on 2008-08-11
ago, did as follows:

ESC as suggested during UBUNTU boot, up cames a ASCII menu with 8 kernels
to select, from 2.6.24-20 down to -12, each with normal and recovery option.

assumed that the default was the newest -20, so just to humor me i did 
choose -19 (not even recovery), and the machine booted perfectly well.

looked all fine, i did start progs with icons on the desktop, all normal.

then: clicked on the TASKBAR in order to restart, but the entire bar just
vanished, and i found no way to get it back. had to hard-off the computer.

did all that now three times, absolutely reproducable. now i am aware we are
talking about two totally different issues (kernel and vanishing taskbar), but
then one without the other also does not go.

greetings      - heinz -

---

### Post by totya4 on 2008-08-13
> **heinz57g said:**
> installed wubi a few months ago...

Hi!

My english is terrible, sorry. But ur problem is simple, only new UUID is required in menu.lst (and possible correct root lines).

Correct UUID:

Ubuntu installed on ur hdd OK. Set this partition label to (if no label) example "Ubuntu804". After print this msg.

Goto directory where ubuntu installed: ubuntu\disk\boot\grub, and open menu.lst with text editor, select all and copy here (answer msg - with CODE tags - see **#**).

Try:
Boot from UbuntuCD, choice only run (NO INSTALL!!!)
From GUI, start terminal
Type sudo -s
Type blkid /dev/sdxy

where:
x : hard drive
y : partition
if ubuntu installed on first hdd, and first partition, u type:
blkid /dev/sda1
if ubuntu installed on second hdd, and second partition, u type:
blkid /dev/sdb2

if sdxy is correct, u get msg, about:
/dev/sdxy: UUID="674cc633334dd634" LABEL="Ubuntu804" TYPE="ntfs" 

if u want see all sdxy devices, type:
ls -l /dev/disk/by-uuid

if installed drive label is not correct, try other xy values (see "ls -l /dev/disk/by-uuid" command).
Well, if u found correct label, where ubuntu installed, then copy UUID, and paste to any editor, after save to (example) floppy.

Okay, start windows, goto ur installed ubuntu directory, goto: ubuntu\disk\boot\grub

If u edited menu.lst (after ubuntu can't start...), u need original from ur backup (if present...)
Now, and this is very important, try arhive ur menu.lst, example "copy menu.lst menu.lst.00".

Edit menu.lst with text editor.
Change all old UUID to new UUID (if first char is not # in the line) :)
This is only two lines.
Save. I suggest stay linux format (linebreak) in text editor.
Open this modified menu.lst with text editor, select all, and copy here (answer msg - with CODE tags - see **#**).
Restart, choice ubuntu...

Edit:
1.I see answer #3... if present "grldr" and "menu.lst" in "c:\" then delete these files. (No delete anything from ubuntu directory!)
If "C:\grldr="Grub4Dos" line is present in ur boot.ini then delete this line (only this line).

---

### Post by heinz57g on 2008-08-13
totya4, did you not read the two mssgs before yours? it has nothing to
do with what you describe and try to correct. if kernel -19 works just
fine, and kernel -20 does not even start, the reason is somewhere else.

also, we are NOT talking about a UBUNTU installation, but a WUBI
installation, with ubuntu just sitting in a WIN folder.

greetings      - heinz -

---

### Post by totya4 on 2008-08-13
> **heinz57g said:**
> totya4, did you not read the two mssgs before yours? it has nothing to
do with what you describe and try to correct. if kernel -19 works just
fine, and kernel -20 does not even start, the reason is somewhere else.

My answer for ur first post, these method works perfectly for me.
I copy my ubuntu (wubi install) to other drive/partition, and works with my published methods.

> **heinz57g said:**
> also, we are NOT talking about a UBUNTU installation

haha :) u wrote this:

> **heinz57g said:**
> UBUNTU also starts, or seems to, but then freezes with UBUNTU sign showing, the bar moving left right left right, and then nothing. it just freezes after about 3 minutes of trying and trying (but HHD access has long stopped).

No problem, bye :)

---

### Post by heinz57g on 2008-08-13
sorry, maybe i was not clear: not a ubuntu **INSTALLATION** on a
dedicated and entire linux partition, but just a **WUBI** installation
where ubuntu sits in a WIN XP folder only.

and the drives and partions incl all names are the same on the old
160GB working copy as on the new 250GB non-working HDD.

and it **DOES** work using kernel **-19**, **but not -20**. but when
starting normally, -20 is the default, so off it goes. and when
updating, it would also update again to -20 ... and stop working.

greetings      - heinz -

---

### Post by heinz57g on 2008-08-26
actually, the solution was simple and already indicated above:

 - kernel 2.6.24**-20** did not work, but was then the default.

 - kernel 2.6.24**-19**, manually selected, worked fine.

 - kernel 2.6.24**-21**, which it updated to a few days ago,
 - and is **NOW** the default, **again works fine.**

greetings      - heinz -

---

