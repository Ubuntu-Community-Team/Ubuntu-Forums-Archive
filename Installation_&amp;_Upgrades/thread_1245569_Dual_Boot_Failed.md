---
title: "Dual Boot Failed"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by Kinetic_lord on 2009-08-20
Hello,

I recently installed Kubuntu 9.04 on a memory stick on a computer running Windows 7. My problem is that without the stick connected, the computer will not start Windows, and even if i insert the stick, the Vista(Longhorn) Loader is probably damaged and it can not boot Windows. What is the problem and how can i make my Windows boot again? 

I tried "repairing" the computer with Windows 7 Install CD and it did not work. Any way i can bring the old boot loader back? (Except reinstalling the system, my HDD is very fragile because of repeated formats, it might fail).

Thank You!

---

### Post by presence1960 on 2009-08-20
> **Kinetic_lord said:**
> Hello,

I recently installed Kubuntu 9.04 on a memory stick on a computer running Windows 7. My problem is that without the stick connected, the computer will not start Windows, and even if i insert the stick, the Vista(Longhorn) Loader is probably damaged and it can not boot Windows. What is the problem and how can i make my Windows boot again? 

I tried "repairing" the computer with Windows 7 Install CD and it did not work. Any way i can bring the old boot loader back? (Except reinstalling the system, my HDD is very fragile because of repeated formats, it might fail).

Thank You!

formatting your hard disk does not "hurt" it other than the fact you have more "read/write" operations on it. To restore Vista's bootloader boot your Vista install DVD and do [this]("http://ubuntuforums.org/showthread.php?t=1014708"). Boot without the USB stick please.

---

### Post by Bartender on 2009-08-21
> **Kinetic_lord said:**
> my HDD is very fragile because of repeated formats, it might fail

I've never heard of such a thing.  I'd better stop playing with various Linux distros and settle on just one before my HDD gets fragile too

---

### Post by presence1960 on 2009-08-21
> **Bartender said:**
> I've never heard of such a thing.  I'd better stop playing with various Linux distros and settle on just one before my HDD gets fragile too

Then how will you have fun? I have heard that myth before about formatting killing hard disks, but fortunately it is just that a myth. It is circulated mostly among those at the novice level. There is nothing wrong about being a novice, we all start there. More experienced people can set us straight when we have a misconception. So to the poster of that comment no malice is meant, but your statement is untrue.

---

