---
title: "Dual Monitors"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by catch2two on 2007-07-14
Okay this is my third attempt to make the switch from MS. I am a complete noob, but i did it, no dual boot just had to make the switch and cut MS out of my life forever.

So far i am very happy with this version and think it will suite my needs fine.

My only fear so far is no dual screens. I cannot go back to one screen.

Please can anybody help me?

Is this going to be too hard to set up for a noob?

I have a nvida PCI express with one vga monitor and one digital monitor of different res.

I do have clone screens at the moment.

If anyone can help me set them up my transition to linux will be complete.

---

### Post by IntuitiveNipple on 2007-07-14
Assuming you are using the Nvidia proprietary driver (that includes the Nvidia configuration utility):

Make sure you've got both displays connected, then:

**Applications > System Tools > NVIDIA X Server Settings**

On the **X Server Display Configuration** page press the **Detect Displays** button. Select the new screen in the preview window then press **Configure...** and choose **Twinview**.

Save settings and restart GDM and you should have 2 3D-accelerated screens sharing one large  desktop space.

---

