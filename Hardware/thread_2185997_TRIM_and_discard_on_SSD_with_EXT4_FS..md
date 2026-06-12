---
title: "TRIM and discard on SSD with EXT4 FS."
date: 2013-11-05
forum: Hardware
---

### Post by alfredo.marchini on 2013-11-05
Hi all,
I have a very strange situation with my laptop.
My Laptop is an Asus N56VZ with 16GB RAM and 2 onboard HD:

1- Kingston SH103S3120G (SSD 120GB) - sda
2- ST750LX003-1AC154 (HYBRID 750GB) - sdb

I use UbuntuGnome 13.10 with kernel 3.11.0-12-generic amd64.
Inside SSD I installed OS so I mount root fs (/) on /dev/sda.
Inside HDD I mounted /home, /var, swap (Sometimes I need it).

In fstab, for / mountpoint, I add discard option since I bought and installed it, but when I do fstrim -v / it tells me that trimmed about 21GB... :confused:
Why if I setted discard option? 

I attach image of my sda partition table.
As you can see I have also a windows 7 x64 installed.
Thank you.
Bye[ATTACH=CONFIG]247586[/ATTACH]

---

### Post by oldfred on 2013-11-05
Is BIOS in AHCI mode? I think that has to be for trim to work. Windows 7 may need a driver installed first if it is not in AHCI mode and you change to it.

I changed from discard to fstrim in a cron job.
 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

 Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

---

### Post by alfredo.marchini on 2013-11-05
Hi,
the bios tells me that i use AHCI, 
following the links, here's the output:

- sudo hdparm -I /dev/sda | grep "TRIM supported"

*	Data Set Management TRIM supported (limit 1 block)

- my fstab row is this:

UUID=a960f078-a3fd-4a99-9d65-8f0ed45a85f2               /               ext4            errors=remount-ro,noatime,nodiratime,discard    0       1

Could it be that I added discard at the end of options instead of the beginning like it shows the link??? but If I cat /proc/mounts I see discard in / mountpoint...
The last link is very useful, I try the example and the TRIM doesn't work.

---

### Post by oldfred on 2013-11-05
I do not think order matters.

I have seen this as a suggested set of options.
 noatime,discard,errors=remount-ro
or this:
noatime,discard,data=writeback,errors=remount-ro

See comments at end of this:
How to Tweak Your SSD in Ubuntu for Better Performance
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
See comment: There&#8217;s no reason to use BOTH noatime and nodiratime, using noatime implies nodiratime.

---

### Post by alfredo.marchini on 2013-11-05
Hi,
I made other tests and nothing changed, neither with the help of your links.
Discard is not working.
Fstrim is strange: first time I run it tells me 21GB trimmed, the second time, before rebooting os 0 bytes trimmed; immiediately after reboot it trims exactly the same 21GB as the first time.
I think there are problems with the firmware of the ssd, I searched for upgrade but I don't found anything.

---

### Post by oldfred on 2013-11-05
My SSD is older now or about 2 years and was a Microcenter house brand so not the top of the line model.

It is 64GB with 2 / (root) partitions of about 27GB.

This is from my daily log.

*** Sun, 03 Nov 2013 07:54:48 -0600 ***
/: 2055827456 bytes were trimmed
*** Mon, 04 Nov 2013 07:51:30 -0600 ***
/: 2920493056 bytes were trimmed
*** Tue, 05 Nov 2013 07:37:31 -0600 ***
/: 3368288256 bytes were trimmed

---

### Post by alfredo.marchini on 2013-11-05
But in your case you launch fstrim once at a day.
If you run it the first time will trim N Gigabytes.
The second time immiediately after the end of the first time will trim 0 bytes.
Immediately after the second time reboot and rerun it: 
How many bytes trimmed... the same N Gigabytes as the first time, forgetting the trimmed data, or 0 bytes again?

---

### Post by oldfred on 2013-11-05
Have not rebooted for a couple of days but regularly reboot as I installed Saucy & Trusty in new partitions on my hard drive. Daily's are about the same for the last month.

If you do not reboot for a day what happens?

I think one of the threads or posts had a user with a SSD that did not write zeros but another char, is something like that confusing fstrim? Or is yours 

       [https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)

---

### Post by alfredo.marchini on 2013-11-06
For me the question is:
why after reboot the ssd firmware forget the sectors on which I made trim before???

Another thing:

I copied a dvd iso inside /root (4.3GB)
sync
fstrim -v / (0 bytes trimmed).
rm -fr /root/iso
sync
fstrim -v / (0 bytes trimmed).

So discard now is working?
No, because if I reboot and rerun fstrim -v / it tells me 21GB trimmed... :confused:

