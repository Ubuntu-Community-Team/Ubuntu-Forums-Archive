---
title: "Problem with Grub and Bootmngr after dualbooting Ubuntu and Windows 7"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by Maupertus on 2009-07-06
Hey everyone,

As my university refuses to adopt a decent wireless network security that can be handled in a easy way by linux, I thought I would try to dual-boot windows 7 on my netbook.

Installation went smoothly. But I can't seem to get to boot into windows anymore.
I've modified GRUB by looking in gparted. There are 2 windows partitions one on sda3 and another on sda4. I've tried both partitions in GRUB (hd0,3) (hd0,4).

sda4 gives me a message on 'Invalid Device'
Whilst sda3 gives me a bootmgr message.

What's the best way to move forward?

---

### Post by Herman on 2009-07-06
> I've modified GRUB by looking in gparted. There are 2 windows partitions one on sda3 and another on sda4. I've tried both partitions in GRUB (hd0,3) (hd0,4).
Try (hd0,2) if you're using GRUB Legacy, as most people would be at this time.
Here's a link to a table for converting between Linux and GRUB (legacy) notation, [A Quick Guide to GRUB's Numbering System]("http://members.iinet.net.au/%7Eherman546/p15.html#A_Quick_Guide_to_Grubs_Numbering_System").

Regards, Herman :)

---

### Post by gemini6 on 2009-07-06
Did you resize your windows partition during installation? If so this link may help [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by Maupertus on 2009-07-08
> **Herman said:**
> Try (hd0,2) if you're using GRUB Legacy, as most people would be at this time.
Here's a link to a table for converting between Linux and GRUB (legacy) notation, [A Quick Guide to GRUB's Numbering System]("http://members.iinet.net.au/%7Eherman546/p15.html#A_Quick_Guide_to_Grubs_Numbering_System").

Regards, Herman :)

Worked like a charm! Thank you Herman. ):P

---

### Post by Herman on 2009-07-09
:) Cool!
... and what kind of wireless networking are you using? 
I'm not an expert on networking, but you never know, maybe I or else someone around here can help you with that too? :)

---

### Post by Maupertus on 2009-07-09
Nah, for some reason they use a terribly inefficient way to secure the network.
You can find the manual [here](http://www.rug.nl/cit/servicedesk/hulp/draadloos/handleidingubuntulinux_en.pdf) but it just won't work at all.

---

