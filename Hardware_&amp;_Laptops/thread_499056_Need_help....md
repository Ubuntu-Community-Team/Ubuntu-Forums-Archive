---
title: "Need help..."
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by arijel on 2007-07-12
I'm using ubuntu feisty with hp nx6325 laptop. After installing drivers from linuxant, for my modem, I'm getting strange error. When I connect to ISP using wvdial, the connection breaks after a few seconds with message that pppd died with exit status 16. I tried different init strings received from support stuff from linuxant, but non is working. The support stuff told me that this is probably hda bus stability issue, and I found that before I get disconnected I receive this message in /var/log/messages:
hda_intel: azx_get_response timeout, switching to polling mode... 
and then connection breaks. 
This is the message I'm receiving when booting:
hsfhda: no version for "cnxthsf_OsHdaCodecClearEventCallback" found: kernel tainted.
Can anyone help to figure out what is the cause to this problem?
Is this maybe related to ALSA drivers?

---

