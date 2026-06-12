---
title: "Root System?"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by wolfman1221 on 2009-02-21
I was wondering if someone could help me. I just recently installed ubuntu, and when I boot it I reach a message  that says no root system is defined and that I need to fix it  in the partition menu. Does anyone know how to correct this?

---

### Post by taurus on 2009-02-21
Did you install Ubuntu on it own partition or did you install it from windows?  When you install Ubuntu, you need to declare which partition to mount as / (root filesystem).

---

### Post by wolfman1221 on 2009-02-21
I'll admit it, I'm really new at this, so I used partition magic, and I used the install another operating system option on that particular program. I am using windows xp.

---

### Post by cariboo on 2009-02-21
Boot from the LiveCD and once at the desktop go to System-->Administration-->Partition Editor and set the root partition.

Once you have the partitions showing in the window click on the partition you set up for Ubuntu, then click the edit button. there in be a dropdown box near the lower right select / and then apply.

My instructions may not be exact, as I am doing then from memory.

Jim

---

### Post by wolfman1221 on 2009-02-21
Okay, that thing is a friend of mine set this up for me. He installed some program called Daemon tools lite, which he said I could use in place of cd. I did this once without a cd, and it worked fine. When I uninstalled ubuntu, and tried to install it again this is when I received this message that said no root system is defined.

---

