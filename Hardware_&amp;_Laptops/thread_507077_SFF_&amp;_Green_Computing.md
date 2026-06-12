---
title: "SFF &amp; Green Computing"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by lazyron on 2007-07-22
I'm going to put together a new home media server and would like to use a small form factor that is energy efficient. I've been looking at Shuttle and Mini-ITX as possible solutions, but I'm having trouble determining their hardware compatibility with Linux (Ubuntu in particular).

I'm sure if I dug deeper I could find energy consumption facts on these platforms, but because I'm having a hard time in general trying to figure out if they work with Linux in the first place I thought I'd post here to see if anyone has implemented a energy efficient SFF Ubuntu box.

Thanks in advance.

-lazyron

---

### Post by lazyron on 2007-07-23
/bump for the new week

---

### Post by lazyron on 2007-07-28
/bump

one more time

---

### Post by Mike'sHardLinux on 2007-07-28
Hi!

There's more than one approach to this problem. For starters, have you searched for specific model numbers?If you have some specific models in mind that you are interested in could you post which they are, and maybe even post links to them on the hardware vendors site?

Generally, with motherboards, you look for (or avoid) certain chipsets. Once you know that certain chipsets are working with Ubuntu, you will be ok with most if not all boards that use them. For example, I have built a couple of systems with the Intel P965 chipset and they have all worked fine out of the box. If you go with an older chipset that is known to work, you'll probably be equally safe.

The only trouble you might run into with such a board is with specific features. For example, many have used the Jmicron controller to have an IDE controller and keep cost down (as it seems to me.) I have seen many posts with people having problems with this controller. I personally have not had the problems that are being reported. I suppose it depends on the bios version on the board.

I build systems fairly often and always put Linux on them at least for testing, and have rarely run into problems where things didn't work. If you stick with a recent version of Ubuntu, and don't buy cutting edge hardware, the odds are in your favor that most things will work out of the box, and you might have to put some work into getting something to work right,

I can't help much with the green computing aspect. Just about all hardware these days has power saving modes. I guess it depends on how green you want it to be.

---

### Post by lazyron on 2007-07-29
Well I'd prefer mini-itx. Pretty much anything the following link that supports SATA and IDE.

[http://www.mini-itx.com/store/?c=2](http://www.mini-itx.com/store/?c=2)

AOpen makes some decent stuff.

[http://minipc.aopen.com/Global/spec.htm](http://minipc.aopen.com/Global/spec.htm)

As does system76.

[http://system76.com/product_info.php?cPath=27&products_id=53](http://system76.com/product_info.php?cPath=27&products_id=53)

Asus has some nice booksize boxes.

[http://usa.asus.com/products.aspx?l1=1](http://usa.asus.com/products.aspx?l1=1)

Looking at the Shuttle boxes again reminds me that they are a little out of my price range.

I'm also trying to keep the cost to around $500, I'm going to be reusing a SATA drive and my DVD/RW drive.

I don't have any specific model numbers in mind, just hopefully something small, and energy efficient that works with Linux.

---

