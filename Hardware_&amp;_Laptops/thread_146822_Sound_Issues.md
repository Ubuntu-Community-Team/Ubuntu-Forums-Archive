---
title: "Sound Issues"
date: 2006-03-19
forum: Hardware &amp; Laptops
---

### Post by LinuxLove on 2006-03-19
Hi,
I've been using Ubuntu since 5.04 release, and since have not been able to find a solution to my sound problem. Basically, I can't hear anything; nothing is coming out of my speakers.

I'm now on 5.10 and the problem persists.

Any information or help is greatly appreciated.
Thanks

---

### Post by hw-tph on 2006-03-19
Not much to go on here so I'll start by requesting some information.

[LIST]
[*] What kind of sound hardware do you have? **lspci | grep -i audio** should tell you if you don't know.

[*] Do you get any error messages? If so, please post them.

[*] Are the audio cables connected to the correct outputs of your card?

[*] Are the proper channels unmuted and set to audible levels (use **alsamixer** in the console).
[/LIST]


Håkan

---

### Post by LinuxLove on 2006-03-19
[LIST=1]
[*]"Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)"
[*]No.
[*]Yes, sound works in Windows XP perfectly.
[*]I checked in users and groups, and I am listed under audio. In volume control my speakers are not muted. In Multimedia Systems Selector I have ALSA selected as output and input.
[/LIST]

Hope this helps.

Thanks for your reply.

---

### Post by KiLLeR_WoMBaT on 2006-03-19
Join the club.  I've posted for several days on similar problems.  I also have an Intel chip and cannot get sound in Gnome.  The login sound plays when Ubuntu boots up, but once you login there is no sound and no matter what sound driver you choose (Asla, Esd, Oss, Artd) in multimedia selector it says "Failed to construct test pipeline for ....'whatever one I've chosen'."

I've checked and done the above mentioned things also.  I've asked what logs to look at and post (no answer for days from 5 different posts) to help diagnose the problem.

lspci | grep -i audio gives he following:

daniel@WoMBaT-Laptop:~$ lspci | grep -i audio
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:03:04.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)


No sound program runs no matter whether I use ESD, ALSA, OSS, or ArtD.  mPlayer plugin in Firefox will load a sound or movie, but then exit out saying "Stopped".  Here are some of the errors and stuff related I have gotten:

---

