---
title: "Installing new firewire card"
date: 2006-03-11
forum: Hardware &amp; Laptops
---

### Post by keene on 2006-03-11
Hey all,

I'm trying to install a new firewire card on my machine -- I've gotten as far as plugging it in. If I do an lspci, it shows up in the list; but there's nothing in /dev, and I can't get any software to work with it.

I honestly have no idea what to try. Google and searching this forum haven't brought up anything helpful....

Help?

---

### Post by WildTangent on 2006-03-11
What are you trying to use it for?

-Wild

---

### Post by keene on 2006-03-12
I want to use it for my digital camcorder. It's a JVC GR-D250U; Mini DV.

When I use Kino, it says that the raw1394 module must be loaded, and I must have read/write access to /dev/raw1394

/dev/raw1394 didn't exist, so I did:

mknod -m 666 /dev/raw1394 c 171 0

but I can't figure out how to load the module.

---

### Post by Magellan on 2006-04-16
I had the same error.
In my case /dev/raw1394 existed.
Executing the following fixed things for me:
sudo chmod +666 /dev/raw1394

Good luck

---

### Post by altonbr on 2007-08-08
> **Magellan said:**
> sudo chmod 666 /dev/raw1394

Worked for me. Thanks.

---

### Post by Pawel on 2007-08-25
Hi!

Could you write a firewire controller card type ?

Best Regards

---

### Post by koosfoto.hu on 2007-09-03
Hi!

I have just plugged in my FireWire card.
A Sony mini DV camera is connected to it now. And I would like to read in videos and edit it under the Ubuntu.
My system does not say a word about the card. 

In Kino there is nothing under the IEEE 1394 tab. No device is listed there. 

What to do?
How can I make it recognized by the system and make it usable for video input?

I am new to Ubuntu, and my knowledge is rather shaky in it. Please, explaine it to me slowly, if possible.  I know how to start the Konsole... and not much more about it.

Thanks a lot!

Tamas

---

### Post by chillyair on 2008-07-03
HI I am also having trouble with my firewire card. I ran the same commands that the above people did but I cant get my card to show up in kinos IEEE 1394 list. Can anyone please help me. I've really been struggling with this and would appreciate it if anyone could point me in the right direction.

Thanks

---

