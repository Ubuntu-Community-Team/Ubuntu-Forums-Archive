---
title: "Vaio TZ quest revisited"
date: 2009-02-09
forum: Hardware
---

### Post by deletarus on 2009-02-09
I noticed the Vaio TZ quest for 100% compatibility thread has been dead for quite some time. I personally am still very interested in this and wanted to revive the topic.

So far in 8.10 I have working on my TZ;
Pretty much everything except;
Camera (which is recognized in Ekiga but nothing else, and doesn't work properly) I had to upload some custom firmware to get it that far.
Media card readers.
Finger print reader.
A couple of the media buttons on the front.

I think everything else works fine. If anyone can offer support for webcam or would like to share how they got things to work on their TZ or similar, please post. Let's complete the quest.

---

### Post by scicode on 2009-04-06
since I cannot post to the old tz quest I will post it here

I only had a very small shell window if I used the ctrl+alt+F1 shell (sorry don't know the correct term for that), I improved it by adding  ```
vga=0x318
``` in the /boot/grub/menu.list this changes the screenresolution on bootup to something more fitting (still not the 1366*768)

here is the whole line
```
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ca8b7d70-46a4-4577-a78b-7f7a97d6820d ro quiet splash vga=0x318 
```

---

