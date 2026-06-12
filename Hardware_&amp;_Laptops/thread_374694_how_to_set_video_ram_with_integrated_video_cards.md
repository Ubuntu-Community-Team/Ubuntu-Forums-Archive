---
title: "how to set video ram with integrated video cards"
date: 2007-03-02
forum: Hardware &amp; Laptops
---

### Post by manutdfan2850 on 2007-03-02
Hi
on my laptop i have a ATI mobilitry Radeon 9000 IGP and I am running the default ubuntu drivers. (did not install ATI drivers).

how can I increase the amount of ram that is dedicated to video? I know in windows i just went to the display properties and it was very easy to change form 32 to up to 128. how can I do this in ubuntu?

thanks.

---

### Post by po0f on 2007-03-02
manutdfan2850,

Can you not do this from the BIOS?  With my Intel integrated graphics chip, I can set the memory usage in the BIOS, I've never use an ATi card though.

---

### Post by manutdfan2850 on 2007-03-03
i have no idea

i remember at some point i was istalling beryl and i went into some blue menu where i defined my video ram to be 32 mb

that was before i upgraded my main memory to 1gb now i can spare 128 to video ram. 

i just cant remember what that menu was.

---

### Post by Prometheus.172214 on 2007-03-03
Well as far as I have known the video memory of an integrated video controller is from the BIOS (Like manutdfan2850 said). However certain applications can modify these settings. I have not used Beryl, but would recommend checking the BIOS for the setting first.

---

### Post by manutdfan2850 on 2007-03-06
now i remember, it was in the Xorg configuration

how can i check what my video ram is now and if necessary how can i change it using xorg?

---

### Post by Githlar on 2007-07-30
As far as checking the current video RAM, I'm not sure. However, you can change it using the XServer config using this command:

sudo dpkg-reconfigure xserver-xorg

---

