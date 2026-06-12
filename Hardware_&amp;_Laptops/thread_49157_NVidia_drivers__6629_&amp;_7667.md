---
title: "NVidia drivers : 6629 &amp; 7667"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by avelldiroll on 2005-07-15
Hello,

I am having 3 issues with nvidia drivers :
- I need to have support for TNT2 cards, and that means using the (=) 6629
- I need to have support for 7800 cards, and that means using the (>=) 7667
- and finally I need to have some bugs corrected for Quadro cards, and that means using (>=) 7664

In Hoary right now only 7174 is present in the reps.

The easy way  to install them is the nvidia installer (nvidia_pkg.run), but I have got quite a lot computer to manage (~100), so I'd like to know if those drivers will be included in the repositories (or in the backports).
If their is no chance for them to be included, i think i'll package them myself next week.

Thanks for any reply.

Cheers

---

### Post by apollo2011 on 2005-07-15
It is recommended that you first follow the directions found at the link below:

[https://wiki.ubuntu.com/BinaryDriverHowto?highlight=%28nvidia%29](https://wiki.ubuntu.com/BinaryDriverHowto?highlight=%28nvidia%29)

If  you have problems with that, and you shouldn't, then you should try the driver off the Nvidia site.  Otherwise, the one that comes in the Ubuntu repositories should work fine.

---

### Post by FLeiXiuS on 2005-07-15
Yes the 7667 drivers posed a lot of threats that Jdong and others didn't agree with.  Thus why they aren't in the backports.

Follow the WIKI it'll furhter explain what you need to do.

---

### Post by avelldiroll on 2005-07-18
Thank's, but my question was not about installing the nvidia drivers (any flavour of them), 
but automating installations on different systems ...

Indeed, the different nvidia drivers have specific isues depending on what card you are using :
- 7174 works well for Geforces (that's why it is the only one in the reps)
- 6629 was the last to support TNT2 cards
- 7664 fixed some huge bugs in 7174 for quadro cards
- 7667 while being buggy is the only one to support 7800 cards

The problem is not  installing those different drivers, but managing different installations (~100 computers) equipped with different nvidia cards. As the easiest/laziest way is to use apt-get I was just asking if those drivers were planned to be added to the reps in the future or not (if not i will make my own, probably building a deb package for 6629 and 7667)

Cheers

---

