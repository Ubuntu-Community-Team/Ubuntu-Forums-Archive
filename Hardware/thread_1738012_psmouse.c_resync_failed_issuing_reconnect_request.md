---
title: "psmouse.c resync failed issuing reconnect request"
date: 2011-04-24
forum: Hardware
---

### Post by hiren_bhatt on 2011-04-24
This could be a known problem to some of you and a few might would have been able to fix it also. 

Three solution to this what I found from various forums are 
1. modprobe -r psmouse
   modprobe psmouse 

2. /etc/modprobe.d/options.conf;
options psmouse resetafter=10

3. GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic nolapic"

None of them work for me. Also the problem that I have it little different then other. When my mouse freezed for the first time I was able to see the "psmouse.c resync failed issuing reconnect request" message, however after trying the above option I dont see this message anymore but still my mouse pointer gets freeze. 

However 
1. The mouse only freezes for touch pad. I have a touch screen 
   and mouse works with stylus. 
2. The pointer only freezes after logging in for user hrien where   
   it freezed for first time. 
3. It only freezes for one user, hiren. I added another user and 
   logged in, the mouse did not freeze for this user. 

I am not getting a clue how to fix this, any help??

I have installed Ubuntu 64bit on HP Pavilion tx2000 yesterday.

---

### Post by keredson on 2011-05-04
similar issue here.  problem goes away as long as i have my ethernet connected however...

---