---

### Post by oldfred on 2013-11-06
I do not know, but I see this comment in man fstrim. And perhaps a reboot requires it to reset something??

> fstrim  will  report the same potential discard bytes each time,
              but only sectors which had been written to between the  discards
              would actually be discarded by the storage device.


---

### Post by alfredo.marchini on 2013-11-07
I don't know too...
I wrote a mail to kingston support, explaining about this problem, and linking this thread to them.

---

### Post by alfredo.marchini on 2013-11-26
Hi all,
i received a very strange response from Kingston, they tell me that the ssd firmware is ok, the problem is the ext4 filesystem:

"The fstrim utility will simply ask the filesystem to find and issue discards on unused blocks.  The ext4 filesystem caches this information and as a result will not discard any blocks if run again immediately after running it the first time.  If you reboot, the cached data is lost and the filesystem will again issue discards on all unused blocks. "

??? So the problem is ext4 filesystem? mmm... they refers to write data cache or something else? :confused: :confused: :confused:

---

### Post by bantuvez on 2013-11-26
> **alfredo.marchini said:**
> For me the question is:
why after reboot the ssd firmware forget the sectors on which I made trim before???


Fstrim will always report that every unused block is trimmed after reboot. Exactly how Kingston wrote it to you. Your firmware is forgetting nothing. How TRIM works:

- The OS sends an ATA command (TRIM) to the SSD telling which blocks are unused by the system.
- The SSD firmware knowing what blocks are unused may (or may not) erase those blocks for faster writing.  
- The SSD firmware won't tell the OS whether it has erased those blocks, only that it has received the command.

Fstrim:
- At first run (after every boot) it sends EVERY unused block to the SSD for discarding. The SSD obviously won't re-erase those unused blocks for which it already know's that are empty. On the second or later runs fstrim will only send those blocks for discarding which became unused since the previous run. (Exactly what Kingston wrote to you.) It is not a problem with ext4, it is not the filesystem's job to know about the internal state of the hardware. 

Discard: If you use discard, the OS will always send the TRIM command as soon as a block becomes unused, and only those blocks.

You should check whether TRIM is working for you by following the article what oldfred linked to you ( [http://techgage.com/article/enabling..._under_linux/2]("http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2") ). If it is working, then your SSD is working well. If it does not report zeros after deleting, then you might have a problem.

---

### Post by alfredo.marchini on 2013-11-26
> 
You should check whether TRIM is working for you by following the article what oldfred linked to you ( [http://techgage.com/article/enabling..._under_linux/2](http://techgage.com/article/enabling..._under_linux/2) ). If it is working, then your SSD is working well. If it does not report zeros after deleting, then you might have a problem.


So I have a problem, because the result of the last  hdparm –read-sector 49598792 /dev/sda is the same of the first time.
But I don't know where is the problem...

---

### Post by bantuvez on 2013-11-26
More to add:

I had a system where Fstrim DID report that xxxxxx bytes were trimmed, although I knew that they weren't, because the driver of my SATA controller was/is faulty and won't send the TRIM ATA command to the SSD. (Yes, it is the fault of the SATA controller's driver, nothing to do with the SSD.) The driver DID report that the TRIM command failed, but fstrim still reported that everything went well. So basically fstrim's output is useless in telling whether trim is working or not.

---

### Post by bantuvez on 2013-11-26
> **alfredo.marchini said:**
> So I have a problem, because the result  of the last  hdparm –read-sector 49598792 /dev/sda is the same of the  first time.
But I don't know where is the problem...

Sorry, but I must ask this:

Did you run 

```
hdparm –read-sector 49598792 /dev/sda 
```

? So you run it with the same number as in the article? You have to change the number to the number of the first LBA which was reported to you by

```
hdparm –fibmap testfile
```

Could you please post the full commands and outputs what you run?

---

### Post by alfredo.marchini on 2013-11-26
Kingston gives me more info again:
The test you linked me is faulty because the firmware of my ssd does not trim immediately the data.
The firmware decide to trim with a proprietary alghoritm.
So for Kingston is all ok. Ext4 is ok. Everything is ok. :-k :D
I need to search for laggy someelsewhere... 
because I have a super laptop, but the performance are not always as I expect from an hardware like this...

---

### Post by bantuvez on 2013-11-26
> **alfredo.marchini said:**
> 
The test you linked me is faulty because the firmware of my ssd does not trim immediately the data.
The firmware decide to trim with a proprietary alghoritm.


That's possible. That is why i wrote that the "firmware ... may (or may not) erase those blocks". That test works for most of the SSD's, but some behave differently. (If you don't see any errors about failed ata commands in your syslog, then your SSD must be working well.)

---

