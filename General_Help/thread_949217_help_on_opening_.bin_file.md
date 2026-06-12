---
title: "help on opening .bin file"
date: 2008-10-15
forum: General Help
---

### Post by ybae on 2008-10-15
I am trying to run this file after downloaded from dd-wrt.  but I get this message.  I did: 

chmod u+x filname.bin 
sudo ./filename.bin 

sbi@sbi-laptop:~/Desktop$ sudo ./dd-wrt.v24_micro_generic.bin
./dd-wrt.v24_micro_generic.bin: 1: HDR0&#65533;&#65533;0f&#65533;: not found
./dd-wrt.v24_micro_generic.bin: 2: Syntax error: ")" unexpected

Can anyone help me?

Thank you.

SAm

---

### Post by Mister.Vash on 2008-10-15
Are you trying to upgrade your wireless router?  That file should be the firmware that you upload to your wireless router directly, it isn't an executable file that you would run on your machine.

See the page [http://www.dd-wrt.com/wiki/index.php/Installation#Logging_In_to_the_Web_GUI](http://www.dd-wrt.com/wiki/index.php/Installation#Logging_In_to_the_Web_GUI)
 for instructions on how to logon to your router and how to update the firmware.  You should also check the list and see if your device is supported and that you have downloaded the correct software for the model of your device.

---

### Post by jerome1232 on 2008-10-15
> **Mister.Vash said:**
> Are you trying to upgrade your wireless router?  That file should be the firmware that you upload to your wireless router directly, it isn't an executable file that you would run on your machine.

See the page [http://www.dd-wrt.com/wiki/index.php/Installation#Logging_In_to_the_Web_GUI](http://www.dd-wrt.com/wiki/index.php/Installation#Logging_In_to_the_Web_GUI)
 for instructions on how to logon to your router and how to update the firmware.  You should also check the list and see if your device is supported and that you have downloaded the correct software for the model of your device.

Let me second that word of caution, **You can brick your router**, and it won't even make a very good brick, if you load it with incorrect firmware or the process fails.

---

