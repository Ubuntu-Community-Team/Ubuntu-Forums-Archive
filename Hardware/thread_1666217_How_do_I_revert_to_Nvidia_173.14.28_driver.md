---
title: "How do I revert to Nvidia 173.14.28 driver?"
date: 2011-01-13
forum: Hardware
---

### Post by AlFrugal on 2011-01-13
I downgraded the graphics card on my PC from a GeForce 6200 to a GeForce FX5200. The PC runs Ubuntu 10.10. After the graphics card downgrade, I no longer get a GUI. The GeForce 6200 used a 260.19.29 driver. (I get my Nvidia drivers from the Ubuntu repositories). The GeForce FX5200 requires a 173.14.28 driver. I don't know the correct procedure for installing this driver.

This is what I tried:

sudo apt-get purge nvidia*

sudo apt-get install nvidia-current

[restart PC]

sudo nvidia-xconfig

[Log out, log back in]

After performing the above, I still had no GUI.

I believe I need nvidia-graphics-drivers-173 and/or nvidia-173.

What is the correct procedure for obtaining the Nvidia driver for my GeForce FX5200? (Since I no longer get a GUI, the procedure must be from the command line.)

I read the "BinaryDriverHowToNvidia" in the Ubuntu Community Documentation. The information I'm seeking might be there, but I didn't recognize it.

---

