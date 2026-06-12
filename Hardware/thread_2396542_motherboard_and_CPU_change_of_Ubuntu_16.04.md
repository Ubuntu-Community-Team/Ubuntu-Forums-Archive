---
title: "motherboard and CPU change of Ubuntu 16.04"
date: 2018-07-17
forum: Hardware
---

### Post by ozkan on 2018-07-17
Hi All,

Recently I changed my ubuntu's motherboard and CPU but now ubuntu does not boot-up. Just after grub, it continues to normal boot and after a couple of seconds, it finalizes by terminal screen asking to check journalctl -xb. when I check I see below screenshot, do you see a problem , do you have any suggestions ? 
[IMG]https://ubuntuforums.org/asset.php?fid=275070&uid=79618&d=1531847745[/IMG]

my new motherbard is 2009 model Asus  Rampage 2 Extreme , CPU is core i7 920  

best regards,

---

### Post by TheFu on 2018-07-17
I can't read the image.
Redirect the log/dmesg to a file and post a link to that here after posting it to the ubuntu pastebin.

Can you boot from a flash-boot system? If that works, it is much more likely to be solvable.  If not, there could be some bad hardware.

---

### Post by ozkan on 2018-07-18
thanks TheFu, yes I can boot from CD.  can you please tell me the exact file to get into the USB ?

---

### Post by TheFu on 2018-07-18
> **ozkan said:**
> thanks TheFu, yes I can boot from CD.  can you please tell me the exact file to get into the USB ?

[https://www.digitalocean.com/community/tutorials/an-introduction-to-linux-i-o-redirection](https://www.digitalocean.com/community/tutorials/an-introduction-to-linux-i-o-redirection)

dmesg -T > /tmp/out.dmesg
journalctl -xe > /tmp/out.boot

and any log file errors. Just the interesting parts. Don't need to see everything.

---