### Post by Penguin Guy on 2009-08-21
Take a look at this topic: [[COLOR="Blue"]MBR Explained[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1244606").

---

### Post by Kinetic_lord on 2009-08-25
Guys, i have not told you that i own a laptop, maybe normal HDD can stand many formattings, but not a laptop's. I did play with a lot of distro's, Windows and OS X all on my poor PC, so... i just hope the warranty will cover it.

By the way, the fixmbr worked. Thank you very much!

---

### Post by presence1960 on 2009-08-25
> **Kinetic_lord said:**
> Guys, i have not told you that i own a laptop, maybe normal HDD can stand many formattings, but not a laptop's. I did play with a lot of distro's, Windows and OS X all on my poor PC, so... i just hope the warranty will cover it.

By the way, the fixmbr worked. Thank you very much!

That is not true, where are you getting this info about formatting?

---

### Post by RabbitWho on 2009-08-25
As I understand it all you're doing is changing a few 1s to 0s and then back again. I don't see how that could do any damage. It's not like re-burning a re-writable cd where every time you do it you're burning a physical change into a very thin film of reflective coating made of.. i dunno.. plastic or something ridiculous like that. 

I mean every time you use your computer you're deleting things and writing over that space again.. That's what defragmentation is about too (as I understand it) 

Anyway I wish I could help you with your problem but maybe I put your mind at ease? 

If someone tells you you're voiding your warranty by doing something like that they're lying and breaking the law!

---

### Post by Sxeptomaniac on 2009-08-25
I must have formatted my old laptop drive around ten times, and it was refurbished when I bought it, so it had probably already been formatted a few times, conservatively.  It was still working great the day it got stolen :cry:  (I miss that T30 sometimes)

Laptop HDDs are made much like their full-size counterparts.  If anything, they are generally more durable, as they are usually built to handle being moved around more.  The only time formatting a HDD is risky is when the drive is already starting to fail (at which point any read/write operations are dangerous).  Otherwise, it will not significantly effect the life of the drive.

Formatting shouldn't be necessary, though.  Like others have indicated, it's probably the MBR, which is fixable.

---

### Post by P4man on 2009-08-25
> **RabbitWho said:**
> As I understand it all you're doing is changing a few 1s to 0s and then back again. I don't see how that could do any damage.

Whats more is that with a (typical quick-) format, you dont even rewrite all bytes, you merely rewrite the partition table and filesystem tables, a few megabytes at most. Downloading almost any program from the net and saving it to you harddisk would cause more wear on your drive.

Defragging would certainly cause more "wear" on your drive, as then you are actually reading and rewriting a lot, if not all sectors on the drive you are defragging. But even that  shouldn't have any real impact on the drive's life expectancy. IT can however, lead to data corruption. If every I/O operation has a 1 in billion chance of failing and remaining undetected (pulled the number out of my... behind), then doing a 300GB defrag may actually make that 1/1B chance become a real possibility.

That is why ppl recommend you dont defrag more than needed: data corruption.

Last point: the most destructive thing to a harddisk is temperature, and temperature variation. Turning it on and off too often is more "dangerous" than reformatting.

---

### Post by Alethi0 on 2009-08-25
I'd just like to confirm formatting killing laptop hard drives. I think I've formatted mine about 10 times since I bought it a year ago and it failed last week. Anyone know a good affordable replacement hard drive for a Fujitsu Siemens Li 2727?

---

### Post by P4man on 2009-08-25
> **Alethi0 said:**
> I'd just like to confirm formatting killing laptop hard drives. I think I've formatted mine about 10 times since I bought it a year ago and it failed last week. Anyone know a good affordable replacement hard drive for a Fujitsu Siemens Li 2727?

I know a **very** affordable one: a Fujitsu Siemens Li 2727. Your should still be covered by warranty. AFAIK, they have 3 year warranty. (and formatting 10x won't void that ;) )

edit:oops, you gave the laptop number, not the hdd. You can check here how much warranty you have on the hdd should the laptop no longer be under warranty:

[http://www.fujitsu.com/us/services/computing/storage/hdd/warranty/summary.html](http://www.fujitsu.com/us/services/computing/storage/hdd/warranty/summary.html)

and thank god for belgian law obliging a minimum 2 year warranty :)

---

### Post by presence1960 on 2009-08-25
> **Alethi0 said:**
> I'd just like to confirm formatting killing laptop hard drives. I think I've formatted mine about 10 times since I bought it a year ago and it failed last week. Anyone know a good affordable replacement hard drive for a Fujitsu Siemens Li 2727?

So tell me in precise terms how you arrived at the comclusion that formatting is what killed your hard disk. Do you have any solid evidence or is this just conjecture?

Hard disks are like any other piece of machinery that has moving parts. They can give out at any time. Some people have brand new hard disks fail after a week or two. Is that because of formatting?

**[COLOR="Red"]Again formatting will not harm your hard disk. Your disk is made to perform read/write operations many, many times over.[/COLOR]** But the fact that the hard disk is comprised of separate parts which move is the reason most failures probably occur. There are other reasons: temperature, banging the hard disk, etc. it is like any other machine.

---

### Post by Kinetic_lord on 2009-08-29
> **presence1960 said:**
> That is not true, where are you getting this info about formatting?

From my laptop, he tells this to me every time i start my PC:

"Backup your data, a crash might be iminent, press F1 to continue"

...so, i didnt smashed it or something, only formats can screw it.

---

### Post by presence1960 on 2009-08-29
> **Kinetic_lord said:**
> From my laptop, he tells this to me every time i start my PC:

"Backup your data, a crash might be iminent, press F1 to continue"

...so, i didnt smashed it or something, only formats can screw it.

That message does not mean formatting has done the damage. what it may mean is your hard disk is about to fail. Formatting will not harm your healthy hard disk. Your hard disk is made to perform many, many read/write operations in it's lifetime. Which BTW in case you didn't know one of which is a format. You are misinterpreting the message and spreading false info. I suggest you investigate hard disks and how they operate. You have no evidence to say formatting ruins hard disks. Now if your disk is in bad health formatting it may be the last thing you want to do to it. But it is not the formatting that is the cause of it.

I still have a 5 year old IDE Seagate 160 GB that has been formatted I can't tell you how many times because of windows issues. It is in my machine now and still going strong.

---

### Post by P4man on 2009-08-30
> **presence1960 said:**
>  You have no evidence to say formatting ruins hard disks. Now if your disk is in bad health formatting it may be the last thing you want to do to it. But it is not the formatting that is the cause of it.


+1

(quick) formatting as far as a drive is concerned, is in no way different to writing a ~100Mb file. All that is done is a partition table that is being written and a file allocation table. Those are just "files", the only difference is that our operating system interprete them differently.

Doing a full format is no way different as writing a file as big as the partition.  Running windows for a day will probably cause more wear on your drive as more data will be read and written written to swap compared to even a full format. A harddisk really doesn't "know" the difference between writing a partition table (=format) or writing a file, and the effect on the drive is exactly the same.

What may case the confusion perhaps, is a *low level format.* something you actually can't even do anymore with modern drives without specialized tools.

---

### Post by Bartender on 2009-08-30
> **Kinetic_lord said:**
> From my laptop, he tells this to me every time i start my PC: "Backup your data, a crash might be iminent, press F1 to continue"

You laptop actually pops up with this message?  Where's the message coming from?  Is it a Windows error message, or does it appear to be from a utility the manufacturer installed, or what?

Kinetic, I have to agree with the general consensus.  Wrong conclusion, based on insufficient evidence.  Are you sure that this is even a HDD error message?

If it were me, I'd want to get to the bottom of this.  Find out what's generating the message, and what to do about it.  If it IS the HDD, you don't want to keep using it until one morning it's done and your data is for all intents and purposes irretrievable.

EDIT: If I'm not mistaken, there are several diagnostic tools available.  I think you can download a utility from the HDD manufacturer that can be burnt to a CD (like making an Ubuntu install CD).  Then spin the CD, test the HDD, see what it says.  If it truly is failing, it's gonna crap out on you soon whether you format or not, don't you think?

---

