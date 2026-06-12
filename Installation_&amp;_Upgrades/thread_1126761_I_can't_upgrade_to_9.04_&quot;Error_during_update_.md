---
title: "I can't upgrade to 9.04: &quot;Error during update: A problem occured during the update.&quot;"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by cryptoz on 2009-04-15
edit: I fixed the problem. How do I delete my post? I was being an idiot. I disabled an entry in my software sources list and the issue was fixed. I want to delete and keep the forums clean but I don't know how. Thanks.

Hi,

I run Ubuntu 8.10. I used to run 8.04, then I upgraded to the 8.10 beta when it was released. I then updated to 8.10 full when it came out (I think I did, anyway. How can I check to make sure?).

I would like to upgrade to 9.04 beta (or full, when it comes out) but I cannot. If I run update-manager (with -d or not), I see:

Not all updates can be installed

Run a partial upgrade, to install as many updates as possible.

This can be caused by:
- A previous upgrade which didn't complete
- Problems with some of the installed software
- Unofficial software packages not provided by Ubuntu
- Normal changes of a pre-release version of Ubuntu

[Partia]  [Ok]

If I run with -d, and get past the dialog (Ok) and click on the 9.04 install button, it goes through some of the then gives errors. The errors are titled "Error during update: A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry". Below that, it says:
----------
W:Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add newt CD-ROMs
, E:Some index files failed to download, they have been ignored, or old ones used instead.W:Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add newt CD-ROMs
, E:Some index files failed to download, they have been ignored, or old ones used instead.
---------

I don't know what all the cd-rom talk is about. I don't think I've ever inserted a CD-ROM into this computer since I installed 8.04 for the first time last year.

I have other problems with Ubuntu that don't bother me but that might be related. If I click on Places -> Computer in GNOME I see "Could not display Computer: Nautilus cannot handle "computer" locations".

Same goes for network drives and trash. I've been using the console or KDE when I need to do tasks like those.

Anyway, I really want to update. Last time I googled around for the "computer locations" problem around a year ago, the concensus seemed to be that I needed to completely re-install. I'm not willing to do that. If there's another way around that, that would be helpful. But that may not be related, and I don't particularly care that I can't access "computer locations" (I'm only mentioning because I feel like it might be related.)

So the real problem is interpreting these updating errors. Can anyone help? Thanks!

---

