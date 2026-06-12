---
title: "Move the Grub"
date: 2008-05-13
forum: Hardware
---

### Post by black_knight on 2008-05-13
I have ubuntu Hardy installed on an external HDD and windows on my internal. The grub was installed on the external.
How do I move the Grub to my internal so I can boot into windows without having to make sure my external isn't plugged in...plus for on the go occasions.

I have tried sudo grub-install hd1
and on hd0 but to no avail. It still boots from the grub on my external.

So the all mighty question is, how do I move the grub loader onto my internal so it will load from my internal?:confused:

any help appreciated.

---

### Post by zenwalker on 2008-05-13
Make the non-external HDD the first boot device in BIOS.

---

### Post by NikoC on 2008-05-13
I was playing around with grub a couple of weeks ago and I messed up... the following thread got things working again:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=install+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=install+grub")
Maybe it will do the trick for you as well!

---

### Post by meierfra. on 2008-05-13
I wrote a howto for this situation:

[http://ubuntuforums.org/showthread.php?p=3995006#post3995006](http://ubuntuforums.org/showthread.php?p=3995006#post3995006)

There is a small problem with the howto: "ms-sys" is not in the 8.04 repositories. You can get "ms-sys" from

[http://packages.debian.org/etch/ms-sys]("http://packages.debian.org/etch/ms-sys")

or your can use the other methods indicated in the howto to restore the MBR of your internal drive.

---

### Post by black_knight on 2008-06-03
thanks meierfra that worked perfectly=D>

---

