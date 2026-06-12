---
title: "Low performance of ATI Mobility Radeon 9000 on Dell D600"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by Mochtroid-X on 2007-09-06
I have a Dell D600 w/7.04 installed and an ATI Mobility Radeon 9000 (listed as a  **ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]** by lspci) and glxinfo | grep direct says I have direct rendering enabled but the performance is not acceptable. I know I cannot use the fglrx driver and I cannot find usable information on the forums. Is there any way I can tweak my xorg.conf to increase performance?

---

### Post by corporatecookie on 2008-04-20
Can you explain what you mean by poor performance ? Is the screen not rendering quickly enough ? Are you using Compiz?

---

### Post by Mochtroid-X on 2008-04-20
Wow, after so long I simply forgot about this thread  I made and accepted that my laptop is crippled.

By "low performance" I meant that anything 3D would usually result in a  black screen, but recently a user in a chatroom (who has the same card on his laptop) revealed that 3D works fine in Ubuntu 7.04. I took out my old 7.04 cd and booted up the live session and it turned out what he said was true! 3D worked perfectly fine: Compiz desktop effects, games, all I could expect from a Mobility Radeon 9000. The strangest thing is that 7.04 uses the "ati" driver for my card and manages all of this, though 7.10 and 8.04 use the same driver and cannot render 3D properly in the least bit. I do not understand at all  what went wrong after the 7.04 release.:confused:

---

