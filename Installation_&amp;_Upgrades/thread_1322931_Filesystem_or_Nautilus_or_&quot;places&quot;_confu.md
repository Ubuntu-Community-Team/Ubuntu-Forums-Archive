---
title: "Filesystem or Nautilus or &quot;places&quot; confused"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by audiomick on 2009-11-11
Hallo.
The "Places" links in the panel are doing weird things
This problem relates (of course) to a computer that belongs to a friend, that I was intending to fix. :redface:

It is a HP laptop with a 60G HD and about a 1.4 gig single core processor, maybe 3 years old. It has been happily running Ubuntu 8.04 LTS the last couple of years. The HD was set up with a / partition and a /home partition. File system ext3. System language is German

I was called to help last week, because the problems had started with pictures in Open Office not appearing. Funnily enough, they were visible in the version that was saved as .doc, but not in the .odt version.

I discovered that the / partition was 100% full. Actually had maybe 400MB free, but not available.

I got a new 9.10 Live CD happening, which also checked ok using it's own checking fuction, started Gparted and made some more room for / at the cost of /home

A boot after this showed that all was still there, pictures were once again appearing in .odt files, and apparently all was well. In hindsight, I probably should have left it alone at that.

I had agreed with the owner to do a new install to 9.10, which I did, leaving both partitions as ext3 file systems.
Theoretically, if the /home partition is left untouched, then the computer should come back the way it was, less the additional programs that one has installed in the course of time. I have proved this several times with my own computer.
In this case, it did come back, e.g. Evolution still works, all the files seem to be there etc.

but...

If I go to Places in the Panel and try and open something, I get the following:

All the appropriate links are there, e.g. a folder on the desktop, some folders in the Home folder, in short, that which is supposed to be there

The link to "computer" works. The file manager starts, it is possible to navigate through the file system to all the folders, open things etc.

Other links either do nothing ( personal folder ) or try and start a music player ( e.g. desktop and a couple of the other listed folders)

I suspect, of course, that the partition changes have corrupted something, and that it will need a complete fresh install, including all partitions, to get it back on the straight and narrow.

Does anyone know anything to the contrary?

Thanks for reading the problem, at least
Michael

---

### Post by darkod on 2009-11-12
Sorry, I have no clue. As I said, I am not expert in Ubuntu. It's just that I was in a situation to plan partitioning a few times. I can discuss partitions but could not troubleshoot something like you describe.

---

### Post by audiomick on 2009-11-12
OK. Thanks for looking

---

### Post by audiomick on 2010-01-03
solved with this thread
[http://ubuntuforums.org/showthread.php?t=1352582](http://ubuntuforums.org/showthread.php?t=1352582)

---

