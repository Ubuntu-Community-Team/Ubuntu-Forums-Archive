---
title: "Linux support for LCD monitors with software based menus"
date: 2008-05-01
forum: Hardware
---

### Post by mozartatplay on 2008-05-01
I have been trying to find a driver to control a number of LCD monitors I have recently purchased in order to adjust monitor settings such as colour temperature, contrast etc.

I have a LG L1900R and a Samsung 245T

Both of these monitors come with windows driver software to control the monitor settings. Has anyone started a project to write driver software to control these types of monitors?

---

### Post by teaker1s on 2008-05-02
nvida graphics adapter binary driver will do this

---

### Post by mozartatplay on 2008-05-03
Thanks teaker

I am aware adjusting settings like gamma etc by launching nvidia-settings. 

But lets say someone uses the software based monitor and sets the colour temperature to warm in windows using the display driver that came with the screen. 

You buy this monitor from the person with this setup when the monitor is turned on and now you want to change the colour temperature in Linux. You can fiddle with the nvidia-settings but you won't be able to get the colour range you could get if you were able to control the monitor directly.

---

