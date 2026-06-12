---
title: "linuxrc in initrd.gz on LiveCD - where is it?"
date: 2005-11-16
forum: General Help
---

### Post by andrewsawyer on 2005-11-16
Hiya,

I hope someone can help me with a question I have.  I am trying to edit the initrd.gz file on the LiveCD to add some USB modules to the linuxrc file, however I can't find it.  Is it somewhere else?

I have uncompressed the initrd.gz file, and then mounted the file within it using:

```
sudo mount -o loop initrd /mnt
```

I have then cd'd to the /mnt directory and searched for the linuxrc file (which is on /usr/share/mkinitrd-cd directory on my main system).  Basically, I'm hoping someone can tell me where is is on the LiveCD?

Is it within the cloop file, or somewhere else?  I would appreciate if someone could let me know!

If you need more clarification, pls let me know.

Andy

---

### Post by andrewsawyer on 2005-11-16
I think I've made this sound harder than it needs to be.

I would like to add the USB modules to the kernel on the LiveCD, and I've been told I can do this by adding them into the linuxrc file.  However I can't find it on the CD.

Can someone please tell me how I can add more modules to the kernel so that it puts them into the boot-process?

Many thanks.

Andy

---

