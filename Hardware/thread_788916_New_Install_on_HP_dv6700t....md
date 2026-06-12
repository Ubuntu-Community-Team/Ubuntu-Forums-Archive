---
title: "New Install on HP dv6700t..."
date: 2008-05-10
forum: Hardware
---

### Post by zoiks on 2008-05-10
(Warning: Unsolicited Blurb!) Welp, just got my new HP dv6700t today. I am trying to get moving on my Ubuntu Hardy Heron install. A couple of notes:

1) I CANNOT BELIEVE HOW LONG IT TAKES TO CREATE THE VISTA RECOVERY DISKS. It's ridiculous. The manual says to create a set of one-time recovery disks when you start up your new HP laptop. It takes not minutes, but **a few hours** to do this! On a brand spanking new computer with 3G RAM and a T8400 chip using DVD+R disks. Ugh. <rant off>

2) I first booted the system up with the ubuntu 8.04 live disk. I noticed most of the hard drive space was left unpartitioned (I got a 250G drive). There's an sda1 at the beginning (~30G) which seems to contain the base windows system, and a sda2 recovery partition at the end (~15G). I created a large partition using GParted sda3 25G *after* the end of sda1 that used up the space all the way up to the beginning of sda2, in anticipation of using this to install Ubuntu. **I'm rather glad I did that before running Vista** (laptop came with Ultimate) as it seems when **Vista first boots it expands the base Windows partition to fill the unpartitioned space**. Once Vista was finally running (had to wait for a while) I noticed I had ~60G total on the C: drive.

3) While running the live ubuntu CD, seems just about all of the stuff works out of the box, including the webcam, but the built-in mics didn't work for audio recording. I'll have to check back with this when I install ubuntu after finishing this godforsaken "recovery disk" burning. (Seriously, couldn't HP have included 3 DVDs at a cost of say $0.50 each, and save their customers hours of waiting around and screwing around???)

Soon I will be (attempting anyway):
 - Setting up the integrated Intel wireless a/g/n to work on my network (802.11g + WPA). That'll be a change from the Ralink rt2500 solutions I've been using with PCMCIA cards for the last couple of years.
 - Getting the fingerprint scanner to work as a login authentication under ubuntu. That otta be fun!

---

