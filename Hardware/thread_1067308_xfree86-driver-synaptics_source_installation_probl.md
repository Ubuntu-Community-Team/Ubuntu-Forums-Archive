---
title: "xfree86-driver-synaptics source installation problem"
date: 2009-02-11
forum: Hardware
---

### Post by mzakharo on 2009-02-11
Hi, I am having troubles launching the synaptics dirver module after manually compiling it from source code. Here are the steps I have performed:

 I have downloaded the source package for synaptics driver from here [http://packages.ubuntu.com/source/intrepid/xfree86-driver-synaptics]("http://packages.ubuntu.com/source/intrepid/xfree86-driver-synaptics"). I have removed original xserver-xorg-input-synaptics package. I installed all of the dependencies and successfully ran the .configure && make and sudo make install command - no errors. However, upon restarting X, the oputput of  /var/log/Xorg.0.log is the following

```
(II) LoadModule: "synaptics"

(WW) Warning, couldn't open module synaptics
(II) UnloadModule: "synaptics"
(EE) Failed to load module "synaptics" (module does not exist, 0)
(II) LoadModule: "record"
```

The module fails to load. My xorg configuration file seems correct (I attached it here just in case). I am stumbled at this point. The readme says that I can start X with additional debugging messages - with the following command :startx -- -logverbose 8 , but I am not sure where and when to run this command.

---

### Post by mzakharo on 2009-02-12
I think I found the problem, the driver from source by default installs synaptics_drv.so into /usr/local/lib/xorg/modules/input. However, the official ubuntu package installs the above mentioned file to /usr/lib/xorg/modules/input. Could that be it, and if so, how do I make the installer install to a non default directory?

---

### Post by mzakharo on 2009-02-12
I am really stuck here. Can anyone help me with this, or why would nobody answer my questions? Is it too technical for this kind of forum ( I noticed that a lot of noob questions are asked here, and mine is well, a bit advanced. Is there maybe a better place to turn to?

---

### Post by mzakharo on 2009-02-12
thanks, solved this one myself. had to use ./configure --exec_prefix=/usr 

Thanks for all your help!

---

