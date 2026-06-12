---
title: "Gutsy Suspend - No restricted modules"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by balak on 2008-01-20
Hi All,

After searching the forums for almost a month, I am ready to give up. Finally thought that I should ask folks in a separate thread. So here goes my situation.

I have an averatec 2150 laptop - amd turion processor, ATI Radeon 200M graphics etc., Ralink RT61 network card.

In feisty, I was able to suspend/hibernate even with the restricted drivers. I had amd64 version installed and had a lot of trouble with the network card, along with an annoying screen flicker.

After upgrading to Gutsy, I am not able to suspend or hibernate. Even in i686 version (32 bits)  - without any restricted drivers. The kernel is using the default 'ati' graphics driver.

The only thing different than stock Gutsy is ndiswapper - I need it to use windoze driver for rt61.

Any ideas on how to debug this issue will be very much appreciated.

I also tried s2disk - It works sometimes but most often it doesn't.

---

### Post by balak on 2008-01-29
anybody? 

I also compiled my own kernel with slab. It still cannot suspend/hibernate..

does this have anything to do with the fact that i use i686 version with an amd64 m/c?

---

### Post by kegobeer on 2008-01-29
Have you tried a clean install of Gutsy instead of an upgrade?

---

### Post by balak on 2008-01-29
I have a clean install. Its not an upgrade from feisty.

I guess my first post was confusing.. I just installed gutsy in another partition.

---

