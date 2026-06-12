---
title: "There should be three FGLRX branches..."
date: 2013-02-26
forum: Hardware
---

### Post by MilesRdz on 2013-02-26
I noticed on Ubuntu 12.10 that there's only fglrx and fglrx-updates and they are out of date.

There think they should make it so that it's:
***fglrx-legacy*** - latest legacy drivers, always
***fglrx*** - latest stable drivers, always
***fglrx-experimental*** - latest beta drivers, always

I think it would be a much better experience that way. 
I'm not a huge fan of installing FGLRX manually to have the latest driver (though I must with Steam).

Is there any PPA that doesn't upgrade Xorg or the kernel that caries the latest FGLRX beta drivers?

Thanks.

---

### Post by Yellow Pasque on 2013-02-26
There are a couple problems with that:
1. fglrx-legacy branch doesn't work on Ubuntu 12.10 without downgrading the Xserver, and unless AMD's policy of not introducing new X support in the legacy branch changes, that will continue to be the case.

2. Ubuntu likes to stabilize fglrx version for each release and offer fglrx-updates

---

