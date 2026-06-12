---
title: "I'm stupid - 8.10 problem"
date: 2008-11-13
forum: General Help
---

### Post by Primula on 2008-11-13
I think I've managed to do the stupidest thing ever... upgraded to 8.10. Great stuff but my net would not work. I have no means of fixing it until bug updates come out. However how could I update without having internet? Is it possible? Now I've booted from the 8.04 live cd in order to post this... HELP me please? 
I though of just re-installing 8.04 but I'll loose a lot of data... 
Any suggestions?

---

### Post by snova on 2008-11-13
If you have another computer with a working connection (you must, since you're posting here), try looking into apt-zip.

---

### Post by Iowan on 2008-11-13
If you have the time to invest in rebooting, you might be able to post enough information to find the problem area.  For starters, were (are) you using static addresses or DHCP? wired or wireless? You could check **lshw** and/or **lspci** to see if your NIC is detected, and **ifconfig** to see if it gets an address (watch out for the 169.X.X.X avahi address - which usually means DHCP failed).

BTW, does the 8.10 LiveCD work?

@snova: I'll have to check apt-zip... I have a LAMP server that I cannot put on network at work, so it's "difficult" to add packages - like phpMyAdmin, or even elinks.

---

### Post by Primula on 2008-11-14
I don't have a 8.10 live cd. Just upgraded through the synaptic manager. It's all fine now. I put all my music and stuffs on a differnt partition and put 8.04 back on over 8.10... Thanks for everyting anyways. I guess I'll try 8.10 later on when some bugs are fixed.

---

