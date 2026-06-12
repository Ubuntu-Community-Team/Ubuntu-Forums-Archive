---
title: "[SOLVED] Live CD cant boot"
date: 2008-07-28
forum: General Help
---

### Post by baju on 2008-07-28
Hi
I want to install ubuntu on my Samsung Q70 and I have the following problem:

I use the live CD and it starts as expected, but it cannot boot any kernel. When I try to boot with the default parameters I only get this message:
```
Could not find kernel image: /cdrom/preseed/ubuntu.seed
```

---

### Post by Het Irv on 2008-07-28
Have you checked the CD for errors? You may have a bad burn.

---

### Post by dexter.deepak on 2008-07-28
yes, you can check for errors ; if you are lazy to reboot...you can check the md5 checksum too....or either try running the cd on a vm, like virtualbox.

---

### Post by baju on 2008-07-28
Ok, there is the next problem: the "Check CD"-option in the menu does not work.

I am now downloading the alternate installer. I'll write a report when ready.

---

### Post by baju on 2008-07-29
ok the new cd worked perfectly. Now with ubuntu i was able to check the cd and the "/caspar/init.rd" had some errors. Seems like my cd burned hitted the live cd at it's Achilles heel.
Thanks for help, please close thread.

---

### Post by Het Irv on 2008-07-29
No need to close the thread, someone else may have a question, but if you (baju) could mark the thread as solved (under thread tools) that will help other users.

---

