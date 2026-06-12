---
title: "Ubuntu 5.10 jre1.5.0_16 problems"
date: 2008-07-30
forum: General Help
---

### Post by The Jasom on 2008-07-30
I have followed all instructions to the word on the following help site: [https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-java.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-java.html) and i am stuck on step six, i am in the terminal and all it says after entering the command is "Bash: fakeroot: Command not found." Any help would be great. I used the jre 1_5_0_16-linux-i586.bin file, rather than the 04 file like shown in the help page.
If someone could help it would be greatly appreciated. Java allows me and my family to play many online games and the windows machine crashed, so much for family friendly huh? :D Anyways, any help means the world to me right now :)

---

### Post by spiderbatdad on 2008-07-30
perhaps fakeroot is not installed? It is in synaptic package manager...though this release is way outside the length of it's support. I don't even know if the repos are still available for download.

I would recommend downloading and burning a copy of 7.10 or 8.04.

Then:```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by The Jasom on 2008-07-30
Thank you much, downloading 8.04 now.

---

### Post by spiderbatdad on 2008-07-30
Hope you have enough ram on this machine...512 at least? Otherwise you will want to look into Xubuntu. The thought just occurred, as you could be running an older machine, since your ubuntu release was almost 4 years old.

---

