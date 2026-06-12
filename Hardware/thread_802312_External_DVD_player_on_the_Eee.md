---
title: "External DVD player on the Eee"
date: 2008-05-21
forum: Hardware
---

### Post by sebast on 2008-05-21
Hi,

I installed Hardy on a friend's computer and he has problems with an external DVD player.

What he did is take out is tower's DVD player and installed it in an external enclosure.

I don't know exactly where to problem comes from but he told me that when he plugs it in the usb port, nothing happens like if it's not recognized.

I'm going to his place tomorrow to help him out, but I would like to know what to look for to make it work properly.

Thanks a lot in advance!

---

### Post by Longrifle3006 on 2008-05-23
> **sebast said:**
> Hi,

I installed Hardy on a friend's computer and he has problems with an external DVD player.

What he did is take out is tower's DVD player and installed it in an external enclosure.

I don't know exactly where to problem comes from but he told me that when he plugs it in the usb port, nothing happens like if it's not recognized.

I'm going to his place tomorrow to help him out, but I would like to know what to look for to make it work properly.

Thanks a lot in advance!

I used an external USB DVD drive on my Eee and it worked like a charm, no problems at all. Might want to check the cable and check for other simple stuff....

---

### Post by sebast on 2008-05-28
Ok,

I went to see him and it seems that the DVD player has its own power and is recognized by Ubuntu fine. I put a C and was able to see the audio files but was unable to play them or copy them on the hard drive. The system told my that there was no data.

What I did is take the external DVD player and brought it home to test it. I also run Ubuntu 8.04 but on a desktop. I put a CD in it and I was able to play the files but they would skip and some of them would stop playing after only a couple of seconds. When I copy the MP3s on the C to my hard drive, I get the same problem, the songs skip all the time.

I assume that the problem comes from a malfunctioning DVD enclosure then. Correct me if I'm wrong.

Thanks

---

### Post by Zatta on 2009-04-29
I have an Eeepc 701. I connected a dvd drive (ide) to it using an ide/usb converter, so as to use it as an external dvd drive.

I had a problem: dvd movies would play for a while, then stop. Sometimes dmesg complained about "Buffer I/O error on device sr0, logical block xxxx", sometimes not. The player would just suddenly stop.

Hard disks connected to the ide/usb converter always worked fine.
The player I used - vlc - was complete with libdvd3 and libdvdcss2.
I tried all 3 usb connectors. 

All to no avail.

Then I saw this post:
[http://forum.eeeuser.com/viewtopic.php?id=58710](http://forum.eeeuser.com/viewtopic.php?id=58710)

Following the sugestion of boa13 in that post, I changed the settings of the player so that it would open the dvd at /dev/sr0, not /dev/scd0 anymore: open vlc->tools->preferences->input and codecs->default disc device->changed to /dev/sr0

It worked 100%. Now dvd movies play without stutter and without stopping suddenly.

Hope it helps.


Zatta.

---

