---
title: "Getting Synaptic to update on slower networks"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by mingtien on 2009-05-17
I'm just wondering if there is some possible means by which to optimise Synaptic / apt-get / Update Manager for those of us at the slower end of the Internet:

My Internet connection comes from a wireless broadband dongle (EVDO/CDMA), which is not blindingly fast, but adequate for everyday work (about 256k, which is nowhere near proper broadband, but still usable).  I can download a 2.4 GB DVD iso in about 5-7 hours, and getting Ubuntu CD iso's via torrent is a doddle.  I can even watch Youtube videos without having to cache them first (most of the time!).

But this, it would appear, is not sufficient for Synaptic -- no matter which repository mirrors I assign.  Reloading package lists after changing repositories fails 100% of the time (especially the dreaded Translation-en_GB), and the only way to do an update is to go to somewhere with relatively fast Internet (rarely convenient).  I've attached some typical errors below...

Is there any way to give Synaptic a shot in the ars^H^H I mean arm?  

I've had a look at the configuration files in the .synaptic directory in /root, and didn't see anything that seemed appropriate.

```

GPG error: http://gb.archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: NODATA 2GPG error: http://gb.archive.ubuntu.com jaunty-security Release: The following signatures were invalid: NODATA 2GPG error: http://gb.archive.ubuntu.com jaunty-proposed Release: The following signatures were invalid: NODATA 2GPG error: http://gb.archive.ubuntu.com jaunty Release: The following signatures were invalid: NODATA 2Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages.bz2  
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2  
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2  
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages.bz2  
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages.bz2  
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2  
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2  
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/restricted/binary-i386/Packages.bz2  
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/main/binary-i386/Packages.bz2  
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/universe/binary-i386/Packages.bz2  
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/multiverse/binary-i386/Packages.bz2  
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2  
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2  
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages.bz2  
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.bz2  
Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by hackapelite on 2009-05-17
I think you have a problem somewhere else; I have a dead slow (i.e. typical Aussie) broadband, I get around 50-60KB/s down (256kbps), downloading the Ubuntu CD took 4 hours and whether I have to cache uToob videos is usually a matter of luck; but I never have any trouble downloading packages, or refreshing the lists, even on a bad day when I get around  30KB/s down and/or have other downloads running...

Having said that, I can't tell *what* could possibly be wrong. Do you often get errors loading web pages (connection to server reset, can't find, unable to connect to, or just broken/incomplete loads)? How about other downloads (BT excluded since it has error checking)? If you have no other troubles with the net (except for the speed), I would definitely look for the problem somewhere else...

---

### Post by jerrrys on 2009-05-17
i agree...except for time, the download speed has nothing to do with it...

---

### Post by mingtien on 2009-05-17
hackapelite: NO other errors or problems really.  On bad days (about 1 morning a week) some web sites can be slow, but they load eventually.  I got the Windows 7 DVD iso from Microsoft's site in the USA (that took about 10 hours, but I suspect that part of that was high demand)... ftp works fine (actually, surprisingly fast), and big email attachments are okay (well, except IMAP, which is slower by nature due to syncing).  Dropbox works  (I forget what protocol it's using), and the various Conduit syncing mechanisms work reasonably (I won't say fast).  

It appears to only be Synaptic that times out and fails -- it did the same under Intrepid, and only for updates.  I can apt-get or use Synaptic to download and install libs and packages with few worries (packages with a lot of dependencies need to be apt-got a few times to get all the bits and bobs).

It seems that update gives up too easily -- it tries to get a file (bz compressed package index), and if it doesn't come immediately, it fails it.  After it has reached the end of the index files, rather than ending, it 'sits there' -- indefinitely, not trying to download the bits that it missed.  If there was some way to set the timeout on that to hold on for a bit longer than 30 milliseconds, or to retry at the end of the update, that would be very helpful.

---

### Post by mingtien on 2009-05-17
Not sure if this helps: the point where Synaptic (or apt-get) gets 'stuck' is on Translation-en_GB for each repository -- I've attached a screenshot.

---

### Post by mingtien on 2009-05-20
I'm still hoping to find a solution to this problem, as Synaptic is unable to update unless I'm connected to a faster (ie. wired) connection -- when the current connection should really be sufficient.  Any suggestions would be greatly appreciated!

---

