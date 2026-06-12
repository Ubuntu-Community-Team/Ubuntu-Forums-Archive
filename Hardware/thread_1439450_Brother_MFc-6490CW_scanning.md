---
title: "Brother MFc-6490CW scanning"
date: 2010-03-26
forum: Hardware
---

### Post by ceaxer on 2010-03-26
**Brother MFc-6490CW**                                                                             

I have a Brother MFC 6490 with an ethernet connection to the router. From a Windows xp based  workstation I  can access all the functions (scan fax,print)  but can only print from Ubuntu. Is it possible to scan  without a direct usb connection? 

If so How? 

Ceaxer

---

### Post by plucky on 2010-03-26
> **ceaxer said:**
> **Brother MFc-6490CW**                                                                             

I have a Brother MFC 6490 with an ethernet connection to the router. From a Windows xp based  workstation I  can access all the functions (scan fax,print)  but can only print from Ubuntu. Is it possible to scan  without a direct usb connection? 

If so How? 

Ceaxer

Go [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html) and download the **brscan3.deb** file and install.It also has instructions how to set up for a network scanner.

Good Luck

---

### Post by ceaxer on 2010-03-26
I installed this driver but no network device available. I am a new user so I am not sure how to check it .

---

### Post by plucky on 2010-03-26
> **ceaxer said:**
> I installed this driver but no network device available. I am a new user so I am not sure how to check it .

See [Here Step 5](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html)

From a terminal **Applications > Accessories > Terminal**
```
dpkg -l | grep Brother
``` will show if the driver has been installed.It should be the brscan3 driver.

Then again from the terminal ```
 brsaneconfig3  -a  name=Scanner  model=MFC-6490CW  ip=xx.xx.xx.xx
``` The name "Scanner" can be anything you want.You have to find out the IP address of the printer by looking on the router.

To see if it is correct ```
brsaneconfig3  -q  |  grep Scanner
``` or whatever you called it.

Good Luck

---

### Post by ceaxer on 2010-03-26
This worked! thanks a ton:p

---

