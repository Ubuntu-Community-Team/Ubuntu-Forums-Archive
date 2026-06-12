---
title: "ET-2600 won't scan with Ubuntu"
date: 2020-05-15
forum: Hardware
---

### Post by marweis34549 on 2020-05-15
I have a problem with the scann function of my favorite EcoTank printer.
Isn't the Epson  ET-2600 still supported by Ubuntu 16.04? 
It's an extreme useful, easily refilled device. It always worked with this Ubuntu  -- Now suddenly it won't scan.
I would miss this extremely economic printer!
Would you recommend me a mono scanner, like Canon Lide was?

xsane 0.999 says -----  ET-2600_series:
Error during save: Could not create secure file (maybe a link does exist): /home/scann0082.jpg
What does this mean? I'm not native English...

Installed the latest drivers. 
Epson support won't help.
Thank you everybody.

---

### Post by marweis34549 on 2020-05-15
Hello everybody. 
Finally I got help when purchased the vuescan universal scanner driving tool from hamrickdotcom in Florida. The rest was easy. The 'vuescan' app for Ubuntu is working for the epson ET-2600 scanning unit.

---

### Post by csae2608 on 2020-05-27
Hello ,
you can find the printer&scanner driver for Ubuntu 16.04 here @Epson

Linux Drivers @ Epson Center

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

---

### Post by kurt18947 on 2020-05-27
VueScan is excellent. The error message meant that the jpeg image could not be saved. I had a somewhat similar problem with the gscan2pdf app, it would scan but wouldn't save. Log out and log back in and it would then save. I think the problem was a bug in python or something like that. The latest version of gscan2pdf in 20.04 seems to work as expected.

---

