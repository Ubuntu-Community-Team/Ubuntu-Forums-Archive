---
title: "Whats the best thing to do with 2 500gb drives"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by tobycatlin on 2007-11-15
Hello everybody,

I just wanted some advice. I have just built a new machine to serve as a media centre. I bought two 500gb drive to use as mass storage. At the moment i just have them mounted as single drives and am manually syncing my photos and other files using rsync. I know it's possible to use raid to combine the two drives into one mount. would it be possible to add a new drive? say a new 750gb later down the line. Also how would i go about setting up some kind of redunancy on the whole setup? 

I'd love to know how others have setup large storage systems.

thanks

toby

---

### Post by kragsterman on 2007-11-15
Hi, Toby! You need to study LVM2 and md raid to be able to get a nice setup. My recomendation is that you grab a 10 Gb drive and install system on it, and then create LVM and md devices of your bigger drives. Basically you create pools with LVM, and then carve out slices, which you later can put together to raid sets. Yes, you can add more drives later. Rgrds JK

---

