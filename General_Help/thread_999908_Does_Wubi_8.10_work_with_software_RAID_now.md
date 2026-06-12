---
title: "Does Wubi 8.10 work with software RAID now?"
date: 2008-12-02
forum: General Help
---

### Post by grahambeale on 2008-12-02
There seems to be conflicting advice across the support forums!

If not, does anyone know when there will be software raid support?

Many thanks,

Graham

---

### Post by Jammanuser on 2008-12-03
> **grahambeale said:**
> There seems to be conflicting advice across the support forums!

If not, does anyone know when there will be software raid support?

Many thanks,

Graham

simple answer: no...its not supported! see [this]("https://wiki.ubuntu.com/WubiGuide#Software%20raid%20arrays")

Hope this helps! ):P

Cheers!

-jammanuser

:D

---

### Post by chongzi35 on 2008-12-03
Through conduit **[cast steel valves](http://www.valvesupplier.net/cast-steel-gate-valves.htm)** are designed for oil & gas pipeline service. Featured with double block and bleed function, the [cast steel valve]("http://www.valvesupplier.net/cast-steel-gate-valves.htm") is suitable for bi-directional flow isolation.

---

### Post by grahambeale on 2008-12-07
[QUOTE=Jammanuser;6301975]simple answer: no...its not supported! see [this]("https://wiki.ubuntu.com/WubiGuide#Software%20raid%20arrays")

Hope this helps! ):P

Hmm...but it says "They will be supported in the 8.10 release". Isn't the latest release v8.10?

---

### Post by Jammanuser on 2008-12-07
> **grahambeale said:**
> [QUOTE=Jammanuser;6301975]simple answer: no...its not supported! see [this]("https://wiki.ubuntu.com/WubiGuide#Software%20raid%20arrays")

Hope this helps! ):P

Hmm...but it says "They will be supported in the 8.10 release". Isn't the latest release v8.10?

i'm pretty sure it meant the 8.10 release of **Wubi**, NOT Ubuntu 8.10! ;)

Cheers! ):P

-jammanuser

:guitar:

EDIT: the **current** release of Wubi is 8.04! Cheers! :D

---

### Post by grahambeale on 2008-12-07
[QUOTE=Jammanuser;6328076][QUOTE=grahambeale;6327953]

i'm pretty sure it meant the 8.10 release of **Wubi**, NOT Ubuntu 8.10! ;)

if you go to [http://wubi-installer.org/](http://wubi-installer.org/), it looks like wubi is on v8.10. am I wrong?

---

### Post by Jammanuser on 2008-12-07
> **grahambeale said:**
> [QUOTE=Jammanuser;6328076][QUOTE=grahambeale;6327953]

i'm pretty sure it meant the 8.10 release of **Wubi**, NOT Ubuntu 8.10! ;)

if you go to [http://wubi-installer.org/](http://wubi-installer.org/), it looks like wubi is on v8.10. am I wrong?

hmm...it sounds like we have a bit of a misunderstanding here...

ok, so let me lay it out for u how it is...

Wubi is an official **installer** of Ubuntu for Windows! The **current** version of **Wubi** (that is, the Windows installer for Ubuntu) is 8.04!

However, the version of **Ubuntu** is 8.10...NOT the version of Wubi...we're speaking about two different things here!

Please do not take that the wrong way...i wasn't trying to be rude or anything, just wanted to clarify what i meant! :guitar:

Cheers! :p

-jammanuser

):P

EDIT: as for what it said on that webpage...i believe they really meant **Ubuntu** 8.10, NOT Wubi 8.10...i'm pretty certain the latest version of Wubi is 8.04, and that is the version u download when u click the download button! Cheers! :D

EDIT #2: its a bit confusing, i know...that's just how i took it! i remember reading something in the Wubi Guide, which u can find [HERE]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won't%20boot?"), that the latest version of Wubi is 8.04! Cheers! :D

---

### Post by grahambeale on 2008-12-08
> **Jammanuser said:**
> [QUOTE=grahambeale;6328094][QUOTE=Jammanuser;6328076]

EDIT #2: its a bit confusing, i know...that's just how i took it! i remember reading something in the Wubi Guide, which u can find [HERE]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won't%20boot?"), that the latest version of Wubi is 8.04! Cheers! :D

It is very confusing! I was very lucky I didn't install that version thinking it was 8.10, it would have royaly screwed my set-up.

They really shouldn't put "Download Now, Wubi 8.10" on the homepage. It does tend to make the user think they are downloading v8.10 of Wubi rather than Ubuntu - especially if you are really keen for the soft raid support!

Thanks for you assistance anyway :)

