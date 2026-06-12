---
title: "How to Remove NVIDIA Proprietary Display Driver."
date: 2016-06-26
forum: Hardware
---

### Post by poorguy on 2016-06-26
Greetings,

Had a Nvidia graphics card die and replaced it with a Ati Radeon graphics card and all is working good.

My question is how do I totally remove NVIDIA proprietary display driver and anything Nvidia related to the Nvidia graphics card.

Ubuntu Mate 16.04 is distro installed.

Thanks.

---

### Post by Linuxisfast on 2016-06-26
In terminal sudo apt --purge remove nvidia*

---

### Post by poorguy on 2016-06-26
Hey Linuxisfast,

Thanks that command appears to removed everything Nvidia related.

After running sudo apt autoremove I ran the command you posted again and nothing shows up.

Thanks for the help.

---

### Post by poorguy on 2016-06-26
What about the  nouveau open source driver does that need to be removed or would that have been removed when I originally installed the Nvidia proprietary driver.

---

### Post by Linuxisfast on 2016-06-26
The nouveau is kernel level so can't be removed but blacklisted. [COLOR=#111111][FONT=Consolas]sudo apt-get install nouveau-firmware [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]sudo dpkg-reconfigure xserver-xorg next time use additional driver method to use it via GUI, far easier and safer.[/FONT][/COLOR]

---

### Post by poorguy on 2016-06-27
Hey Linuxisfast,

Thanks.

---

### Post by Linuxisfast on 2016-06-27
> **poorguy said:**
> Hey Linuxisfast,

Thanks.

You are welcome.

---

