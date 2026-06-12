---
title: "Microserver hardware"
date: 2014-11-18
forum: Hardware
---

### Post by Skywalker# on 2014-11-18
Hey all,

I currently have a Mac-mini server but I'm not getting the most out of it considering how much it cost plus I like to keep things current so feel tied to upgrading the OS and paying the extra server OS costs.

My colleague has a Ubuntu server and I would like to go down the route or owning and implementing an Ubunu server.

I want a microserver that isn't too loud as it will be in the lounge (worst case scenario I could move upstairs).

Would you recommend Ubuntu server hardware wise that is small and fit for purpose?

I'm just planning on setting up SMB shares, telnet/ssh, FTP and Plex Media server - I have a NAS box that has the main storage. 

It's also to learn on - I want to learn Ubuntu server commands etc.

Thanks,
Luke

---

### Post by TheFu on 2014-11-18
If you have to transcode HiDef through plex for different client devices, you'll want a Core i5 or better CPU.
If you can live without transcoding, then a $100 AMD APU system will easily support those other requirements.  Don't go any cheaper - a RaspberryPi will have terrible performance for all those things.

Small, low-powered systems generally don't have a GUI. Will that be an issue?

The main consideration for these tiny systems is how much storage will be connected, how will it be connected and how do you plan to back it up?

Oh - and don't use telnet or plain FTP. Rather use ssh, sftp. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)  Inside the LAN, CIFS is fine ... telnet and FTP are just bad habits to be broken.

You'll have a steep learning curve - it will be fun too.
Is your background more Windows or OSX?

I can recommend beginning reading material based on your answer.

---

### Post by Lars Noodén on 2014-11-18
The minis make fine servers running Ubuntu.  Though you might have to do some fiddling with the video output to get it to boot headless.  Which model is it?

---

### Post by Skywalker# on 2014-11-18
Thank you both for your replies;

> **Lars Noodén said:**
> The minis make fine servers running Ubuntu.  Though you might have to do some fiddling with the video output to get it to boot headless.  Which model is it?

The only thing with keeping the Mac Mini is I have spent a lot of money for it to not do much. Originally I had more intentions for getting a Mac Mini - getting certified etc. Now I am certified in Cisco and the majority is CLI. I do like that aspect and that pushed me more to a linux server.

I am hoping to sell the Mac Mini after I replace it.

**TheFu:**
I convert/save my media to MP3 so all are the same format, currently I have this stored on my NAS box and Plex on the Mac Mini is mapped to it. It has no problem playing media this way.

No GUI is fine, as long as I have Ubuntu Server :)

The storage for the server itself would not need to be huge but doesn't hurt if the price is right, shares on the NAS will be sufficient. I have a separate external HDD which I can use to back it up (USB) or again I could do this on the NAS.

SSH would be more ideal, I hope I can set it up ok easily enough.

I have worked in IT for years supporting customers with Windows so I would say I am strong with windows although my primary OS at home (and preferred) is Mac OS X so a bit of both. Ubuntu I have dabbled with but it is my least known out of the three.

With the server hardware slimline or micro would be fine but I just want it too be reasonably quiet. The Mac Mini is pretty much silent.

Thanks again for your help.

---

### Post by TheFu on 2014-11-18
If you aren't using Plex for video - *ANY* CPU is fine. It is video transcoding that needs the power, not audio anything.  Audio is trivial and barely worth having Plex for - there are lots of other solutions.

---

### Post by Skywalker# on 2014-11-18
Sorry I forgot to say. I do play videos. They are stored on the NAS and accessed by the server running plex. There is no conversion - it plays the format that it is.

---

### Post by TheFu on 2014-11-18
> **~Luke said:**
> Sorry I forgot to say. I do play videos. They are stored on the NAS and accessed by the server running plex. There is no conversion - it plays the format that it is.

Well - if you have complete control over the format of the videos, then you can ensure they are stored so that GPU-based playback happens.  My $150 Plex server handles any SD content of almost any format fine in software - for HiDef content, it needs to be h.264 or mpeg2 video or the GPU won't be used and it will stutter, badly.  Playback for many devices - chromecast, roku, android, i-whatever may require transcoding.

---

### Post by Skywalker# on 2014-11-18
There's hardly any video there but what is there is MPEG4 or h.264 anyway.

What hardware do you have? - $150 is good.

---

### Post by TheFu on 2014-11-18
[http://blog.jdpfu.com/2012/08/15/building-a-new-to-me-system](http://blog.jdpfu.com/2012/08/15/building-a-new-to-me-system) - explains my build from 2012. I've looked for any comparable systems since then - cannot find any. I'd get another and use it as a NAS if I could. It took a while to get the box working without any terrible issues. Using it now to watch some PAL-encoded BSG DVDs. Enjoy the comments. ;)

BTW - mpeg4 isn't much of a standard - .mp4 is just a container - it can have any sort of video inside.  Online, most videos are h.264/aac/mp4.  Recorded TV here is mpeg2/ac3/mpg ... which gets transcoded into h.264/ac3+aac/mkv for local consumption.

---

