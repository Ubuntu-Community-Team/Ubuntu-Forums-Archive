---
title: "Kubuntu Sonypi acting weird"
date: 2006-06-07
forum: Hardware &amp; Laptops
---

### Post by wh0rd on 2006-06-07
sonypi: On Ubuntu, it runs fine, but on Kubuntu I'm having issues. It won't load on boot. I have to manually set it in Laptops & Power - System Settings everytime.  When I log out and log back in it works, seems to take the settings, but when I reboot I guess it resets the settings. I have no idea why it's doing this.

---

### Post by SiDaFaLiCkNo on 2006-06-08
Your oing to have to reset the bios

---

### Post by r3st on 2006-06-08
[QUOTE=SiDaFaLiCkNo]Your oing to have to reset the bios[/QUOTE]

this actually worked for me once

---

### Post by wh0rd on 2006-06-08
But it worked completely fine without resetting the BIOS in Ubuntu Gnome.

---

### Post by wh0rd on 2006-06-09
Okay I did:

sudo chmod 666 /dev/sonypi

Logged out and logged back in. Everything works, but I have to keep doing that whole process everytime I reboot. Thats just weird!

---

