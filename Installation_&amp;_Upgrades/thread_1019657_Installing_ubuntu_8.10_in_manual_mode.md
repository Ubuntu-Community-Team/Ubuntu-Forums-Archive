---
title: "Installing ubuntu 8.10 in manual mode"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by pikiley on 2008-12-23
Hi 

I tried to install ubuntu 8.10 but had some problems. Any help will be appeciated.
I have a 82gb HD running win98se. My hd has three partitions, one primary partition (c drive) where win 98 is installed, and two other extended logical partition (d and e drives). All three partitions are Fat32.
When I tried to install ubuntu in one of the ext logical partitions (e drive) using guided mode I got a message...."file system is reporting the free space as 0 clusters, not 1895184 clusters" and recommended me to use manual mode for installation. When in  manual mode installation, it didn't allow me to create more than two partitions. /, /home or /, linux-swap, but  not the three partitions I want (which are /, /home and linux swap). Thanks for your help.

---

### Post by theteju on 2008-12-23
Hi , I am not sure but try to make all logical partition instead of primary.
Since you already have C, D and E ; you probably choosing primary for swap and root which will not allow you to have /home because as far as I know, YOu can only have maximum 4 primary partition on a HD.

Try to make ,/ as primary and rest all /swap & /home logical.

Or you can make all logical.

Hopefully that will work.

Thanks for reading.

Take care.

---

### Post by pikiley on 2008-12-23
thanks theteju for your quick response.
I followed your advice and was able to create three logical partitions and proceeded with installation. However, when installing, I got an SQUASHFS error: unable to read cache block [2a1c3f2e:c94] and fail reading block list [2a1c3f2e:c94].
Now I don't know what to do. Any idea or suguestions?
thanks, again.

---

