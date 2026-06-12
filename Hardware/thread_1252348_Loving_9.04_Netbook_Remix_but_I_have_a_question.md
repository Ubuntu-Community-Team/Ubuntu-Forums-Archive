---
title: "Loving 9.04 Netbook Remix but I have a question"
date: 2009-08-28
forum: Hardware
---

### Post by gus6464 on 2009-08-28
I recently got an Acer Timeline 3810TZ and I am loving using 9.04 NBR on it even though it's not a netbook but I really like the interface for the stuff I do with my laptop which is just email, openoffice, and web surfing.

My question is that my Timeline has an empty mini PCI-e slot and I have been wanting to install an SSD into the slot just for NBR. Reason for this is because I want to put NBR by itself and Windows 7 by itself on the 320gb HDD. Now I know I can do this but I was wondering if there was a way to have a menu selection upon bootup that let me pick what OS I wanted to load without having to pick a specific boot drive with F12. I was wanting to do this by using EasyBCD if it is at all possible.

---

### Post by gus6464 on 2009-08-29
Does anyone have any ideas or thoughts?

---

### Post by ad_267 on 2009-08-29
Well Ubuntu uses a boot loader called GRUB which can boot into Windows, Ubuntu or any other OS usually, so it should be able to work in this situation too. You could install Windows 7 first, then install Ubuntu onto the SSD which will install GRUB onto the master boot record. I don't have any experience dual booting with one OS on an SSD card though so it could be a bit different to dual booting with two hard drives.

Edit: I had a look at the Wikipedia entry for EasyBCD and it looks like that should work too.

---

