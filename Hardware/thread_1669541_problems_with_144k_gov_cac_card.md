---
title: "problems with 144k gov cac card"
date: 2011-01-17
forum: Hardware
---

### Post by brjaan on 2011-01-17
I have been reading the numerous on how to setup cac readers using coolkey and pscs tools I hope that i spelled that correctly. I had it working with my old cac card. I then tried ubuntu 10.10 which i was not a big fan off hopefully they have worked some of compatibility issues since then. I had upgraded from 10.04 and it could not recognize any cards I put in the card reader. Im back using 10,04 which I love but am having difficulties with my new cac card which is the new 144k card. I have read all over the forums and found workarounds for both 10.04 32bit (mine 64bit) and 10.10 32bit I was wondering if any military folks had figured out how to get this work on a 64bit machine using Lucid linux 10.04 LTS. I am a beginner.

---

### Post by zbert on 2011-01-24
I posted a fix for this in my blog: [COLOR="Blue"]**[http://blog.skeltonnetworks.com/2011/01/fixing-libcoolkey/](http://blog.skeltonnetworks.com/2011/01/fixing-libcoolkey/)**[/COLOR]

Basically, remove the repo version of libcoolkey (and libckyapplet1 & libckyapplet1-dev) and replace it with the 1.0.7 'experimental' version and it will work with your 144k CAC card.  If you're registered with [COLOR="blue"]**[https://software.forge.mil/](https://software.forge.mil/)**[/COLOR] there is a 'cackey' module in the Community CAC project that addresses this problem as well.

Zack

---

### Post by brjaan on 2011-02-08
Thank you your information combined with what I could piece together from the web worked well. I am now able to use my cac card with ubuntu 10.10 success yeah):P

---

### Post by brjaan on 2011-03-07
Help cannot redo are replicate what you wrote here. I went to your link but it is telling me that the downloads are not available when I try to wget the info and it does not work.

---

### Post by brjaan on 2011-03-13
I figured it out the download information on your post is dated and no longer works. I went to debian website and downloaded the current version of coolkey and it worked like a charm. [http://dl.dropbox.com/u/22808663/coolkey_1.1.0-8_amd64.deb](http://dl.dropbox.com/u/22808663/coolkey_1.1.0-8_amd64.deb) the current version of coolkey solves all the issues I had with the 144k cac card. Coolkey 1.1.0-8 for 64 bit computers. This will only work on 64 bit computers for 32 bit you'll go to the debian website to download the 32 bit version.

---

