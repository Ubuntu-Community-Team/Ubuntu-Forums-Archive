---
title: "hardware modem problem"
date: 2005-03-01
forum: Hardware &amp; Laptops
---

### Post by xenocide on 2005-03-01
Hi,
I was thinking about switching from slackware to ubuntu so I tried out the ubuntu live cd today.  Everything was fine with sound, video, ect however ubuntu did not detect my external modem.  I tried using wvdial and it said modem was either busy or not found and I could not use the networking app in gnome either.  This is weird because every other distro I have tried has detected it perfectly as it's not a winmodem...I don't know where  I would find drivers for the modem either as it has no info listed on it.  My question is, would the full install detect my modem or is there anything else I can do to find out info about my modem for drivers? Thanks!

---

### Post by m4ng0 on 2005-03-01
If you have a SERIAL external modem, you do not need any driver.
Try:
sudo pppconfig
and use /dev/ttyS0 (or /dev/ttyS1 ...) for device if your modem is connected to COM1 (or COM2 ...)

Things can change if you have a USB external modem. What kind of modem do you have?

---

