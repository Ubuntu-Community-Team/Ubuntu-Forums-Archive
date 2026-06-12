---
title: "CD/DVD Problem"
date: 2011-02-24
forum: Hardware
---

### Post by raunhar on 2011-02-24
The problem is very strange.
Even after I take out the disk from the drive, the icon of the disk shows even after that.
The icon still remains even after I insert some other disk. The current disk does no show the contents but shows the content of the previous disk.
To correct that I have to restart the PC.

What to do.
The DVD drive is of Sony

---

### Post by zenwalker on 2011-02-24
Does this happen even if you Right click and say Eject option? Then it seems to be a problem with the Udev/HAL. But i am not sure. Try updating your system and try again.

---

### Post by theozzlives on 2011-02-24
I agree, use eject or unmount before switching CD/DVDs.

---

### Post by raunhar on 2011-02-24
If i press the Eject option on right click, it goes off, but on pressing the button on the drive, it still remains.

---

### Post by zenwalker on 2011-02-24
Its much safer this way than force ejecting. But the latest udev/HAL (HAL is obselete now) should be able to detect the force ejection. Atleast on my distro it works. May be try a new ver of your distro.

---

### Post by raunhar on 2011-02-24
WHich distro do you have.
I have Ubuntu 10.10
I just saw that HAL is not installed.
 I have installed it now.

---

