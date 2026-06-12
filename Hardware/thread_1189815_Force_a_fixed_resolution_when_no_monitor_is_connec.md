---
title: "Force a fixed resolution when no monitor is connected"
date: 2009-06-17
forum: Hardware
---

### Post by Amorphous_Snake on 2009-06-17
I am trying to run my PC without a monitor or keyboard/mouse via VNC through my other PCs. But the problem is that when Ubuntu detects that there is no screen connected, it automatically sets the resolution to 800x600 which is completely unacceptable to me. I can fix it temporarily using the nvidia-settings options, but when I restart, it switches back to 800x600. I want to fix it without using nvidia-settings as I also want to use the same technique in another PC that have the free nv driver running in it.

I used to have Mandriva running on the same machines and the option was available through the Mandriva Control Center to force a certain resolution.

Thanks.

---

### Post by Amorphous_Snake on 2009-06-21
Anybody?

---

### Post by Amorphous_Snake on 2009-06-30
Anybody???

I searched the forums and there is no solution. The new xorg.conf doesn't have the same entries that other threads refer to. The threads are old before xorg.conf became fail-safe or whatever.

If I have overlooked some thread, kindly give me the link.

---

### Post by Amorphous_Snake on 2009-07-02
OK. I solved it myself. So much for what ubuntuforums.org used to be...

Anyway, here is what I did, in case someone is in the same boat as me.

Simply when you disconnect the monitor then boot and log through another computer via VNC, press Alt-F2 and then type "gksudo nvidia-settings" assuming that you have the nvidia driver installed. Choose the resolution that you want and then choose to save to xorg.conf. Since you are running this as root, it will save. The next time you restart, the resolution that you chose will be there for you.

To the mods: How can I add Solved to the thread title?

---

