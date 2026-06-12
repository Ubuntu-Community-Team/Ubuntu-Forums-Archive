---
title: "Need a bunch of advice"
date: 2008-05-11
forum: Hardware
---

### Post by Squish on 2008-05-11
Well I am going to need to network a bunch of computers together using mac and linux, and I am looking to buy some hardware as well. Some advice would be appreciated.
Essentially this is a gig for my new job up at a childrens camp:
I am trying to keep this post simple:

Existing Hardware:
3 Macintosh running tiger
1 System76 Serval Performance Laptop, running ubuntu
1 Custom built tower running ubuntu and xp, however will be tweaked based on advice.
1 750gb External Harddrive

Hardware in which I will be buying:
1 Canon HV30 Camcorder + accessories

Possible Hardware/Software I need advice on
2-4 New Harddrives
Networking
Raid Controller
Linux Distrobution

Basically, I am a video editor, which explains the mac's. I want to centralize the storage of video that I, and my assistants will be editing. I thus want to take the custom built desktop, and have all 4 computers (3 macs, and my laptop) use it as the central storage database.
So, in order to do this, I will need to network these computers. Because it is video, I want the highest transfer speeds I can get.

Here is my questions:
1: The desktop currently houses 2 x 250 gb harddrives. Because I will be doing video in HD, I will need substantially more space (how much more, I am uncertain). Because it is valuable video, I want to make sure I can back it up. What harddrives should I buy that will give me good a "gigabyte per dollar" ratio, and what raid scheme would be advisable for setting them up?

2: I want fast transfer rates because of how large the files are. What router should I get that will support the 4 computers (and the external as well would be nice), and will give me the fastest transfer rates over Ethernet.

3: The desktop will likely not be used because of 4 other ample computers, thus it will be fairly dedicated to the task I give it. In order to improve performance, would I set up a server on the desktop? What type of partition should I use? Should I go with ubuntu server or desktop, 64bit or 32 bit? Would buying a raid card increase performance for the networking?

4: Random Questions
Can kino handle high definition dv?
Any news on jahshaka?
Do PiTiVi plugins actually exist?
I want a soundcard that sounds amazing under linux. What is a good soundcard for linux, that not only works, but actually sounds amazing like its supposed to?
Can I install ubuntu on these powerpc Imacs?
Anyone know if its possible to get my WMPGRX54 wireless card working under linux?
Can I do remote sessions with the macs using my laptop (vinagre anyone?)? My lappy is a powerhouse, with 4 gigs of ram, so if it was hooked up to a network, then I could essentially enjoy the outside while editing video.

I usually buy top notch equipment, so I dont usually like to stinge for cheapo stuff. Just as long as I dont hit over 800 dollars for this equipment, I should be satisfied... although cheaper is better. I dont want to do overkill as well.

Oh and feel good, because this is work for a non-profit organization, in which I am trying to get them to switch over to free and opensource software. If luck has it, they will make me the IT guy, so I can install ubuntu on all their workstations. I tried doing that last year, but the IT guy that year, completely spazzed out... which was unfair because I was setting up the computers which was supposed to be done months ago by him.

---

### Post by rs3 on 2008-05-11
RAID hardware tends to be quite expensive.  If you're trying to meet an $800 budget, you'll have to do some serious digging to find hardware RAID at that price.

That said, you can still see some performance and (of course) redundancy benefit if you go with software RAID.  You'll need to run an alternate installation disc of Ubuntu to configure software RAID.

The ideal RAID array and configuration scheme will differ based on how many hard drives you acquire.  If you get two, you'll want to do RAID 1 for mirroring (one HD copying the other at write-time).  If you acquire three or more drives, I would recommend RAID 5 to allow you to take fair advantage of space and still offer redundancy.  (RAID 5 on three drives would get you about 65% of the total space between them and offer one drive redundancy.)

As far as network performance goes, I would opt for a Gigabit ethernet switch or any router that offers these speeds to connected (wired) clients.  [This]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833124262") router/switch/AP combo device might suit your needs fine if it has enough ports for you.  You'll be hard pressed to find more than four wired clients to a router, and you may need to buy a separate switch for multiple clients.

With regard to using the desktop as a server, I'm not terribly knowledgeable on the subject, but perhaps you could create a partition from your RAID array to use as a Network File System (NFS) mount.  I would probably recommend using JFS or ReiserFS for speed, but again, I'm not terribly knowledgeable here. :D  I do understand, though, that JFS offers good speed and self-maintenance features at a small CPU cost, and ReiserFS will harness lots of CPU time for fast writes and reads.

The PowerPC arch was discontinued with Ubuntu as of (I think?) 7.04.  There might be an unofficial port of Ubuntu somewhere, but if you want to get a current, supported Linux-based operating system for the PowerPC Macs, you may have to go with Fedora (Fedora 9 is coming out in a couple days) or Debian (if you want something that retains a lot of the best core features of Ubuntu, such as the package manager). 

With sound, I had decent luck with the M-Audio Delta Audiophile.  The default Ubuntu/GNOME mixer was a bit obtuse, but ALSA and JACK support for the card are quite good, and Ubuntu Studio should work very, very well with it.

As far as 64-bit and 32-bit go, well, I have had issues getting some things to work with the 64-bit arch (most recently with Hardy; I stepped down to 32-bit and have not had issues since) but if you're using it as a server, I would try 64-bit.  You're especially likely to see better performance for tasks involving data throughput, so it would be a good match.  (Also, 64-bit will be necessary if you intend to address 4GB or more of memory; 32-bit will truncate your available memory to, I believe, 3.2GB.)

I don't know much of anything about video; hopefully someone else here will!  You may want to try the Multimedia Production forum if you have not already.

---

### Post by Squish on 2008-05-11
That was a great reply man, I really appreciate it.

This is what I am thinking then for a raid scheme

2 x 250gb in a Raid 0, or a raid 1

4 x 500gb or 750gb in a raid 5.

Software raid it is, although my mobo offers it onboard as well. I havnt been ever able to detect it with ubuntu though.


oops, gotta jet, finish this post later

---

