---
title: "Please, please, please help me. Hardy install cleared 1TB of data"
date: 2008-07-17
forum: Hardware
---

### Post by Arcy on 2008-07-17
Hello,

I've been a fairly avid Ubuntu user over the years, but I had to take a hiatus and go back to Windows XP for work purposes. Yesterday, however I was finally able to come back to Ubuntu. I downloaded the ISO, burned it, and restarted my computer. I was greeted with a new installer, and I have to say I was impressed with Hardy so far, then absolute disaster.

I decided to manually partition my internal harddrive, as well as set mount points for my two external drives. I told the installed to only format my internal. With everything set, I hit next and the install started. A few moments later the activity lights on my external drives started going crazy. Frantically I hit cancel, hoping to halt whatever was going on. I just wanted to set mount points, why all the activity?

Upon restarted my computer and getting into the LiveCD environment I discovered the true horror...

All my data, nearly 1TB worth, was gone. Emails, documents, music, applications, financial info, projects, and my portfolio...gone. These were my backup drives, and I just formatted my internal, I am screwed.

Quickly, I reinstalled windows xp and grabbed every data recovery app I could find. GetDataBack, PC Inspector, etc.

I can't recover my data, I don't know what else to try. 

Please, anyone, any advice, my entire personal and professional life was on those two external drives.

-Colin R.
Lighting Designer

---

### Post by snowpine on 2008-07-17
Hi Arcy, welcome to the forums (and sorry it is under these circumstances). I am afraid I'm not a data recovery expert, so I can't help you except to bump your thread. :(

I am sure you probably already know this, but you should immediately stop using the drives until you have a strategy, because continuing to use them will make the data recovery more difficult. 

Good luck Colin!

---

### Post by CryptSphinx on 2008-07-17
hi , havent done much file recovery before but heres a relevant link

[http://ubuntuforums.org/showthread.php?t=417761](http://ubuntuforums.org/showthread.php?t=417761)

---

### Post by Arcy on 2008-07-17
Thanks for the link. I'll look into those options extensively. Right now the drives are just sitting there, off and unplugged from my system. I'm going to test out the various recovery apps on another drive that lost data, but not nearly as important. If something is going to get even more messed up, might as well be a drive I don't care about.

I think I'm still in denial...

---

### Post by Brebs on 2008-07-17
Find a professional data recovery service, and pay the money. Don't do anything with the drives yourself - that includes your formatted master, as well as the backups. The master might have recoverable data.

In future, whenever installing an OS, physically disconnect any drives containing important data.

---

### Post by Arcy on 2008-07-18
Alright, I recovered my files... the only problem is nothing has an extension or correct file name. I can live without the file names for now, but does anyone have a way of determining the file type for a large batch of files?

Lostfile00000021 doesn't tell me much :(

---

### Post by dominiquec on 2008-07-18
Happy to hear you managed to partly recover your data.

> does anyone have a way of determining the file type for a large batch of files?

Try this:

```
find mydirectory -type f -exec file {} \;
```

where mydirectory is the parent directory.  You can pipe the output to a file if you want.

Here's sample output from my own computer:

> Documents/Dagmay 2008-06-18/Mga Mama ug Mga Papa.txt: UTF-8 Unicode text, with very long lines
Documents/Dagmay 2008-06-18/Dagmay 2008-06-22.doc: Rich Text Format data, version 1, ANSI
Documents/Dagmay 2008-06-18/Dagmay 2008-06-21.abw: XML


---

