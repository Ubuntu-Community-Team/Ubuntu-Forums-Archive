---
title: "How to install my intel onboard graphics card?"
date: 2012-12-03
forum: Hardware
---

### Post by silysnipe on 2012-12-03
my laptop is running on an intel 3000 series onboard graphics card and i was wondering if there was a way to install the graphics card.

---

### Post by BlinkinCat on 2012-12-03
> **silysnipe said:**
> my laptop is running on an intel 3000 series onboard graphics card and i was wondering if there was a way to install the graphics card.

Hi,

Ubuntu automatically detects your intel graphics and installs it for you -

Cheers - :)

---

### Post by silysnipe on 2012-12-03
so i dont need to install any other drivers? and why does it say the graphics card is unknown in the details?

---

### Post by Isamu715 on 2012-12-03
The driver is installed correctly. If your graphics card is shown as *"Unknown"* then it means that the system cannot acquire the information because *glxinfo* is not installed on the
system. Install it using:
```
sudo apt-get install mesa-utils
```Your graphics card should show up correctly in system details then.

---

### Post by silysnipe on 2012-12-03
yes it has " intel sandybridge mobile". mobile i assume because im on my laptop. but it has the experience is "Standard" is there anyway to make it more? for better graphics? or should i leave it alone?

---

### Post by Isamu715 on 2012-12-03
There are only two types of graphics experience: "Standard" and "Fallback", if everything works fine it's "Standard" and when there's no 3D acceleration or other problem it's "Fallback".

If you want to improve performance you can enable [SNA acceleration]("http://www.webupd8.org/2012/10/how-to-enable-intel-sna-acceleration-in.html") or use more [updated drivers]("https://launchpad.net/~glasen/+archive/intel-driver"). But there's really no need to do anything if the system is working fine for you.

---

### Post by silysnipe on 2012-12-03
oh ok, thank you sir. it really helped me out :D

---

