---
title: "2nd Gen iPod shuffle does't work in Edgy"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by geokker on 2007-04-17
I've just downscaled my iPod Nano to a 2nd generation shuffle. I really only listen to one thing (podcast) between computer sessions, so don't need a screen or a large capacity. While I can happily plug it in to my Mac and Windows boxes, I have a problem with Eft.

I can format the device for Windows or Mac and it will be recognised and mounted in Ubuntu with no problem. I can even transfer music to it with Rhythmbox or Banshee. However, when I try to play the music, the player tells me that there's no music on the machine. iTunes indicates that there's 'something' on it, but cannot read it.

I've tried maximising the iPods data mode, but I have the same problem.

I suspect music files are being transferred to the unit in Ubuntu but they're corrupting the metadata files.

What can I do?

Has anyone managed to get a 2nd gen shuffle to work with 6.10?

---

### Post by volksolwagen57 on 2007-04-17
i think i read on a forum somewhere else that the shuffle (any generation) is formatted with ntsf instead of fat32. ntsf is the new (faster) file sysem protocol that windows uses. ntsf does not work with linux. maybe you don't have all the multimedia codecs installed. is your music an ogg file or an mp3? off files will not work on other machines. i don't know if there's a way, but have you tried to format your shuffle to fat32 (the older file system protocol)?
hope this helps.

---

### Post by geokker on 2007-04-18
I've formatted it as HFS+ and FAT32, both don't work. It mounts, I can read the mp3s, songs even seem to transfer fine. When I eject and play however, the device reports no songs. In the case of the nano, I get a message on the screen to the effect 'Use iTunes to restore this iPod'.

---

### Post by njee on 2007-04-18
I have a similar problem with a first gen shuffle. The strange thing is that it will write to a video ipod and show up just fine. It's not really a fix but I found I could add the files in rhythmbox, which was easier for playlist etc and then open up the ipod in gtkpod and synchronise, this way I was able to get the shuffle to play the tracks.

Or maybe you could just use gtkpod. Either way, maybe this has been fixed in Feisty? Here's hoping.

---

### Post by olterman on 2007-04-27
Try the rebuild_db script it works marvels both with Edgy and Feisty 

Howto here 
[http://warcry.olterman.se/new/2007/04/26/ipod-shuffle-trouble-in-feisty-and-an-easy-fix/](http://warcry.olterman.se/new/2007/04/26/ipod-shuffle-trouble-in-feisty-and-an-easy-fix/)

---

### Post by geokker on 2007-04-27
Boom! Problem solved! Thanks muchly.

---

