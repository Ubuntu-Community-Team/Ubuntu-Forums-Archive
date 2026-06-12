---
title: "hardware recommendations for ubuntu server"
date: 2012-08-08
forum: Hardware
---

### Post by badperson on 2012-08-08
Hi,
I want to build a home server that will stay on all the time. The setup I have now has had consistent problems, and I don't know if it's hardware or software. 

Can any of you who have home servers that stay on all the time talk about what hardware you chose and how it's worked out for you? 

the server will serve as a samba share, a web server, version control, host a db and so on. 
thanks, 
bp

---

### Post by badperson on 2012-08-10
k,
short followup. Are there any good SSD's I could use for a syatem drive? Any rec's for a small/fast sys drive? 

Also, my current server is now not posting. I'll have to pull it out, unseat all the ram and boot up with one stick at a time. Then I'll turn the thing on, leave it running for 6 weeks or so and the problem will repeat. 

Does that issue sound familiar to anyone? 
I posted in a couple prev posts about the issue I was having: 

[http://ubuntuforums.org/showthread.php?t=2004838]("http://ubuntuforums.org/showthread.php?t=2004838")

[http://ubuntuforums.org/showthread.php?t=1905674]("http://ubuntuforums.org/showthread.php?t=1905674")

but didn't get a lot of answers. Anyway, I think I'm ready to just bag my current setup and get some parts designed for servers. 

thanks, 
bp

---

### Post by ahallubuntu on 2012-08-10
I've built a number of servers for various uses using "consumer hardware" (not enterprise stuff that's more reliable but really expensive).

One server uses a Core 2 Duo CPU and a G41 Express chipset motherboard.  It is an archive server (Samba and FTP) and is mostly OFF and in Standby.  I wake it up remotely via Wake On Lan and can access it even over my VPN that way from outside my network.

I just have a standard SATA system drive in this thing.  It draws about 50 watts at idle with several drives in it, but it's not on that much.  

I just built a web/email server that's on 24/7.  This one has a Sandy Bridge Celeron (dual core) G540 2.5GHZ - plenty fast enough for what I need, but best of all, it draws only about 20 watts at idle!  I built it with a cheap motherboard with an H61 chipset and 4GB of RAM.  I put an Intel SSD in it.  Intel SSDs are considered to be more reliable than some of the cheaper consumer brands.  I expect this won't last forever, but I back it up regularly and would be able to restore to another drive efficiently if need be.  I would do the same with a hard drive.  I just assume it will fail at some point and have a tested, systematic recovery plan in place.

I put 12.04 LTS server edition on the Sandy Bridge system.  It works great except that while I was testing it, I could not get suspend/resume to work reliably.  This system is on 24/7 so I don't care about suspend, but I did with the other, older machine that I wake up when needed.    Maybe I could have tweaked things to get suspend to work on the H61 chipset, but I didn't bother for now.  If you think you'd care about suspend and resume, take that into consideration - Ubuntu may not support them yet on newer hardware or at least not without a lot of tweaks.

---

