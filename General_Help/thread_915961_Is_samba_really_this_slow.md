---
title: "Is samba really this slow?"
date: 2008-09-10
forum: General Help
---

### Post by jerome1232 on 2008-09-10
Samaba was copying at ~ 300 Kilobytes per second over a 54 Megabits per second connection. The file server in this case was actually a Windows Vista Laptop

54 mb = 54,000,000 bits
8 bits = 1 byte
54,000,000 bits = 6,750,000 bytes
1024 bytes = 1 Kilobyte
6,750,000 bytes = 6,591.8 Kilobytes
1024 Kilobytes = 1 Megabyte
6,591.8 Kilobytes = 6.44 Megabytes
20% of that is 1.28 Megabytes

Doing the math that's about a 6.44 Megabytes per second maximum connection speed. (overcourse with wifi there's more overhead and transmission errors so I understand you'll get about 20% of maximum so that's 1.28 Megabytes per second realistically).

So just to see I copied the files over to a computer via sshfs protocol and I got ~ 800 Kilobytes per second, now that's a huge difference and it's close to what crunching a few numbers said I should be getting! 

This network only has 4 computers on it one of which was turned off and nothing was accessing the internet during any of the transfers. The only difference was this time the connection was between a 54 mb/s wifi desktop and a 10 mb/s ethernet connection. Both wifi computers are roughly the same distance from the router and in the same room with excellent signal so I don't think that is a factor either. btw the 10 mb/s ethernet comes out to 1.19 Megabytes per second so it's a slower connection than when I was connectiong between two wifi's.

---

### Post by Sycron on 2008-09-10
If you copy a large amount of small files then the speed is much more slower than if you copy a single file with the size of all those small files.

I have too a 54Mbps wifi connection and yes, is slow when it comes to transfer file from another computer on the network.

---

### Post by jerome1232 on 2008-09-10
Yeah but sshfs was nowhere near as slow, even over a slower connection.

But I was transfering alot of ~3 MB files using samba and one large file using sshfs so I will retest with a large file

800 KB/s sshfs compared to 300 KB/s using windows file sharing

The windows file sharing was done with a 54 mb/s - 54 mb/s connection
The sshfs was done with a 54 mb/s - 10 mb/s connection and was considerably faster.

---

### Post by jerome1232 on 2008-09-10
Okay so tested with a large file over samba ~370 KB/s, still much slower than sshfs, I'm considering ditching samba in favor of ssh, I think I can install ssh servers on the windows machines.'

edit: wow I spoke to soon, after the first few seconds samba drops to 187 KB/s, where as ssh maintains at 675 KB/s (the 800 was only first few seconds it looks like)

---

### Post by zabby on 2008-11-12
I'm having the same problem.  Does anyone have any advice?



I'm trying to dump the HD contents of a laptop w/ the 8.10 liveCD over the network.  I mounted a Samba share and stared to copy... but I'm getting pathetic speeds... at this rate it won't be done for two days!

Any help would greatly be appreciated.

---

