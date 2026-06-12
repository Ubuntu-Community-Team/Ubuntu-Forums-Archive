---
title: "X Server doesn't start on boot"
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by ffloimair on 2006-10-14
Hi!

I'm using the Ubuntu Edgy Beta with all updates installed. After initial installation everything was fine, but after I updated everything and the following reboot my X Server won't start.

The odd thing however is, that it does start fine, when I start it manually after switching to a tty and running startx.

Also I get an error message "Failed to initialize HAL" since then.

Everything else works fine, except for this problem.

I've searched for hours now and didn't find anything helpful so far.

Any suggestions? Maybe a bad update like the nvidia-driver stuff with Dapper a few days ago?

Thx for your help in advance!


Regards

---

### Post by taurus on 2006-10-15
Have you tried to reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ffloimair on 2006-10-15
yes i did. unfortunately that didn't solve the problem

---

### Post by taurus on 2006-10-15
Are you using nv or nvidia (Driver) in your /etc/X11/xorg.conf?

---

### Post by ffloimair on 2006-10-17
No,

I have integrated Graphics (intel i915GM)

---

### Post by ffloimair on 2006-10-21
Solved: the start-scripts for gdm were missing in rc#.d directories.

Nevertheless the HAL problems still remain

---

