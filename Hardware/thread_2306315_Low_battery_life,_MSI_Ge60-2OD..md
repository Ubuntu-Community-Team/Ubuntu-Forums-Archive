---
title: "Low battery life, MSI Ge60-2OD."
date: 2015-12-14
forum: Hardware
---

### Post by anawizowski on 2015-12-14
Hey folks,

I am running Ubuntu 14.04 with the Unity environment on my MSI GE60-2OD laptop. I noticed the battery dies out really fast ( about 20-25minutes ) while on Windows it lasted about 80 minutes.
Tha laptop has a dual gpu system, though I am running it with the integrated Intel one while on battery.

I don't run many programmes in the background- just Dropbox and Spotify.

Any ideas what may be causing the problem, or how to check the root of it?

---

### Post by Vladlenin5000 on 2015-12-14
Hi and welcome.

It begs the question: When did it last 80min with Windows? 1-2 years ago?

---

### Post by pfeiffep on 2015-12-14
> **anawizowski said:**
> Hey folks,

I am running Ubuntu 14.04 with the Unity environment on my MSI GE60-2OD laptop. I noticed the battery dies out really fast ( about 20-25minutes ) while on Windows it lasted about 80 minutes.
Tha laptop has a dual gpu system, though I am running it with the integrated Intel one while on battery.

I don't run many programmes in the background- just Dropbox and Spotify.

Any ideas what may be causing the problem, or how to check the root of it?Assuming the difference was measured on a fully charged battery in the same week you might benefit from my [experience]("http://ubuntuforums.org/showthread.php?t=2251752") having the screen intensity adjusted.

---

### Post by anawizowski on 2015-12-14
@Vladlenin5000 actually it was about a week ago, I just transitioned to Ubuntu.
@pfeiffep Thanks, I'll give it a go.

---

### Post by efflandt on 2015-12-15
I have a GE60-2OE. I have not tested battery life lately, so not sure how long it lasts, but I don't remember it going down real quick while using it with Intel graphics on battery. I boot 64-bit Ubuntu 14.04 from a 512 GB mSATA SSD card that I added and spin down my hard drive.

Note that the battery will drain some even when it is not on. So if it was not fully charged recently when you booted it, that may somewhat explain it. But dimming the screen some when on battery and turning off keyboard backlight should help.

---

### Post by anawizowski on 2015-12-15
The solution provided by pfeiffep actually helped. Thanks a lot!

---

### Post by trag on 2015-12-20
Try installing TLP for better battery life
[FONT=Roboto Slab]sudo add-apt-repository ppa:linrunner/tlp[/FONT]
[FONT=Roboto Slab]sudo apt-get update[/FONT]
[FONT=Roboto Slab]sudo apt-get install tlp tlp-rdw[/FONT]
[FONT=Roboto Slab]sudo tlp start[/FONT]

---

