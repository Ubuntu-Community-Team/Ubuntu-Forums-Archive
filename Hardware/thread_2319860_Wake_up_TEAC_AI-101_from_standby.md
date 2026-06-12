---
title: "Wake up TEAC AI-101 from standby"
date: 2016-04-08
forum: Hardware
---

### Post by afgibson on 2016-04-08
I am caught in a bit of a catch-22.  The TEAC AI-101 is built to go into standby after 30 minutes of no input, but designed to exit stand-by on detection of a digital signal on the USB port.  However, Ubuntu recognizes the TEAC DAC/AMP as a USB sound card.  All works well as long as it is on.  However, once it enters standby, Ubuntu sees no longer detects the presence of a USB sound-card.  So attempts to send digital output to the AMP result in the error.
aplay: device_list:268: No sound card found... 
At the moment I have the inelegant solution of cronning the Ubuntu server to send .1 seconds of silence (as an MP3 file) to the USB DAC/AMP every 10 minutes. This works by preventing the TEAC AI-101 from entering standby mode.   I would prefer to allow the TEAC to go into standby and then "wake it up" on the need to send music to it.  Any thoughts on how to accomplish this?

---

