---
title: "Error when the Ubuntu is starting!"
date: 2007-03-31
forum: Hardware &amp; Laptops
---

### Post by lounigccman on 2007-03-31
Hello,

I have just bought a ASUS A9250 graphic card and it is ATI Radeon 9250.
While the Ubuntu 7.04 beta was starting,the monitor showed some codes like:
[123.3124235] 42365234568935633246 (I can't remember it)
And it showed again and again.But once I changed the graphic card,the OS could work
properly again!

Please help me to solve this problem as I really want to use Ubuntu!!!

---

### Post by taurus on 2007-03-31
Boot into recovery mode from GRUB menu and reconfigure your X again since you changed the video card.

```
dpkg-reconfigure xserver-xorg
```

---

### Post by lounigccman on 2007-04-01
I'm sorry,but the problem still cannot be solved....
Is Ubuntu support ATI RADEON 9250??I just wonder that....

---

### Post by Mmmbopdowedop on 2007-04-04
yes it does support it, mine works great with a few changes to xorg.conf

explanation :    [Click Here](http://ubuntuforums.org/showthread.php?t=398395&highlight=radeon+9250)

---

