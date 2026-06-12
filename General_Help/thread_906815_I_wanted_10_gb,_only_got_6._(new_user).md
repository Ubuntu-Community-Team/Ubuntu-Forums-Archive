---
title: "I wanted 10 gb, only got 6. (new user)"
date: 2008-08-31
forum: General Help
---

### Post by turtleraj on 2008-08-31
Hi,

I am a new Linux user and I am also new on the ubuntu forums (it's not a coincidence). I have a few questions but I will ask only one right now.

I've always wanted to try out Linux, and I heard Wubi was the easiest, most painless way to go about doing this. So last week, I downloaded Wubi and ran it. I selected 10 gb, and started the download process. The download and installation worked great, or so I thought. Once I started up ubuntu, I checked the amount of free space I had, and it was 3 gb. I knew this couldn't be right so I checked online and someone said that this could be a problem in the virtual partition. Their advice was to uninstall and reinstall. So I did that. Now after the second installation, I have 5.9 gb free. Is this normal?

Any help would be greatly appreciated.

I forgot to mention that before I installed ubuntu, my hardrive had 22 gb free.

---

### Post by snl2587 on 2008-09-01
This is normal. Wubi automatically allocates space for a swap partition, so that the swap + linux partitions take up the space you specify. I'm not sure how to resize this or tell Wubi not to allocate as much space, but that may be in the documentation.

---

### Post by Orlsend on 2008-09-01
In the Installer you can tell how much space you wan it to take, In you case will range from 4-20 GB

Yeahtheres no way you can go wrong with wubi

---

### Post by turtleraj on 2008-09-01
ok thanks.

---

