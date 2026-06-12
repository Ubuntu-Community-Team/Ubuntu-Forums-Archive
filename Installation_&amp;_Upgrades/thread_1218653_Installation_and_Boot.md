---
title: "Installation and Boot"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by flareback on 2009-07-20
When I installed Ubuntu 9.04 I kept getting these weird errors. It eventually got passed them and did install though. When I rebooted the same errors showed up before booting into Ubuntu. It does run correctly but it takes a long time to get through the boot process. I have windows 7 installed alongside which installed and boots normally. below are some images of the errors as it was installing. I noticed it mentions sdb, could my second hard drive have an error?

This is being installed on a computer with the following specs:
Intel core i7 920
Gigabyte EX58 UD4P
Sapphire Radeon HD 4850
2 x 400 GB Seagate Sata drives

[[IMG]http://i973.photobucket.com/albums/ae220/flareback/th_01UbuntuError_sdb.jpg[/IMG]]("http://s973.photobucket.com/albums/ae220/flareback/?action=view&current=01UbuntuError_sdb.jpg")

[IMG]http://s973.photobucket.com/albums/ae220/flareback/?action=view&current=04UbuntuError.jpg[/IMG]
[[IMG]http://i973.photobucket.com/albums/ae220/flareback/th_04UbuntuError.jpg[/IMG]]("http://s973.photobucket.com/albums/ae220/flareback/?action=view&current=04UbuntuError.jpg")
[IMG]http://s973.photobucket.com/albums/ae220/flareback/?action=view&current=04UbuntuError.jpg[/IMG]

---

### Post by quixote on 2009-07-22
> could my second hard drive have an error?

That's what the error messages are saying.  Is there a way for you to unplug /dev/sdb?  Then try booting up and see whether that changes anything.

---

