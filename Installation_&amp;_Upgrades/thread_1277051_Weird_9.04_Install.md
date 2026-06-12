---
title: "Weird 9.04 Install"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by hoosemon61 on 2009-09-27
Ok, I'm not sure what happened here at all.

I'm going to give you the whole story instead of just the last bit, just in case the earlier stuff helps.

I was running an previous version (Dapper maybe?) on an older machine - celeron, 512 MB Ram - 10GB HDD - slowly but without a problem.

It had a CDRW but nothing that would read DVDs.

I installed an older DVD ROM I had laying around.

It started acting funky, but mostly it would see the DVD but not mount it.

I realize now it might just have been a driver thing, but I thought why not try 9.04 instead?

I also decided to try a larger HDD since I had a few laying around.

I tried installing 3 times on a 20GB drive, and I'm pretty sure the errors I got were telling me the drive is bad.

I then found an 80GB western drive I missed the first time and tried again with that.

Install went fine, only message I got was a warning that it was selecting a lower level graphic mode because I don't have a discrete video board.

Here's the weird part.....

It works fine, but the version of Ubuntu installed is 7.10!!

I checked the CD and it definitely says 9.04.

I checked the repositories in synaptic package manager and they're all trying  (and failing) to upgrade from Gutsy repos.

I'm using the machine now, so it works, but how did I get 7.10 from a 9.04 install CD and what should I do?

:confused:  Hoosemon

---

### Post by stlsaint on 2009-09-27
maybe you had an older version on ubuntu on there previously or something...does sound pretty weird...i recommend formatting the hdd prior to installation thru system>admin>partition editor then going back to desktop to click the install button.

also consider re-downloading and reburning the disc. check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") also.

---

### Post by hoosemon61 on 2009-09-27
You're right.  Sorry, really dumb on my part.

I went back to reinstall and found that during partitioning there was an old Win 98 install as well as a 7.10 partition.  

In my haste I chose "install along side" rather that "use entire disk".

Hopefully that'll get me going.

Thanks!

Hoosemon

---

