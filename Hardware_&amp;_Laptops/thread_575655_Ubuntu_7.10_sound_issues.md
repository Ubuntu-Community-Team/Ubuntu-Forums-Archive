---
title: "Ubuntu 7.10 sound issues"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by igggyc on 2007-10-14
Hello

I have just installed the pre-release of Ubuntu 7.10 Gutsy Gibbon with just 4 days until its release on my Dell Inspiron 1720. Everything appears to be fine, except I can't get my soundcard to work.

According to dell and my motherboard settings, the soundcard is a Sigmatel 9205.

I looked briefly on google and found this link:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

which seemed to address my problem. I followed the instructions there, my sound card still is not detected. the volume control symbol is crossed off by a little red circle and no sound plays.

At first I thought maybe the drivers provided on the link were wrong, so i went to the following site:

[http://www.gtlib.gatech.edu/pub/suse...apshot/driver/](http://www.gtlib.gatech.edu/pub/suse...apshot/driver/)

and downloaded the following file:

alsa-driver-hg20071013.tar.bz2 and followed the first link's intructions on unzipping this file, yet still nothing works.

i must add i am not an experienced user, so any help for idiots such as myself would be greatly appreciated. i should also add that command: cat /proc/asound/card0/codec#* | grep Codec

comes back as invalid and fails to retrieve my codec info. it says "no such file or directory".

any help appreciated!!!!!

p/s/ all the unzipped files are in a directory caleld "alsa" located in home folder...

---

### Post by arkara on 2007-10-14
try to boot with acpi=off

---

### Post by igggyc on 2007-10-14
where do i turn acpi off??? bios settings???

---

### Post by omegamormegil on 2007-10-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/131133](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/131133) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It's a bug.  Follow the link above to the report.  Hopefully this will be fixed in time for release.

---

