---
title: "Zoom V92 USB modem worked on 9.04; doesn't on 9.10"
date: 2009-11-04
forum: Hardware
---

### Post by frank4360 on 2009-11-04
My Zoom 56K USB dial-up modem model 3095 worked "out of the box" on Jaunty 9.04 - I was amazed as this almost never happens.

I have just upgraded to Karmic 9.10 and it is not recognised - attepmts to use gnomeppp return "No modem was found on your system".

******************

Problem resolved - steps here for those that follow!!

I went to where I had a WiFi connection, and logged on to [http://www.linuxant.com/drivers/dgc/downloads-installer.php](http://www.linuxant.com/drivers/dgc/downloads-installer.php)
to get the latest driver for the Conexant chipset for the Zoom modem.

This site has an auto installer that works fine - except you may have to remove previous "dgcmodem" drivers using the Synaptic Package Manager - the auto installer can fail on this step.

If any part of the Auto Install fails, you have to go back to reload the driver, as the required password changes at each install attempt.

Follow the instructions, and the modem works - I use gnome-ppp to dial.

Beware - if you attempt to test the modem when there is a WiFi connection, it is not detected - you get something like 'ACM0 busy', even if you disconnect the WiFi connection. However the modem worked fine when I got back home to my dial-up only mountain retreat.

---

