---
title: "DVDROM help please!"
date: 2010-02-17
forum: Hardware
---

### Post by shadowcrunch on 2010-02-17
Hello! I've been bouncing around forums on this problem for a few weeks, trying this and that, with no luck. I should add I have about 3 months into Ubuntu (9.1). The problem I'm having is my dvd-rom drives. In my desktop I have two drives, top is a reader, bottom is a dvd-r/rw. Both drives work fine in vista and I can boot off both no problems. In Ubuntu, the reader opens and closes, spins the discs, but will not read anything (music, movies, or data)...while the writer won't even open. 

Here's what I know so far: when I go to places/computer I see two icons for cd/dvd, but when I right-click and go into properties there is no information, the privilege tab is grayed out on both drives. When I open 'fstab' with gedit, it shows one drive on /dev/scd1. I'm assuming because the other drive isn't in fstab that's why it won't even open.

most recent thing I tried tonight was based on a forum post which said to mount the /dev/scd1 using a terminal command something like 'mount /dev/scd1 /mount/cdrom' but when I tried that it failed saying that location does not exist. I would really like to get both drives working properly. Anybody have any ideas? Thanks in advance for any help!

---

### Post by FabioSan on 2010-02-17
Hi,

I had also tried to mount a DVD reader without success despite following different recommendations from several sources. In my case the software solutions did not work, they all referred to what you mention in your message, fstab. I wondered if the problem could be my hardware and noticed that Ubuntu responded in different ways to changes in jumper configuration. When I made my drive behave as a slave all software problems were gone. I am not sure this will solve your problems but it might be worth trying to change your jumper configuration on the CD/DVD readers. Good luck,  Fabio

---

### Post by shadowcrunch on 2010-02-18
Thanks for the response! Interesting idea, and I'm sure I never would have thought of it. Now all I have to do is get the motivation to pop this sucker open again (just put my case back together a few days ago...again). Thinking about it, I never even checked to see how my drives were set up in the first place! Oh well, thanks again!

---

