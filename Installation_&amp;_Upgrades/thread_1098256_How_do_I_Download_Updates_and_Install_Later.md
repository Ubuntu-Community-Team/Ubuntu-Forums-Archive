---
title: "How do I Download Updates and Install Later"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by ASolano on 2009-03-16
Hi All,

I have just convinced my brother to make the switch to Ubuntu.  As a result I have 3 PCs (all with different specs) that need to be wiped and have ubuntu 8.04 installed.

My problem is that after the installation I will have 3 PCs that will all need updates (currently over 300Mb) and although I have ADSL2 (12mbit .. I'm far from my exchange) it only seems to download at 30Kb, i.e. it takes about 3-4 hours to download.

So what I needs is a way to download the updates, manually copy the files to each PC, then run the updates using the downloaded version (i don't fancy the option of setting up a proxy server, download the files once, then have each new pc download from the proxies cache)

Ideally I'd like "Update Manager" to do the downloading, then on the new PC's, drop the files into a location that "Update Manager" will be able install from.  Or better yet, download the correct files from a faster source (using a download manager or torrent client or any other technology that's faster then Update Manager)

Any instructions or links to how to's would be greatly appreciated

---

### Post by Cheesehead on 2009-03-16
You might reconsider setting up a caching proxy or p2p client on one of the machines - you will have the same problem each time a big upgrade or new release comes out. apt-cacher-ng and debtorrent have worked for me in the past.

---

### Post by lavinog on 2009-03-16
There is a program called apt-cacher that should do what you want, but it might be easier to just update one machine, then copy all of the deb files in /var/cache/apt/archives to the other machines that need updating. That should reduce the download significantly

---

### Post by ASolano on 2009-03-17
Thank you very much lavinog!  I tried out your solution last night and it worked perfectly.  3 machines done, 0 downloads used (I got the files from one of my existing PCs) 1 happy installer.

I can verify that the updater only installed the packages that it identifed as being needed (the files from my existing PC included other packages), I was concerned that Update Manager would install any package it found in the archive folder, thankfully this was not the case.

I would like to know if update manager does any verifying on the packages in the archive folder.  So if anyone knows if this is happening I would appriciate the response, but for my purposes I'd say this question has been solved.

Just a nice little summary, the following is what I did

ON A CURRENT PC

1. Use Update Manager on 1 PC (to download the files)

2. Copy the files (exclude the locked file and partial folder) in the folder /var/cache/apt/archives (I used a USB drive)

ON THE NEW PC

3. In the Terminal copy the files using sudo (you need root access to write to the folder /var/cache/apt/archives) i.e.

```
sudo cp <source>/*.deb /var/cache/apt/archives/

```

4. Run the Update Manager

NOTE: After you copy the files to the new pc, you'll notice a grey version of the Update Manager icon will appear (indicating that Update Manager is processing) even if Update Manager is not running at the time.

---

