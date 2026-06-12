---
title: "touchpad not working on a Toshiba laptop"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by natetheinfamous on 2006-12-25
I am new to Ubuntu and I just installed it on a toshiba L35 series laptop. It works beautifully and I'm very happy with it except for the fact that my touchpad isn't working, It works fine with a USB mouse, however my touchpad just doesn't function. when I look under the Device Manager, under 'Unknown' i see a device called 'SB ALSA Control device' which I assume is probably it. Is their some special driver or utility I need to download? I'm using Ubuntu 6.10 if that helps.
 Thanks,
   Nate

---

### Post by dbbolton on 2006-12-26
i think alsa is sound. is it a synpactics touch pad ?

there's a package for those in the repositories.

---

### Post by natetheinfamous on 2006-12-26
you're right, it is a synaptics touchpad, and it seems to be installed, just not enabled at all. I'm trying to figure out how to configure it.

---

### Post by natetheinfamous on 2006-12-26
I fixed it!

apparently, this model of touchpad disables at the hardware level or something, because I had temporarily disabled it in Windows (I'm dual booting) and forgotten to re-enable it before rebooting in Ubuntu, thus, it wasn't working, However, I re-enabled it in windows and it now works fine. It's interesting how I'm not even using it (much) and windows still manages to stab me in the back. ](*,)

---

