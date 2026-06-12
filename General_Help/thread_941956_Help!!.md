---
title: "Help!!"
date: 2008-10-08
forum: General Help
---

### Post by DanHorniblow on 2008-10-08
Hey could anyone help me. I have just installed ubuntu on my new vista hime premium laptop as a second OS.

I created a new partition for ubuntu and installed it in there so vista and ubuntu are seperate.

Ubuntu and Windows Vista both apear in the boot selecter upon power up.

But when I select ubuntu it frezzes turing launch.

Can someone help me.

---

### Post by ajmorris on 2008-10-08
> **DanHorniblow said:**
> Hey could anyone help me. I have just installed ubuntu on my new vista hime premium laptop as a second OS.
 
I created a new partition for ubuntu and installed it in there so vista and ubuntu are seperate.
 
Ubuntu and Windows Vista both apear in the boot selecter upon power up.
 
But when I select ubuntu it frezzes turing launch.
 
Can someone help me.
 
 
hi there,
when it shows the boot select menu, press 'e' on ubuntu and 'e' again on the kernel line, at the end of that line, put noapic, nolapic  then press 'esc' once, and press 'b' on the line you just edited. If ubuntu still freezes during launch, can you please open up a linux live cd (or other media that can read your ubuntu partition) mount your ubuntu partition and get the /var/log/syslog file, and paste the contents into a reply :)
 
AJ

---

