---
title: "Can't dist-upgrade from hady to intrepid"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by radu_radu on 2008-12-22
As the title says, i can't dist-upgrade from hardy to intrepid. I have a computer that haven't been updated for 6 months; decided to go directly on intrepid, and ran dist-upgrade. So it pulled a lot of new packages, all went fine, but lsb shows it's still hardy. Dist-upgrade doesn't want to install any new files. I've selected from Software Sources to show all releases, not just LTS ones, but still nothing.
Any idea on how should I go ?:confused:
I was thinking of replacing by hand all "hardy" with "intrepid" in apt/sources.lists and run full-upgrade - will this work? Or it will break everything?

---

### Post by gerkin on 2008-12-22
radu_radu

"dist-upgrade" is probably not the way to go

Check out the upgrade instructions here:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

I have done several upgrades following the instructions near the end of the page where i:

"Upgrading Using the Alternate CD/DVD" .... which have all gone faultlessly

If in doubt download the alternate CD and give it a go

cheers ...........dave

---

### Post by oygle on 2008-12-22
I need to retrieve all the .debs for an upgrade to 8.10, on a 64-bit box. If I view this file - [http://releases.ubuntu.com/intrepid/ubuntu-8.10-alternate-amd64.list](http://releases.ubuntu.com/intrepid/ubuntu-8.10-alternate-amd64.list) , I can see the list of .debs there. So, would that be a complete upgrade to 8.10 (i.e. all the .debs) ?

I want to retrieve the .debs rather than download the ISO, as the connection I'm using to download is a little bit unreliable, and therefore a high risk of file corruption by downloading one huge file, better to download many small files.

The .debs seem 'self checking' anyway, if I run a script with the wget command, and then if I run it again, wget comes back with a msg about file already retrieved.

That file list seems to be comprehensive. Of course, I would still have updates to apply since then, but that's okay.

Oygle

---

### Post by radu_radu on 2008-12-22
Thanks for the tip, **gerkin**
Will try it when I'll get home.
One thing, though: I remember having installed Ubuntu - but I also pulled up Kubuntu base and a lot of KDE stuff; also, I use mostly KDE. The alternative CD will upgrade my basesystem to Intrepid, right? and the rest will come off the net. (I don't have any connection problems)

---

