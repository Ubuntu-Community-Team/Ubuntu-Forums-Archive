---
title: "Lubuntu 21.04 PS3 DS3 automatically power off and right analog issues"
date: 2021-06-12
forum: Hardware
---

### Post by aug7744 on 2021-06-12
Hello.
Using Lubuntu 21.04 64 bits and Playstation 3 Dualshock 3 controllers using wired connection.

Both controllers had worked in windows. Now in Linux has issues.

Pressing the PS button enable the controller, but the controller will be power on at 20 minutes and after automatically will be power off. The strange detail is that disconnected from wired trying to power on using the PS button to bluetooth connection the controller not power on.
Need some hours to controller work again being an issue that begin to happen since the first time trying use in Linux.
Other problem is right analog is totally to up being not pressing buttons or moving analog sticks.

Thus I had tested with another PS3 DS3 controller using wired connection and the same problem with right analog.
Avoiding use that controller if anything is damaging the controllers.
Have an problem with right analog axis in Ubuntu PS3 controller driver ?

Anyone has tested PS3 DS3 controllers in Ubuntu ? works without problems ?
Have chance that HIDAPI or other controller api send data to controller and make problem in eeprom ?

Thanks for your reply.

---

### Post by VMC on 2021-06-12
Have you looked at your logs? Check dmesg for any errors related after power off ```
sudo dmesg
```
```
journalctl -b
``` will give latest errors. Go to end of file right after you encounter power-off

---

### Post by aug7744 on 2021-06-26
I will test and after post the result here.

---

