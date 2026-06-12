---
title: "Amarok + Creative Zen Xtra with njb not show option"
date: 2008-02-07
forum: Hardware &amp; Laptops
---

### Post by sexus6 on 2008-02-07
Hi
I read various posts about Amarok  Creative Zen Xtra's support.

[http://ubuntuforums.org/showthread.php?t=316246](http://ubuntuforums.org/showthread.php?t=316246)

[http://ubuntuforums.org/showthread.php?t=18058](http://ubuntuforums.org/showthread.php?t=18058)

but for me does not works this sollutions :(

I compile amarok (1.47, and 1.48 for testing) with => ./configure --with-njb --with-mtp --prefix=`kde-config --prefix`

And all the compiling is ok.

To add my Zen xtra, I go to the device list and try MTP device. This does not work. There is not another entry that I read that uses Creative Zen Xtra.

I test gnomad2, and this soft can connect to my Zen Xtra, but the soft is very poor,  I want to make amarok's support.

for some info, when I run gnomad2 by the console:
LIBMTP_Get_First_Device: No Devices Attached
This is a PDE device

If there is not a mtp device, amarok can't get them?

Please help

---

### Post by glisignoli on 2008-03-26
I found that I could use my Zen in ubuntu (8.04) as long as the package mtp-tools was installed.
Seemed to work fine once that was installed.

---

### Post by sexus6 on 2008-05-13
Yes!
In ubuntu 8.04 works... 

Another problem....
I want to transfer all mp3 files DEVICE=>AMAROK COLLECTION.
The transfer button is greyed.
I can transfer with contextual option DOWNLOAD TO COLLECTION, but only download showed files. The default device list shows only icon artist. I can click to + button to show artist content, and see albums. If I click to + button in each album, I see the tracks within....

If I select one artist (or all artist list) and click DOWNLOAD TO COLLECTION, only download files that are opened. If I don't  open and see list of tracks, I can't download. 

This is very tedious because to download all my mp3, I has to openl ALL artist and albums to see each file. Is there another easy way to select all files to download? Why transfer button is greyed? is there another way to sincronize my device with my pc?

I don't want gnomad2, has too much bugs and there is no option to use directories at downloading to pc.

Sorry for my poor english

---

