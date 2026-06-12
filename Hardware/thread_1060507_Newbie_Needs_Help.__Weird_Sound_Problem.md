---
title: "Newbie Needs Help.  Weird Sound Problem"
date: 2009-02-04
forum: Hardware
---

### Post by dnixon on 2009-02-04
Hi all. I could use some help if someone knows the problem. Installed Ubuntu 8.10. Runs great. When starting the Ubuntu music plays crystal clear. As soon as that music is finished, any other sounds are mostly static and you can hardly understand anything. Using SBLive! Value cT4871 (alsa mixer). I see nothing about this in forums and would appreciate some help. I'm at a loss and hope someone with experience can help. I can put code in terminal window if you have that info. Still learning the ropes.
Thanks!
Doug

---

### Post by byStanderone on 2009-02-05
hi,
...sounds like a driver problem, try loading the patches from the ubuntu backports:

sudo gedit /etc/apt/sources.list   (uncomment this line by removing # in 
                                        front of it)

# deb [http://archive.ubuntu.com/ubuntu/intrepid-backports](http://archive.ubuntu.com/ubuntu/intrepid-backports) main restricted universe multiverse

save and exit...then sudo apt-get install ubuntu-restricted-extras

---

