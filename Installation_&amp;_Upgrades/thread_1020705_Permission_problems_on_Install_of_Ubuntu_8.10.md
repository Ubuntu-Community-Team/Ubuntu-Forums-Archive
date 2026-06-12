---
title: "Permission problems on Install of Ubuntu 8.10"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by Epidural on 2008-12-24
Hi there. I'm trying to install Ubuntu Desktop 8.10 from the CD. 

When I try to do anything from the CD (either the Install or to try the Live CD), it gives me an error saying "-bash: /dev/null: Permission denied". 

I have a command prompt (ubuntu@ubuntu:~$) but don't know what to do from here.

The hard drive is good, but the CD says it has errors on it (So says the CD Checker with Ubuntu)

However, I've tried 2 CDs that worked no more than 3 days ago, and they both come up with the same permission error and the same amount of errors on the disc. It just seems unlikely.

Any help is appreciated.

---

### Post by 2hot6ft2 on 2008-12-24
Did you md5sum the iso you downloaded to make sure it was good? Burn at the slowest speed possible? Use a cd drive lens cleaner?

---

### Post by Epidural on 2008-12-24
> **2hot6ft2 said:**
> Did you md5sum the iso you downloaded to make sure it was good? Burn at the slowest speed possible? Use a cd drive lens cleaner?

Quite honestly I don't know what a md5sum is, and I burnt it at the AutoDetect speed here on my laptop. (The only other option my burner gave me was 24x.)

The thing I can't wrap my head around is that all 3 of the CDs worked on other computers not long ago, and yet all of a sudden all three have errors and such? I even made one this morning from the latest download of 8.10 from Ubuntu's website, and it's not working either.

Is the CD the only possiblity?

---

### Post by 2hot6ft2 on 2008-12-24
> **Epidural said:**
> Quite honestly I don't know what a md5sum is, and I burnt it at the AutoDetect speed here on my laptop. (The only other option my burner gave me was 24x.)

The thing I can't wrap my head around is that all 3 of the CDs worked on other computers not long ago, and yet all of a sudden all three have errors and such? I even made one this morning from the latest download of 8.10 from Ubuntu's website, and it's not working either.

Is the CD the only possiblity?
How to md5sum here
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
The md5sum hashes here
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Dirty cd/dvd drive lens would cause errors. An old worn drive would too. Burn at the slowest speed possible. Read the instructions on the pages linked to above.

---

### Post by 2hot6ft2 on 2008-12-24
You also might try adding noacpi to the end of the command string when starting the cd. Right after selecting your language hit the F6 key and add the noacpi to the end and hit enter. That works for some but doesn't explain the errors.

---

### Post by Epidural on 2008-12-24
> **2hot6ft2 said:**
> You also might try adding noacpi to the end of the command string when starting the cd. Right after selecting your language hit the F6 key and add the noacpi to the end and hit enter. That works for some but doesn't explain the errors.

Adding "noacpi" to the end of the boot options string didn't seem to work (I simply wrote noacpi at the end of the string, nothing else, is there something extra I have to do there?), but I'm in the process of burning a new ISO at a slower speed (new burning software). The md5sum was a match to the Desktop i386 8.10 version listed, and it all checks out that way.

Is it possible that the error has ANYTHING to do with the board, ram, or processor? Because the other hardware (DVD and CD drives, hard drives, vid card) were all from my old machine which Ubuntu worked perfectly on. It's using rambus memory... Somehow I doubt any of that would make a difference but I'd really like to get this problem solved and I guess anything helps.

---

### Post by 2hot6ft2 on 2008-12-24
> **Epidural said:**
> Adding "noacpi" to the end of the boot options string didn't seem to work (I simply wrote noacpi at the end of the string, nothing else, is there something extra I have to do there?)
No that was it, didn't think that would do anything for the errors.

You could try the mem test that's on the cd to check for RAM errors. Or try the OEM install that's on it or just install without going to the live part.

---

### Post by Epidural on 2008-12-24
> **2hot6ft2 said:**
> No that was it, didn't think that would do anything for the errors.

You could try the mem test that's on the cd to check for RAM errors. Or try the OEM install that's on it or just install without going to the live part.


I did the memtest, everything checked out.

I'll try the OEM install next. I'm occupying my time with installing XP onto a seperate partition at this moment, but I'm also downloading Fedora to see if it will work. I found a program that's writing the discs at 4x, so I'll try once more to get Ubuntu going from a 4x disk after the OEM install try.

Thanks for all your help, I'll reply back with any findings good or bad.

---

### Post by 2hot6ft2 on 2008-12-24
> **Epidural said:**
> Is it possible that the error has ANYTHING to do with the board, ram, or processor? Because the other hardware (DVD and CD drives, hard drives, vid card) were all from my old machine which Ubuntu worked perfectly on. It's using rambus memory... Somehow I doubt any of that would make a difference but I'd really like to get this problem solved and I guess anything helps.
Sure it is, could be any of them. I would try swapping the cd drive with a newer one if you have one laying around. That has worked before with some machines I've installed on.

---

### Post by 2hot6ft2 on 2008-12-24
> **Epidural said:**
> I did the memtest, everything checked out.

I'll try the OEM install next. I'm occupying my time with installing XP onto a seperate partition at this moment, but I'm also downloading Fedora to see if it will work. I found a program that's writing the discs at 4x, so I'll try once more to get Ubuntu going from a 4x disk after the OEM install try.

Thanks for all your help, I'll reply back with any findings good or bad.
Sounds like a plan and 4x is much more in line with what they recommend.

---

### Post by Epidural on 2008-12-24
B-e-a-u-tiful success.

It was my DVD drive... somehow. I guess the new board didn't quite interface properly with this DVD drive.

XP installed from it no problem, but nothing else seemed to want to interface quite right (installing .exe's from the disk, etc)

Switched my CD/RW to master, popped the CD in, and it's working flawlessly.


Thanks to those who replied.

---

