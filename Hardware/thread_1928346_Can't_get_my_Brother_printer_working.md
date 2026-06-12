---
title: "Can't get my Brother printer working"
date: 2012-02-19
forum: Hardware
---

### Post by AnthonyReid99 on 2012-02-19
I'm running Ubuntu 10.11 (on an Acer AspireOne Netbook) and I'm trying to install a Brother MFC-J825DW printer/scanner. It isn't in the default list of drivers presented when I try to install it, so I downloaded drivers from the Brother website. They offer both an LPD driver and a cupswrapper driver. The first time I installed the LPD driver package and it worked perfectly right away. However, I've had to reformat and install Ubuntu again and now it isn't working. I can install the LPD driver, but the printer is still not installed. When I try to install the cupswrapper driver, it claims that there is a dependency error; the LPD driver package is not installed. However, it IS installed and the name is exactly the same as the package it is claiming is not installed. When I try to force its installation (--force-all), the printer is finally acknowledged by Ubuntu but when I try to print, I get an error message that the filter is not installed. Any ideas?

---

### Post by AnthonyReid99 on 2012-02-20
UPDATE: I managed to get it working, and I'll leave this thread up for anybody else in  the same situation to see. I tried installing drivers for another printer just to see. It didn't end up working, but I was able to install the cupswrapper after the lpr driver and there was no false claim that the lpr driver package was not installed. I concluded that the drivers for my printer were simply defective. So I downloaded the rpm versions of them, hoping the same bug was not present in them. I used alien to convert these rpm packages into deb packages and installed those (make sure to use the argument --script, or the post installation scripts that set up the printer won't be retained). I no longer got a dependency error, and the printer installed successfully. I changed the location of the printer in settings, sent a test page, and success was had! There's a good chance my strategy has no merit and this just happened to work for some other reason I can't think of, but if you are in the same situation, give it a try.

---

