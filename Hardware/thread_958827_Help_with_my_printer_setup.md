---
title: "Help with my printer setup"
date: 2008-10-25
forum: Hardware
---

### Post by sspletttstoeszer on 2008-10-25
Hi,

I'm new to Linux. I"m have problems getting my printer setup.
I have a Toshiba X205 laptop, a Dlink wireless router and a Hp Photsmart C6280 all in one printer that is network ready. It is hooked up to the router and my laptop is wireless which works. When I use windows it works but now I"m lost on how to make it work with Linux Ubuntu 64 bit. I have looked all over but no luck yet can anyone Help me.

Thank you, 
Newbee Scott

---

### Post by pytheas22 on 2008-10-25
First of all, did you try setting up your printer by going to System>Administration>Printing?  Ubuntu should be able to auto-detect it there.

If not, take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=638170&highlight=HP+Photosmart+C6280") and see if you can figure it out--people there say that they needed to install the latest version of hplip (the HP Linux printer drivers) in order to get their C6280 working, because the driver that ships with Ubuntu 7.10 was too old.  I'd assume that the driver in 8.04 would work out-of-the-box, but maybe not, so if you're sure that Ubuntu is unable to see your printer anywhere, try installing the most recent hplip as per the instructions in that thread.

If that doesn't help, let me know.

---

