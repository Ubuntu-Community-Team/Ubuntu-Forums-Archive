---
title: "No sound Ubuntu 22.04 on Asus Zenbook pro duo ux582hs"
date: 2023-08-10
forum: Hardware
---

### Post by neodiz on 2023-08-10
Buy a laptop. I need Linux to work. Installed Kubuntu 22.04. Everything works but there is no sound(mic work fine).If I plug in headphones I can hear something.

This is my second day trying to fix this problem. I came across these links:
 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1925057](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1925057)

[https://ubuntuforums.org/showthread.php?t=2476921](https://ubuntuforums.org/showthread.php?t=2476921)

[https://askubuntu.com/questions/1476088/no-sound-with-ubuntu-22-04-2-lts-on-asus-zenbook-ux582l](https://askubuntu.com/questions/1476088/no-sound-with-ubuntu-22-04-2-lts-on-asus-zenbook-ux582l)

But there are other models and its not work for me.Can anyone help me ?

---

### Post by readableauthor on 2023-08-10
How about you share your PC specs and logs with us:
```

sudo apt install hw-probe
sudo -E hw-probe -all -upload


```
Post the output link here.

---

