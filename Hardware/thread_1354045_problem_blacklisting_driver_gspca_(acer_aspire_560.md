---
title: "problem blacklisting driver gspca (acer aspire 5600)"
date: 2009-12-13
forum: Hardware
---

### Post by dencamel on 2009-12-13
Hello,


I have installed ubuntu 9.10 on an acer aspire 5600 and I have a very slow startup.
When checking the logs I see that there's a difficulty with a driver. After some searching I found out it had to do with the webcam (orbicam).  

I decided to blacklist the driver by adding the following line in the file /etc/modprobe.d/blacklist : blacklist gspca.
Since this had no effect I also added the same line in the /etct/modprobe.d/blacklist.conf but also not with the desired result.

Anybody an idea why the blacklist does not work?

Here's the log with the problem probing gspca:
803.673202] gspca: probing 046d:0896
[32803.673521] vc032x: check sensor header 2c
[32803.699652] vc032x: I2c Bus Busy Wait 2c
[32803.732675] vc032x: I2c Bus Busy Wait 2c
[32803.736781] vc032x: I2c Bus Busy Wait 2c
[32803.769781] vc032x: I2c Bus Busy Wait 2c
[32803.802781] vc032x: I2c Bus Busy Wait 2c
[32803.835781] vc032x: I2c Bus Busy Wait 2c
[32803.868779] vc032x: I2c Bus Busy Wait 2c
[32803.901779] vc032x: I2c Bus Busy Wait 2c
[32803.936035] vc032x: I2c Bus Busy Wait 2c
[32803.969029] vc032x: I2c Bus Busy Wait 2c
[32804.005281] vc032x: I2c Bus Busy Wait 2c
[32804.039406] vc032x: I2c Bus Busy Wait 2c
[32804.072406] vc032x: I2c Bus Busy Wait 2c
[32804.105405] vc032x: I2c Bus Busy Wait 2c
[32804.138781] vc032x: I2c Bus Busy Wait 2c
[32804.171780] vc032x: I2c Bus Busy Wait 2c
[32804.204946] vc032x: I2c Bus Busy Wait 2c
[32804.238156] vc032x: I2c Bus Busy Wait 2c
[32804.238163] vc032x: Unknown sensor...
[32804.238195] vc032x: probe of 1-6:1.0 failed with error -22
[32804.238360] usb 1-6: USB disconnect, address 56


Thanks for any info on this.

---

### Post by dencamel on 2009-12-14
Ok I found the solution in another thread.
Apparently you have to blacklist gspca_vc032x...

---

