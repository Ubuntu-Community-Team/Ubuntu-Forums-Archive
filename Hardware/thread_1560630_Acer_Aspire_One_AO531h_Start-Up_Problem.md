---
title: "Acer Aspire One AO531h Start-Up Problem"
date: 2010-08-25
forum: Hardware
---

### Post by last_wish1649 on 2010-08-25
Hi everyone,

I've been using Ubuntu on my main PC for the last two years now, and I've just invested in an Acer Aspire One netbook.
I booted Ubuntu Netbook remix on my memory stick and tested it out on my netbook.
Everything that I needed working was fine (I don't need wireless).
The installation was neat and quick, but once I restarted and tried the start-up, the netbook hanged; the only thing that was moving on the screen was a dash blinking on and off in the top left hand corner.
I understand it could be a HDD fault, but I'm not sure what else to try.
BTW, Windows 7 was originally on my netbook, and I reinstalled UNE instead.

Any help would be great, Thanks! :)

---

### Post by clrg on 2010-08-25
Could you boot with the USB stick again, mount the partition containing /var/log and check out /var/log/messages? It might contain some clues to what went wrong during the boot process.

Also, edit /etc/default/grub and remove the "quiet" and "splash" options. Then run 
```
sudo update-grub
```
and restart. That should print some messages during startup.

---

