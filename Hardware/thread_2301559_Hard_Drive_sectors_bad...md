---
title: "Hard Drive sectors bad.."
date: 2015-11-03
forum: Hardware
---

### Post by righN on 2015-11-03
Hello, I know that my Hard Drive is bad but i don't know why, when i was using Windows skype started crashing because of I/O error and now same with ubuntu. I used computer with ubuntu apie 1-2 weeks or more and computer just started my showing errors with bad sectors. Everytime I launch computer I see ubuntu and dots every time are orange and i see lines like they trying show me something and then i restarting my computer. When computer restarts it's shows me GRUB loader and i selecting "Ubuntu" and his showing me that is my sectors is bad.

---

### Post by tgalati4 on 2015-11-03
Boot a Live Session using a USB stick.  Connect your computer with an ethernet cable.

Open a terminal:

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

Write down the errors.

Find a new hard disk.

---

