---
title: "USB U2F security sticks - how to make them?"
date: 2018-01-08
forum: Hardware
---

### Post by marpolda on 2018-01-08
Hi. I've read about security U2F USB sticks and I'm wondering, how could I make an existing one U2F compatible. I have couple of USB sticks and would like to make one of them the security key (with additional support for normal USB storage, if it's possible). What are the requirements for U2F USB sticks? How much free space does it need for the key to be stored and does it support normal USB storage, like regular USB stick? How could I make my existing regular USB stick become the security key?

I'm a lazy person and don't want to buy an additional USB stick just for authentication. I'd like to make one myself, from an existing one. Is it even possible? How could I achieve that through standard Ubuntu Terminal?

Thank you :)

---

### Post by TheFu on 2018-01-08
U2F isn't a storage device, it is a USB device.  The specifications are online. [https://fidoalliance.org/specs/fido-u2f-v1.0-rd-20140209/fido-u2f-overview-v1.0-rd-20140209.pdf](https://fidoalliance.org/specs/fido-u2f-v1.0-rd-20140209/fido-u2f-overview-v1.0-rd-20140209.pdf)
There are slide decks out there too. [https://www.slideshare.net/FIDOAlliance/fido-u2f-specifications-overview-tutorial](https://www.slideshare.net/FIDOAlliance/fido-u2f-specifications-overview-tutorial)

I've purchased U2F devices for $10, so it isn't exactly expensive. They were subsidized by a company for a few months. That deal is over.  I saw a U2F long-term plan where we'd buy them at 7-11 whenever needed for $3.  That hasn't happened, yet.  

Remember that not all USB devices that happen to look similar are the same.

---

### Post by marpolda on 2018-01-10
Okay, I'll look into store later. Like I said, I'm a lazy person and basically tried to ask for a way to make one home from existing USB stick, like both auth and storage device. Since this is not possible, I'll just buy one myself while I'll get to it :) Thank you anyway :)

---

### Post by TheFu on 2018-01-10
There isn't a way to make a U2F device from a storage device (that I know), but there are ways to have it as an authentication device.  I didn't read the question as that broad.  Search "use usb storage for authentication linux" for some ideas.

There seems to be a way to build your own u2f device: [https://github.com/conorpp/u2f-zero/wiki/Building-a-U2F-Token](https://github.com/conorpp/u2f-zero/wiki/Building-a-U2F-Token)  The link claims you can build your own with about $3 in parts, some soldering, etc ...
Perhaps that is an option?

---

