---
title: "Sharing XP printer with Breezy"
date: 2006-04-24
forum: Hardware &amp; Laptops
---

### Post by monomaniacpat on 2006-04-24
I have set the printer to share and enabled unix support on my windows machine. Having looked for the printer on the network neighbourhood from my Mum's powerbook, the PC is not visible. 

I have samba and swat installed (but can't seem to run either (I tried localhost:901, but firefox couldn't load it) - can anyone give me a guide as to how I should detect and install the network printer? I don't know what my PC's IP address nor how to find it out, although my router is 192.168.1.1.

Thanks in advance for any help you can give me.

mono.

---

### Post by monomaniacpat on 2006-04-24
I found [this](http://ubuntuforums.org/showthread.php?t=138325&highlight=printer+sharing) thread and followed the advice (this is not the first time I've tried a similar technique, but at least it told me my PC's IP address) but it doesn't reach the printer.

---

### Post by monomaniacpat on 2006-04-24
C'mon guys, this must be possible?!

---

### Post by CronoDekar on 2006-04-24
Since you can't get Samba to work either, I'm wondering if it might be a firewall problem on one or both of the computers.  If so, they should be set up to allow traffic from the local network.

The howto looks like how I got my XP printer shared, so I don't think it's a problem in that process.  Though, be sure that the printer name you put in Linux is the name given to its share name, not the printer name itself (for me the default was "Printer").

Sorry I can't be of any more help!

---

