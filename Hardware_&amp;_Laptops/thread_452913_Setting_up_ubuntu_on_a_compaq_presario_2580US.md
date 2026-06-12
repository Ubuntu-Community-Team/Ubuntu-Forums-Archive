---
title: "Setting up ubuntu on a compaq presario 2580US"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by mdwag17 on 2007-05-23
I've been recently trying to make the switch from windows to linux, but I have run into some issues with setting up ubuntu on my laptop. My laptop is a compaq presario 2580US, see url for product specifications. 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00248814&lc=en&cc=us&dlc=en&product=374872&query=dm758a](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00248814&lc=en&cc=us&dlc=en&product=374872&query=dm758a) 

My main issues I'm having are with setting up the my wireless internet card and getting the video drivers to work properly. What I need is a step by step guide on how to set these two things up. Also based on the specifications attached to the url if there are any other drivers that can available for installation that are compatible with ubuntu than please let me know. Plus, any step by step installation instructions would be very helpful.

thank you

---

### Post by teaker1s on 2007-05-25
firstly take a look here
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

secondly you will either have broadcom or possibly intel wireless, you can check by using
```
lspci
```
```
lsusb
``` if your not sure post output

then this may help
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29")

---

