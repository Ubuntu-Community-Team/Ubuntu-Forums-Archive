---
title: "ssh client"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by banditti on 2005-06-02
Having only yesterday moving to Ubuntu as my primary OS from XP, I am having trouble finding a SSH client like Putty.  I would like to be able to save profiles, etc, so I don't have to remember 14K ip addresses.

Thoughts?

---

### Post by djg on 2005-06-02
PuTTY and tools for PuTTY are available in the Universe repository under Networking.

apt-get install putty putty-tools

---

### Post by banditti on 2005-06-02
Thank you!

---

### Post by alastair on 2005-06-02
You could also put those 14K IP addresses in your /etc/hosts file and use plain "ssh" ;-)

---

### Post by Vorian on 2005-06-27
Helped solve my problem too, Thanks!!!

---

### Post by wherethebibawi on 2005-06-28
[QUOTE=djg]PuTTY and tools for PuTTY are available in the Universe repository under Networking.

apt-get install putty putty-tools[/QUOTE]
 Cool thanks that's XactLy wat i was L00king 4....

---

### Post by arosct on 2005-07-02
Hi. Since there is an ssh client installed (for use in your favorite terminal application), use that instead of installing extra sw. Why arent you making aliases in  your rc/profile file? I use this way for my smtptunnel:
alias smtptunnel='ssh [email]gugus@www.blabla.ch[/email] -L 35353:mail.gmx.net:25'

Then, when you whish to connect, simply type:
smtptunnel <CR> and: voila.

Regards.

---

