---
title: "Windows can't see my DVD burned with brasero"
date: 2008-08-15
forum: General Help
---

### Post by Sycron on 2008-08-15
I have just burnt a dvd with brasero, but when i put the DVD on a windows box the DVD is empty. However when i put the DVD back in ubuntu box it sees my files.

What i've done bad ? I'm sure that I checked those increase compatibility with windows...

---

### Post by jerome1232 on 2008-08-15
I can't help you much but to bump your thread, I've had a similar problem where I copied Open Office documents to a dvd-rw, stuck it in a windows drive and it didn't see them, I put it back in ubuntu and I converted them to .doc files and reburnt, then windows magically saw them.

---

### Post by SabreWolfy on 2008-10-18
> **Sycron said:**
> I have just burnt a dvd with brasero, but when i put the DVD on a windows box the DVD is empty. However when i put the DVD back in ubuntu box it sees my files.

What i've done bad ? I'm sure that I checked those increase compatibility with windows...

Hi,

I am experiencing the same problem. I burnt a data DVD using Brasero, which reported errors. I tried again on another blank DVD using Nautilus burner, and the DVD burned successfully. I made an ISO of it and checked the md5sum against the original ISO and they were the same. However, the DVD appears as empty in Windows XP and Vista. The label of the DVD appears and Windows shows the used space correctly, but there are no files on the DVD. If I place the DVD back into Ubuntu, the files *are* present. Any ideas?

Same problem [here]("http://ubuntuforums.org/showthread.php?p=5990858").

---

### Post by Sycron on 2008-10-19
Eh... I don't use anymore MS things so it's not a problem for me. In my opinion is a MS Windows problem not an Ubuntu/Brasero problem.

---

### Post by jake1017 on 2008-10-19
It is another story of MS not supporting anything but there own products!

---

### Post by Sycron on 2008-10-19
> **jake1017 said:**
> It is another story of MS not supporting anything but there own products!

How true can be this sometimes. I tried to burn iso's with brasero and all of them worked in windows and this is strange.

---

### Post by SabreWolfy on 2008-10-19
Just for the record though, I have also experienced the reverse problem. A friend using W*ndows Vista burned a data DVD for me (in UDF format version 2 I think?) which I could not read in Ubuntu, so the problems seem to run both ways. I've only recently got a DVD writer, and it seems to be more trouble that it's worth! ](*,)

I did find a M*crosoft Hotfix for XP SP2 ([here]("http://support.microsoft.com/kb/899527")) which had something to do with UDF 2.0 DVD-RWs with sparing table spanning more than 1 sector (?), but the DVD in question shows as empty in XP SP3 (which includes that hotfix) and in Vista, which is strange. As I mentioned, W*ndows does show the DVD disk label and the used space correctly.

---

### Post by silviu.cacoveanu on 2009-04-11
No answers yet? I've been looking for a solution to this problem for months, still nothing...

I have no Linux on my laptop right now, so any ideea on how to get my files back would be appreciated (besides reinstalling linux)

Oh, and this is not necessarily a Windows problem, I've experienced it with different distributions of Linux too.

---

### Post by SabreWolfy on 2009-04-12
In my experience, *Brasero* is very unreliable. It's included by default now in GNOME 2.26 I think. I tried burning a normal CDRW recently with *Brasero* under Hardy and it broke the CD completely -- I could not even erase it. I now use Nautilus CD burning -- drag and drop files and folders onto the CD icon on the desktop and write to disk. Works better for me.

---

### Post by redbook4574 on 2009-04-12
> **SabreWolfy said:**
> In my experience, *Brasero* is very unreliable. It's included by default now in GNOME 2.26 I think. I tried burning a normal CDRW recently with *Brasero* under Hardy and it broke the CD completely -- I could not even erase it. I now use Nautilus CD burning -- drag and drop files and folders onto the CD icon on the desktop and write to disk. Works better for me.

I agree with the above I always stick with K3B (tried and tested) it has never let me down yet,

---

### Post by NFblaze on 2009-04-12
Wow...this sucks...I havent really used Brasero to burn anything substantial yet. Though, i remember I tried using the default release that came included with Intrepid...and it sucked..i t kept freezing up and it would accept all of the files I was requesting. I had to use Nautilus which worked very well. Although, the latest release doesnt seem to have that problem.

Although, from what I understand its the new default burner for Jaunty...

I dont really think that is such a good idea until all of the kinks are worked out...I hope they include an opt-in for Nautilus burner tho...

---

### Post by Aviopene on 2009-09-05
I don't think that Brasero sucks at all... It sucks hard about UDF stuff! :)

Well, I have the same problem: UDF DVD, (substantially 1.02, with errors) with a large (~ 4Gb) file on it, that results blank on WinXPSP3.

I tried the Toshiba UDF 2.5 driver:

[http://cdgenp01.csd.toshiba.com/content/support/downloads/qg600udfx.exe](http://cdgenp01.csd.toshiba.com/content/support/downloads/qg600udfx.exe)
[http://forum.slysoft.com/showthread.php?t=15597](http://forum.slysoft.com/showthread.php?t=15597)

with no luck, and then the Philips UDF Verifier:

[http://homepage.mac.com/wenguangwang/myhome/udf.html](http://homepage.mac.com/wenguangwang/myhome/udf.html)
(Partner area on [http://www.ip.philips.com](http://www.ip.philips.com), you'll need an account)

that says that my UDF DVD is "almost" 1.02 with some odd things (it also begin at sector 257, instead of a multiple of 16).

I'll bet a service pack that it won't read neither on Vista...

I'll try K3B, next time I need a UDF DVD... let's see.

---

### Post by jivabill on 2009-09-08
Well, I have a similar problem but it is with different versions of Ubuntu.

Burned a CD, I used Brasero.  I can see it fine on the original machine, the one that burned it which is using 8.04.

BUT

When I try to read it on my old Dell Latitude C610 Laptop which is running a new install of 9.04, it won't mount the CD period.  No way.  Says it can't mount the CD.  And in Brasero on the Laptop the CD shows as empty.

But I can put it on my Windows XP Pro machine and read it.  On the 8.04 machine and read it.

My conclusion is that Brasero is a piece of junk.  Possibly they got it from M$OFT?

---

