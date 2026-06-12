---
title: "System Recomendations"
date: 2008-12-18
forum: Hardware
---

### Post by StephenD on 2008-12-18
We recently bought a new network printer with a feature that is not compatible with Active Directory.  I am currently looking into getting a new server to take advantage of this feature.  I am not looking to rebuild our server simply add another computer.

What I need is a simple file server the printer can save scans to.  It only needs to serve a handful of files at a time. 

If I do this it will be with something purchased off of ebay or craigslist for $25-50 and I was wondering what you would recommend as the minimum for this system, and which variant of Ubuntu to use?

Thank you very much.

---

### Post by nixscripter on 2008-12-18
Having dealt with junk computers before, and seen some performance characteristics, I would recommend a Pentium III 500 MHz and 384 MB RAM to do anything with Ubuntu. I have purchased several computers for $35 on Craig's List which are faster than that -- prices may vary in your area.

If you are building any kind of server, especially one which acts as shared storage, you will probably want at least 800 MHz and 512 MB of RAM, as well as a 1 GB network card and a rather large hard drive (or a software RAID array of multiple small ones, but that's if you're really cheap ;-) ).

Also, make sure to get Ubuntu Server Edition, to save a lot of overhead on junk, and share the files over SMB (or NFS if you can). I'm afraid I haven't installed the Server Edition -- I'm a Gentoo fan, myself -- but that's what Google is for.

Hope this helps.

---

