---
title: "need help in driver for NVIDIA GeForce 7000"
date: 2008-08-05
forum: Hardware
---

### Post by kamekazekit on 2008-08-05
hello, everyone im starting to explore how to install drivers for my video then, i downloaded some packages for nvidia im just wondering why my geforce 7000 video card is not on the list of the supported graphics card can anyone help me thank you! im sorry if my terms are so mess up im still a newbie.

---

### Post by Nepherte on 2008-08-05
Go to System->Administration->Hardware Drivers and check the box to enable the restricted drivers for your nVidia card if the option is provided.

---

### Post by kamekazekit on 2008-08-06
there's a red button saying in status not in use. how can i fix it thanks once again

---

### Post by phidia on 2008-08-06
> **kamekazekit said:**
> there's a red button saying in status not in use. how can i fix it thanks once again

There's a little box in the column labeled "enabled" click/check that box.

There's a guide with screenshots [here]("http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200").

---

### Post by kamekazekit on 2008-08-06
it was enabled still the status is not in use 
the device driver column  displays nvidia_new and also when i check the enabled box it doesnt look for a driver it confirms automatically to restart the system, what could be wrong? thanx for the help again.

---

### Post by abhilashkumar on 2008-08-06
In my case, ubuntu downloaded the drivers after I checked for it to use the restricted drivers. 

Did yours install anything automatically after the restart or before?

---

### Post by kamekazekit on 2008-08-06
no prompt at all

---

### Post by Nepherte on 2008-08-06
You could always use envy if it doesn't work. Uncheck the nvidia hardware driver and install envy (P.S. every code block should be run in a terminal: Applications menu -> Accessories -> Terminal):
```
sudo apt-get install envyng-gtk
```

Afterwards run envyng:
```
envyng -g
```

I suggest you choose 'remove the nvidia driver' first, to make sure it is actually removed and will not interfere with a new installation. Afterwards you can choose to 'install the nvidia driver automatically'.

Hopefully that works for you.

---

