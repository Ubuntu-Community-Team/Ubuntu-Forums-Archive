---
title: "Brother mfc-l3770cdw can not get scanner to work"
date: 2019-07-08
forum: Hardware
---

### Post by halfprice5 on 2019-07-08
I have searched the forums & brother support howto's, I have done as suggested no joy.

I'm running 18.04 lts

Any suggestions specific to 18.04 lts?

I'm a command line noob so I need detailed instruction

---

### Post by him610 on 2019-07-08
Brother does a good job supporting Linux, both Red Hat and Debian (Ubuntu). 
Note: Before you begin, recommend you assign a static IP address to your MFC device. If you don't know how, refer to your user manual.

Go to this Brother webpage, [https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcl3770cdw_us_eu_as&os=128]("https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcl3770cdw_us_eu_as&os=128")
Download (click on it) the *Driver Install Tool* Be sure to be sure you read and understand the notes before downloading, and the How to Install instructions. 
The file you will be downloading is, *linux-brprinter-installer-2.2.1-1.gz*
In step 6, How to Install Instructions, substitute your model, MFC-L3770CDW for the one in the script.
In step 7, DeviceURI is the static IP address you should have entered as recommended in the Note above.
Follow the prompts, respond as necessary.
 
Good luck.

---

### Post by halfprice5 on 2019-07-09
I get to step 4 and this happens, need help from here on

 Step4. Enter this command to extract the downloaded file:

Command: gunzip linux-brprinter-installer-2.2.1-1.gz  no password entry for user

e.g. gunzip linux-brprinter-installer-2.2.1-1.gz

Step5. Get superuser authorization with the "su" command or "sudo su" command.

Step6. Run the tool:

Command: bash linux-brprinter-installer-2.2.1-1 mfc-l3770cdw
e.g. bash linux-brprinter-installer-2.2.1-1 MFC-l3770cdw          no password entry for user

Step7. The driver installation will start. Follow the installation screen directions Nothing happens

---

### Post by halfprice5 on 2019-07-09
Solved

---

### Post by him610 on 2019-07-09
Great! Please mark it solved using the thread tools.

---

### Post by stelios10 on 2019-11-18
How was it solved? Would You please elaborate? I am planning on buying this all-in-one and would like to know before I run into trouble

---