---

### Post by Jammanuser on 2008-12-08
> **grahambeale said:**
> 

It is very confusing! I was very lucky I didn't install that version thinking it was 8.10, it would have royaly screwed my set-up.

They really shouldn't put "Download Now, Wubi 8.10" on the homepage. It does tend to make the user think they are downloading v8.10 of Wubi rather than Ubuntu - especially if you are really keen for the soft raid support!

Thanks for you assistance anyway :)

No problem...I'm glad i could help! :p

Cheers! :D

-jammanuser

:guitar:

EDIT: as for them needing to change their webpage...i'm with u on that, bro! the fact that they put "Wubi 8.10" is indeed confusing...and is something that they need to fix! Cheers! :D

---

### Post by boba1120 on 2008-12-09
I also don't mean to be rude, but I'm pretty sure Jamman that you're incorrect.  If you take a look at this:

[http://sourceforge.net/project/showfiles.php?group_id=198355&package_id=234923](http://sourceforge.net/project/showfiles.php?group_id=198355&package_id=234923)

It's pretty clear that the current release is 8.10 as of October 29.

I'm jumping in here because I'm having similar problems.  I've successfully installed wubi on other machines, but I'm unable to get it running on my home PC, which has an on-board (but still "soft") NVidia RAID 0.

---

### Post by smoky57 on 2008-12-22
The wubi.exe file downloaded from [http://www.wubi-installer.org/](http://www.wubi-installer.org/) is revision 515 and is version 8.10 (right click on exe file and select properties).

[http://www.wubi-installer.org/faq.php](http://www.wubi-installer.org/faq.php) says that software RAID is not supported which is fairly definitive.

However, there are many posts and documents (e.g. [https://wiki.ubuntu.com/WubiGuide#Software%20raid%20arrays](https://wiki.ubuntu.com/WubiGuide#Software%20raid%20arrays)) that says that "Software raid arrays 0 and 1 are not supported. They will be supported in the 8.10 release." Hence my (and, I think others) confusion.

My assumption is that software RAID support was planned to be included in Wubi 8.10 but problems prevented this happening. Is this correct? Are there new plans to include it in a future release? A different version of Wubi 8.10? Any guesses on when this support might be available?

I'd appreciate a summary of exactly what the situation is from someone involved in planning/developing this support. I'm sure this would clear up a lot of confusion.

I'm waiting for this support to allow installation onto an existing Dell system that has come with already setup Windows XP on a RAID 0 setup. This system isn't mine and I don't want to go through the process of resizing the RAID 0 system and then installing Ubuntu (lack of confidence!) but want to demonstrate the benefits of Ubuntu via the easy Wubi install.

Thanks for any news.

Ian

---

### Post by seubill on 2008-12-23
Apparently revision 515 is not supporting software RAID configurations. I'm using a Dell Precision 380 workstation configured to RAID Level 1 (mirroring) with XP Pro. GRUB files simply refuse to install, even using the Linux terminal. I tried a Grub Super Disk and still no success. Backed-up all data that I did not want to lose and then deleted the RAID array, of course effectively wiping both hard drives clean, reinstalled XP and Ubuntu 8.10 successfully. Rebuilt RAID array and now Ubuntu does not boot. \ubuntu\disks\boot\grub folder is empty on XP side. grub> /boot/grub/stage 1 does not exist on Linux side. Would also appreciate hearing an explanation from the planning/development folks!

---

### Post by skeetre on 2008-12-25
Hmm. I wonder if someone uses reconstructor or remastersys, etc to do a respin of Intrepid adding in dmraid, if it will then work in Wubi. I might just have to test this tonight. I will return with results tomorrow. :) I really wonder why Ubuntu doesn't include dmraid by default by now, as many other distros do.

---

