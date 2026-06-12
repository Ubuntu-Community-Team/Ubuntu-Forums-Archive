---
title: "Can't use external monitor"
date: 2010-03-27
forum: Hardware
---

### Post by Goldwolferadior on 2010-03-27
I have a msi A6000 laptop with a nvidia GeForce 8200m. I have installed the recommended proprietary driver for the graphics card.

The problem occurs when I try to use my Gateway FPD1810 monitor that I have connected to my laptop. I go into the X server, enable the monitor, click "Save to X configuration file", and get this message:
Failed to parse existing X config file '/etc/X11/xorg.conf'!

Is there any way to fix this problem so I can use my external monitor?

---

### Post by 2hot6ft2 on 2010-03-28
> **Goldwolferadior said:**
> I have a msi A6000 laptop with a nvidia GeForce 8200m. I have installed the recommended proprietary driver for the graphics card.

The problem occurs when I try to use my Gateway FPD1810 monitor that I have connected to my laptop. I go into the X server, enable the monitor, click "Save to X configuration file", and get this message:
Failed to parse existing X config file '/etc/X11/xorg.conf'!

Is there any way to fix this problem so I can use my external monitor?
In order to be able to save the configuration you have to start nvidia-settings as root so start it like this:
Open a terminal
Applications > Accessories > Terminal
and run
```
gksu nvidia-settings
```
You will have to enter your password and hit Enter
Then you will be able to save it.

---

### Post by Goldwolferadior on 2010-04-02
OK, so I ran the code you gave me, but it still gave me the error message. Along with that, on the command line, it gave me:

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

Is there any way to fix this problem?

---

