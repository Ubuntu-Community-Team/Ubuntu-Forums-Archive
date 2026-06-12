---
title: "Live CD not booting"
date: 2008-10-08
forum: General Help
---

### Post by user1001 on 2008-10-08
Hi all,

I just downloaded the ISO, burned it on a cd, so I am sure it is the newest version.

the version I downloaded was: 
 Ubuntu 8.04 LTS Desktop Edition - Supported to 2011
 Standard personal computer (x86 architecture, Pentium&#8482;, Celeron&#8482;, Athlon&#8482;, Sempron&#8482;)

My current CPU is: Intel Pentium 4 HT 3.4 GHZ.

The boot screen takes ages, and after that's finished, an error keeps repeating down the screen...

btw: Ubuntu 7.10 works But I don't have that anymore after I formatted my pc and installed XP MCE.

thx in advance

---

### Post by phidia on 2008-10-08
What is the error that keeps repeating?

Did you check the md5sum of the downloaded iso?

---

### Post by Elfy on 2008-10-08
First - it would be good to know what the "error keeps repeating" actually is.

HAve you sufficient ram to boot the livecd - 384Mb minimum requirement.

Have you checked that the cd burn isgood with the check cd for defects option.

Did you check the md5sum of the download prior to burning it - [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by user1001 on 2008-10-08
> **phidia said:**
> [COLOR="#0000ff"]What is the error that keeps repeating?[/COLOR]

**Did you check the md5sum of the downloaded iso?**


**what is that?**

btw: [COLOR="Blue"]the error keeps repeating so fast I can't seem to read it :S[/COLOR]

and also I tried open suse, newest version, it took so long on the boot screen (same thing) i just shut the pc switched it on again and took the cd out.

---

### Post by Therion on 2008-10-08
Reburn the CD image using a burn speed of 8x -- or thereabouts.  4x is even better.

Edit: Almost forgot... Sometimes I have better luck burning CD images onto DVD's.  Don't know why it seems to help (and it's not a sure thing) but it seems to work sometimes when nothing else does.

---

### Post by user1001 on 2008-10-08
> **Therion said:**
> Reburn the CD image using a burn speed of 8x -- or thereabouts.  4x is even better.

You sure that will work?, 
I brned mine with a program called Sonic something... I didn't have options like that...
what program do you suggest?

---

### Post by Kevbert on 2008-10-08
Please take a look at [[COLOR="Red"]this[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto")
First you need to perform a md5sum on the downloaded file.  Then burn at the slowest speed possible. Finally check the integrity of the CD.  It's all in the link above and any tools that you need.

---

### Post by Therion on 2008-10-08
> **user1001 said:**
> You sure that will work? 
No.  But it won't hurt.  You need burn ACCURACY here, not speed.

> **user1001 said:**
> I brned mine with a program called Sonic something... I didn't have options like that...
what program do you suggest?
Burning from within a Windows install I assume?  I'd suggest using [Active ISO Burner](http://www.ntfs.com/iso-burning.htm) or [Deep Burner](http://www.deepburner.com/?r=download).  Both have free versions.

---

### Post by user1001 on 2008-10-08
I just checked the integrity, and there was 3 file errors, waste of CD LOL!

now how do I find the download link of that program to check MD5...?

edit#1: found it... :)

edit#2: check sum is same, burning Image...
Now if I get this to work, I'll update here.

---

### Post by user1001 on 2008-10-08
I burned disk in 8x... still the same error.

**[COLOR="Red"]0x7ab16[/COLOR]** repeating within a sentence of error, which I was unable to stop to read.... ++
integrity check, error in 3 files.

any of you know what this is?...

I am assuming I might have downloaded the wrong version, 
[COLOR="Navy"]I downloaded:
 Standard personal computer (x86 architecture, Pentium&#8482;, Celeron&#8482;, Athlon&#8482;, Sempron&#8482;)[/COLOR]
[COLOR="RoyalBlue"]maybe I should've downloaded:
 64bit AMD and Intel computers[/COLOR]

btw my cpu is Intel Pentium 4 3.4GHZ Hyper Thread

---

### Post by user1001 on 2008-10-08
sorry for bumping... :) it's about to get lost in other pages :(

---

### Post by Therion on 2008-10-08
It is possible your CPU is 64-bit, some P4's are.  Even if it is, you should still be able to install the 32-bit version of Ubuntu.

I'm pretty convinced we have failure to get a clean burn of your media here however.  Do you use any Torrent applications like Bit Torrent, uTorrrent or Transmission?  

The reason I ask is that anything downloaded via a torrent is automatically checked for integrity.  It's a more reliable download.  If you can, I'd try that.

Or you could try using a different brand of CD's, burning the .iso on a different computer, or burning the .iso on a DVD instead of a CD.

One more thing to try if you can burn a DVD: Get the .iso of Ultimate Edition (see my sig line).  I've seen it boot up for people when the plain-vanilla version of Ubuntu would not.

Worst case scenario, try burning an .iso of 7.10 and maybe you can force a dist-upgrade.  Not my preferred way of doing things, but it might work if we have no other option.

---

### Post by user1001 on 2008-10-08
> **Therion said:**
> It is possible your CPU is 64-bit, some P4's are.  Even if it is, you should still be able to install the 32-bit version of Ubuntu.

I'm pretty convinced we have failure to get a clean burn of your media here however.  Do you use any Torrent applications like Bit Torrent, uTorrrent or Transmission?  

The reason I ask is that anything downloaded via a torrent is automatically checked for integrity.  It's a more reliable download.  If you can, I'd try that.

Or you could try using a different brand of CD's, burning the .iso on a different computer, or burning the .iso on a DVD instead of a CD.

Worst case scenario, try burning an .iso of 7.10 and maybe you can force a dist-upgrade.  Not my preferred way of doing things, but it might work if we have no other option.

so you're saying the download may be broken?
since it gives the same error on two of the burned cd's that might be the case...

I'll try torrent.

I will update..

---

### Post by Therion on 2008-10-08
> **user1001 said:**
> so you're saying the download may be broken?
Yes.  

In my experience the two biggest causes of LiveCD "failure" is a corrupt download or a corrupt "burn" of the disc.  We're going to try and eliminate those possibilities first since they are the easiest and the cheapest of the available things to try.

---

### Post by user1001 on 2008-10-08
> **Therion said:**
> Yes.  

In my experience the two biggest causes of LiveCD "failure" is a corrupt download or a corrupt "burn" of the disc.  We're going to try and eliminate those possibilities first since they are the easiest and the cheapest of the available things to try.

I swear MD5 thing checks for broken downloads? ... am I right?

---

### Post by lisati on 2008-10-08
> **Therion said:**
> 
Edit: Almost forgot... Sometimes I have better luck burning CD images onto DVD's.  Don't know why it seems to help (and it's not a sure thing) but it seems to work sometimes when nothing else does.
I checked out using DVDs when I first came to Ubuntu. One  possibility that comes to mind is that some blank CDs have a 650Mb capacity instead of the 700Mb capacity that I usually buy. I haven't used one for a while, however. And some brands of CD seem to be more reliable than others.

> **user1001 said:**
> You sure that will work?, 
I brned mine with a program called Sonic something... I didn't have options like that...
what program do you suggest?
Both my current machines came with software by Sonic pre-installed with XP: my desktop has "MyDVD", and my laptop has a customised version of "RecordNow" (which seems to be geared towards audio CDs). I think Roxio supports these products these days.

---

### Post by Therion on 2008-10-08
> **user1001 said:**
> I swear MD5 thing checks for broken downloads? ... am I right?
I would be burned at some kind of stake, I'm quite sure, if I were to impugn Md5 sums so I'm not going to.  I'm simply going to say that I do not trust them 100%.  Let's just try a torrent and we'll go from there.

I would also prefer it if you would try using Active ISO burner since it's a well known and trusted performer for this particular task.

---

### Post by user1001 on 2008-10-08
> **Therion said:**
> I would be burned at some kind of stake, I'm quite sure, if I were to impugn Md5 sums so I'm not going to.  I'm simply going to say that I do not trust them 100%.  Let's just try a torrent and we'll go from there.

I would also prefer it if you would try using Active ISO burner since it's a well known and trusted performer for this particular task.

thx for the info, I just found a 7.10 cd at home, I am currently on it..

however now the problem is when I click on install on the desktop, it doesn't run ? :(

---

### Post by user1001 on 2008-10-08
> **user1001 said:**
> thx for the info, I just found a 7.10 cd at home, I am currently on it..

however now the problem is when I click on install on the desktop, it doesn't run ? :(

damn, I am so dumb, it opened on the other desktop :@ LOOL
edit: and now I replied to my self, maybe I have to go and have a rest :(

---

### Post by Calmatory on 2008-10-08
If another distro fails also, that could mean that there is something in common between them which is causing this. New kernel maybe? 

I am almost certain that it is a hardware compatibility problem, and kernel might be causing it. What you could do is try to remove all the external peripherals(sound card, use integrated VGA instead of external card, network card) and and disable all integrated devices in BIOS(except the VGA, if it is used) and then try again. Even better would be if you could test it with same parts but with different motherboard.

---

### Post by Therion on 2008-10-08
> **Calmatory said:**
> 
I am almost certain that it is a hardware compatibility problem, and kernel might be causing it. What you could do is try to remove all the external peripherals(sound card, use integrated VGA instead of external card, network card) and and disable all integrated devices in BIOS(except the VGA, if it is used) and then try again. Even better would be if you could test it with same parts but with different motherboard.
Very possible, but I'm thinking we should rule out a few things before we start tearing the system apart.  

Besides, if it is a hardware compatibility issue and we tear his system down to the bare essentials to confirm it, we'll be no further ahead than when we started.

---

### Post by Kevbert on 2008-10-08
Have you performed a memtest recently from the CD boot menu ?  It may be worth running it for at least a couple of passes.

---

