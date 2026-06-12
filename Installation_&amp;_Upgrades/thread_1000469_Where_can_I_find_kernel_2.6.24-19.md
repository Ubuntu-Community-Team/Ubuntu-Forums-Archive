---
title: "Where can I find kernel 2.6.24-19?"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by Syd35 on 2008-12-02
I no longer have kernel 2.6.24-19 on my recent Toshiba laptop and I would like to re-install it as it is the only one with which my Atheros AR5007 wireless card functioned at all. Originally I used that kernel successfully for Ubuntu 8.04 and now would like to use it in 8.10 Ibex.
Where would I find it and how is it installed please.

I'm very desperate to get my wireless network back up.

Thanks,

---

### Post by duanedesign on 2008-12-02
at the bottom of the page you will see Download linux-image-2.6.24-19-generic and a place to  select i386 or x64. This will take you to a page where you select a mirror.

[http://packages.ubuntu.com/hardy-updates/linux-image-2.6.24-19-generic](http://packages.ubuntu.com/hardy-updates/linux-image-2.6.24-19-generic)



here is a link to the public Linux archive. If you keep scrolling down you will get to the 2.6.24-* I think you have to compile this one though.

[http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)

---

### Post by Syd35 on 2008-12-03
Thanks Duanedesign. Thanks for your suggestion. Unfortunately I don't see the kernel I was seeking; perhaps I have the numbers wrong. If I do get this right and I choose one, which version do I download? ".tar.sign" or "tar.gz"

Thanks again

---

### Post by duanedesign on 2008-12-03
I would go for the .deb off the Ubuntu site. I updated the first link, you might try that one again and make sure.
here is a link straight to the mirrors (edit) this is 32 bit

[http://packages.ubuntu.com/hardy-updates/i386/linux-image-2.6.24-19-generic/download](http://packages.ubuntu.com/hardy-updates/i386/linux-image-2.6.24-19-generic/download)

make sure you keep another kernel installed so you can still boot up if something does not go right. I havent cleaned mine off in awhile and I have 3 kernels on mine:)

---

### Post by Syd35 on 2008-12-03
Thanks. I downloaded 2.6.24-19 and at least the card sees the network now, or vice versa, but no connection yet. I'll persevere.
I have the kernels which came with U 8.10 when I downloaded it. I have seen that the new kernels incorporate  "ath5k" which seems a combination of Madwifi and some other which I forget. I would like to get the wireless going eventually with the new system.
You have been a great help, thanks

---

