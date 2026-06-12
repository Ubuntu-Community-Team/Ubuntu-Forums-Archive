---
title: "Dual-boot doesn't work with Windows XP"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by hathiphnath on 2009-04-30
Hi all!

My first post here, if I misplaced the thread, please move it to an appropriate section.

My issue then.

A couple of days ago, I had working Gutsy & XP dual boot (see attachment of partitions below). XP was on sda4. I have no idea why sda3 was listed as boot. sda3 had no OS on it, it was just a data drive.

Anyways, I deleted all partitions but sda4 and installed Jaunty on the free space. Now output looks like this:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9996    80292838+   5  Extended
/dev/sda4   *        9997       14593    36925402+   7  HPFS/NTFS
/dev/sda5               1        9627    77328814+  83  Linux
/dev/sda6            9628        9996     2963961   82  Linux swap / Solaris
```

I added the following lines into menu.lst

```
title	 Windows XP
root	 (hd0,3)
savedefault
makeactive
chainloader	+1
```

Windows boot error: NTLDR is Missing

I used this tutorial: [http://support.microsoft.com/?kbid=318728](http://support.microsoft.com/?kbid=318728)

So, my question: How should I set up my **menu.lst** and **Boot.ini** to make the XP work again?

Thanks! :)

---

### Post by Mark Phelps on 2009-04-30
My guess is that you had the XP loader files installed in sda3 -- which is why, now, XP can't find the files it needs.  Don't know if you can install them in an Extended partition.  Have heard conflicting stories about that.

---

### Post by hathiphnath on 2009-04-30
Uh, I'll explain a bit further... I copied **ntldr** an **ntdetect.com** to c:\ from XP disc and tried to recreate **Boot.ini** as in the tutorial above.

Now that I try to boot up XP, I get an error message that **system32/hal.dll** is missing, but the file totally exists on **sda4**.

I think I have pointed either **menu.lst** or **Boot.ini** to wrong partitions, most likely the **Boot.ini** which I recreated like this:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Professional" /fastdetect
```

I tried using partition(1), partition(2), partition(3) and partition(4) in **Boot.ini** with no success (although the error messages differed).

*Edit:* Oh, and when I installed Jaunty, it claimed that there were no OS's on the drive... but I'm used to living in Windows world and thought not recognising other OS's was normal behaviour, so, I simply proceeded with the install...

---

### Post by Sef on 2009-04-30
Windows needs to be on the first primary partition, not on an extended partition.

---

### Post by hathiphnath on 2009-04-30
> **Sef said:**
> Windows needs to be on the first primary partition, not on an extended partition.
Could you elaborate? And how come it worked with Gutsy then? See the screenshot.

---

### Post by Herman on 2009-04-30
It's safest and simplest to tell people that Windows needs to be located at the start of the hard disk in the first primary partition, and not in some other partition or in an extended partition or somewhere else on the hard disk.
That's the best advice to give most Windows users. Sef is right, generally speaking.

Actually though, if you know what you are doing or you're prepared to mess around a bit, you should be able to boot Windows in any location in any hard disk, and, in any partition number. I have spent a lot of time running various experiments and it works for me, at least in my computers. It should be able to be persuaded to work in most other people's computers too I would hope and imagine . You should even be able to boot Windows in a logical partition (without a primary 'boot' partition), if you know how. 

Try
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)WINDOWS="Microsoft Windows XP Professional" /fastdetect
```As a side note, you can make small edits to your boot.ini file from Ubuntu, but be careful not to make any new lines.
If you make any line breaks (using your carriage return or 'enter' key), that will probably corrupt your boot.ini file, as Windows fails to recognize Linux's style of line breaks.
If you want a new boot.ini file generated automatically for you, you should be able to run bootcfg /rebuild from a Windows recovery console, and while you're there you might as well run fixboot too, just for good measure.

That should work, if not try running CHKDSK /F or CHKDSK /R and see if that helps any.

---

### Post by hathiphnath on 2009-05-02
> **Herman said:**
> Try
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)WINDOWS="Microsoft Windows XP Professional" /fastdetect
```Duh! WINDOWS, not WINNT! Of course!

But it gives me an error message... **Error 23: Error while parsing numbers**

Clueless again. I tried partitions 2 & 3 too just in case, but the same error.

> **Herman said:**
> As a side note, you can make small edits to your boot.ini file from Ubuntu, but be careful not to make any new lines.That's how I created the file :) I copied the text from the Microsoft help page, so, I never created new lines myself.

---

### Post by meierfra. on 2009-05-02
Windows does not count  extended partitions (/dev/sda1), and it only counts partition which really exists (so it does not count /dev/sda2 and /dev/sda3). This makes Windows the first partition. So you need to use 

partition(1)

Also there is a "slash" missing in the last line in boot.ini. So use

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition([COLOR="Red"]1[/COLOR])\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition([COLOR="Red"]1[/COLOR])[COLOR="Red"]\[/COLOR]WINDOWS="Microsoft Windows XP Professional" /fastdetect
```


> Error 23: Error while parsing numbers


That sounds like a typo in "menu.lst". I suggest to use

title	 Windows XP
rootnoverify	 (hd0,3)
chainloader	+1

---

### Post by hathiphnath on 2009-05-03
Hey meierfra!

I owe you a huuuuge cup of coffee, man. Your suggestions totally fixed it! Thanks!

:guitar:

---

