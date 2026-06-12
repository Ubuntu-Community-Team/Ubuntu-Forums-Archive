---
title: "[SOLVED] ATI Radeon xpress 1250 problem. Ubuntu 8.04. Please Help!"
date: 2008-11-15
forum: General Help
---

### Post by Marius Derekus on 2008-11-15
Hello,
I am dual booting widows vista and Ubuntu 8.04. I have an ATI Radeon xpress 1250 graphics card. When i don't have the graphics card enable(through**system>adminidtration>hardware drivers**), somthing like opengl or mesa is used(I don't know how that works.). When the graphics card wasn't enabled, wolfenstein: enemy territory ran (an advanced 3d game) just very slowly. When i enabled the graphics card and reboot, the computer shows the ubuntu bootup screen, but once it gets to the login screen it goes black. To fix this, I ran ubuntu through recovery mode (fix x-server) and it booted up right, but the graphics card was then disabled. Is there any thing i can do to enable my graphics card without any issues?
Perhaps edit something in /etc/x11/xorg.conf

---

### Post by Marius Derekus on 2008-11-15
I downloaded this file: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) 

Would that fix the issue?

---

### Post by Marius Derekus on 2008-11-15
I think i have fixed the issue.

---

### Post by Stünky on 2009-02-24
Hi Marius,
   Please can you share how you solved the problem? Thank you.

---

