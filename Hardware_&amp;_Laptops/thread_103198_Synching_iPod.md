---
title: "Synching iPod"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by Jordan Meeter on 2005-12-13
I recently had to reformat my laptop, so all my data was lost. I'm really nervous here, because the 7+GB of music I had on my laptop now only resides on my iPod. What program can I use, and how do I synch my iPod with Ubuntu so all of the music will be put *back* on my computer?

Thanks!

---

### Post by mulino on 2005-12-13
[QUOTE=Jordan Meeter]I recently had to reformat my laptop, so all my data was lost. I'm really nervous here, because the 7+GB of music I had on my laptop now only resides on my iPod. What program can I use, and how do I synch my iPod with Ubuntu so all of the music will be put *back* on my computer?

Thanks![/QUOTE]

Hi,

I use GTKpod for synching. You have to define the import mount point. That's all. Normally iPods get mounted under /media/<ipodname_in_capital_letters>. OK? Hope it helps! 

Regards, mulino

---

### Post by Jordan Meeter on 2005-12-13
But if there is no music on my computer, is it going to erase everything on my iPod?

---

### Post by stuporglue on 2005-12-13
Plug it in, then use the command line to navigate to /path/to/ipod/iPod_Control/Music/

Edit: You may be able to do this with Nautilus if you choose "Show hidden files".

In iPod_Control/Music there are a bunch of F?? folders. F00-F49 in my case. Just copy all of these folders to your HD and you've got a backup!

True, the titles will all be like OAOZ.m4a and UCET.mp3, but the id3 info is still inside, so if you use a 1/2 decent mp3 player, it'll list things by the data, not the filename.

---

