---
title: "USB Multi card reader not working in Ubuntu 13.10"
date: 2013-10-26
forum: Hardware
---

### Post by geemac2 on 2013-10-26
Hello,

I'm having an issue with my computer's multi-card reader that runs via an internal usb connection.  The reader used to work fine on earlier versions of Ubuntu.  I mainly use this to read my CF cards and my SD cards.  I have spent over two hours digging through older posts to get an idea, but nothing for issues with 13.10.  I think there may have been one issue about a 5 minute mount wait time, but it really did not releate to 13.10.
I have tried dmesg, lsusb and sudo blkid and the reader does not show anymore.
Usually I can find a fix for an issue via Google, but apparently 13.10 is too new.
I'm not sure if what Mfg. this is, but I am guessing that it may be a Realtek chipset.
The card reader is built into the computer and it would be a pain to have to pull it to find out for sure what the chipset is.

Any help would be appreciated getting this running again.

Thanks 
TC

---

### Post by warp99 on 2013-10-26
If you boot to a live DVD or USB does the card reader work?

---

### Post by geemac2 on 2013-10-27
Thanks for the reply Warp99,

That is something I should have tried from the get go.  How stupid of me.
I tried your suggestion and it still did not work.  It was working until I did the fresh install of 13.10.  Go figure that after I opened the case, pulled the wire to the USB header on the board, started the computer up and let things settle a bit, plugged the connecter back onto the header, wonder of all wonders it started to read the cards again.
You would never think of reseating a connection on a header when something stops working.  It just happened to go South right at the time I am installing 13.10.
And I do support for a gaming software; and I tell the users if it worked before and it just stopped, don't jump to the conclusion that its the software, check everything first.
How embarrassing...:oops: 
Now off to two other items that stopped working after Win7.  My USB ATI RF remote and my Avermedia TV tuner card.  And they have been reseated to the point of almost wearing out the PCI slot and the USB port.  Never could get these to work on any distro, and they show up in dmesg.  Oh what fun...

Thanks again Warp
TC

---

### Post by geemac2 on 2014-09-26
Solved

New install of Trusty 14.04 64bit solved usb reader.

---

