---
title: "[SOLVED] Hacker looking for open ports?"
date: 2008-07-16
forum: General Help
---

### Post by Squid Tamer on 2008-07-16
In the "events" tab of firestarter it's telling me that Samba (SMB) is sending something (requests? packets? events? I don't know what word to use) that is being blocked. 

I searched the net and found that this is a hacker looking for open ports.


Should I be worried? 
What should I do?

Additional info: 

The ports are 137 and 138.
The IP adresses are:

192.168.1.103
192.168.1.100
192.168.1.147
192.168.1.146
192.168.1.102
192.168.1.142

There may be more, but that's all I could see right away.

---

### Post by tuxxy on 2008-07-16
Calm down before you accuse a hacker, your port 137 is your UDP port and 138 is the netbios port for your SAMBA, both related to windows.

Also 192.168.1.xxx is usually the IP range of your router, if you were using samba at the time then no i wouldnt be worried.

---

### Post by Squid Tamer on 2008-07-16
I wasn't accusing a hacker entirely, that's just what I heard. Funny thing is, I'm not using samba. I made sure it wasn't installed before I posted. I also thought I recognized that IP from somewhere... but no one on my network have or use samba (I'm 99% sure)... Thanks for your reply though.

---

### Post by tuxxy on 2008-07-16
If you have a windows drive in the system it also would cause this.

---

### Post by Squid Tamer on 2008-07-16
oh...  I see now... It's a windows network thing... I thought it was some linux file sharing program and it was trying to break into my system to "share" some files. sorry. Silly me. I feel stupid now...

---

### Post by tuxxy on 2008-07-16
lol no, it simply reporting it to you as it thinks it should do.

Reconfigure your firestarter :)

good luck

---

