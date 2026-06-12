---
title: "Connection Problems on Compaq Presario v2000"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by lucky sevin on 2007-03-10
So I got my new Compaq Presario v2000 with AMD Turion64 cpu.  I replaced the hard drive and put the one with Windows preinstall aside, which I haven't checked out yet.  I installed Edgy, and right away on the live boot, I noticed that I had no internet connection from my cable modem plugged into the ethernet port.  To my suprise, it installed anyways.  But still no connection.  I took it to my friend's house, who has ATT/Yahoo and got it to work.  Then I realized the wireless card, which was listed in Network maager, couldn't be enabled.  Long story short, I followed the steps on [this]("http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper") post.  I even downloaded a new kernal like it suggested in the troubleshooting part.  

After that, the wireless card wasn't even listed in Network Manager.  So I'm stuck there.  Plus, while trying to install a copy of Breezy that I had (on my cable internet), it said it couldn't detect the DHCP.  When trying to boot Knoppix, it says "Can't find KNOPPIX filesystem, sorry.  Dropping you to a (very limited) shell."  I'm starting to wonder if I'm going to have to return this.  Can anyone help?

---

### Post by lucky sevin on 2007-03-10
UPDATE:  I've reinstalled 6.10 to start over.  And another not:  before the reinstall, I put a gdesklet on my desktop to manage network connections and it showed activity when the cable modem was plugged in, but I still could not use the internet on Firefox.

---

### Post by Nabil on 2007-03-10
I'm Having the Same problem i get no internet and no connection but i need to find a drive for my network card. Broadcom something 802.11 g/b and that's my biggest problem everything works great apert form that . the sound works fine and so do the mute/sound up/down button but i need internet access.

---

### Post by aximmaxim on 2007-10-23
I had the same problem -- you need to use cheat code NODMA
i.e.
at the BOOT prompt, type:

knoppix nodma


Good luck!  It's been running beautifully on my (Sadly) hard-driveless presario for 3 days!

---

