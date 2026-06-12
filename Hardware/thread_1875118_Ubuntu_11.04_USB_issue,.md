---
title: "Ubuntu 11.04 USB issue,"
date: 2011-11-04
forum: Hardware
---

### Post by chrisbarnes1992 on 2011-11-04
Hi all,

Recently I have worked on a Acer Aspire 3050 laptop and installed Ubuntu 11.10 and it works very well but with one down side. The USB ports will not Pick up USB devices etc. The 3 mobile Internet dongle doesn't seem to work but I think there is more needed to fix that. 

At the moment my dad has got it and he is working away from home for the next few weeks. I have tired to all of my Ubuntu knowledge (Lol) and to see what I could do with Google here at home. 

He has tried all of the USB ports and no prevail, even re booting it with the Pen drive in and it still wont pick it up. 

I have asked him to go to the terminal and put in lusb and it comes up the the USB Foundation 2.0 etc. but no sign of the pen drive.

Getting confused now :(

Does anyone else have any word of wisdom / Tips and tricks that I could try and see if we can get the USB working.

I have used Ubuntu for about 4 - 5 years now and this is a completely new problem for me.

---

### Post by chrisbarnes1992 on 2011-11-05
Not long after posting this post i  had discovered System Testing and had looked at he USB part of it.

I had told Dad this and he has done it a little later. He followed it and when it asked him to plug in a USB device he did such thing and it passed. Same applied to removing the USB device. 

However it failed on putting data on the pen drive.

Little confused still but googling away.

---

### Post by CppD on 2011-11-05
I had a similar problem with an SD card.  Turns out it wasn't formatted right/was completely unformatted.  It would show up in the reader, but it wouldn't write to it.  Try using gparted (sudo apt-get install gparted) to reformat your drive.

---

### Post by chrisbarnes1992 on 2011-11-06
I had passed on the message to him and explained how to format the pen drive. As the laptop was not connected to the Internet he formatted in Windows. 

He is saying it has not made any difference to using his pen drive in Ubuntu. 
When he did the system testing again it still can pick up the pen drive when he plugs it in.

I did ask him to see if there is anything in /media as that is where Ubuntu seems to be mounting devices etc. and is coming up with nothing pen drive related.

---

