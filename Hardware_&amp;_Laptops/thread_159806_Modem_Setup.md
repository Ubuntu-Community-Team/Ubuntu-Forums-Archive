---
title: "Modem Setup"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by brim4brim on 2006-04-13
Hi,

I've got my mobile phone setup to connect with my laptop through USB in Windows.  However I wish to get it working with Ubuntu so I can update Synaptic properly.  

Anyway I've got the settings from my ISP so I was wondering could someone here help me set it up.  My phone is a Motorola V3 and these are the settings from my ISP for GPRS.

> 
extra initialisation command:
AT+CGDCONT=1,"IP","ISP.MYMETEOR.IE"
Siemens is *99***1# and 
*99# for all other phones.

First Pair up your handset and your computer then follow the steps below:



Menu> Programmes> Accessories> New Network connection Wizard


Connect to the INternet 

Set up my Connection Manually 

Connect using a dial up modem 

Select Desired modem 

Next Name it 

Type the Phone number *99# 

Add a shortcut to your desktop


Menu> Settings> Control Panel> Phones and Modems> 

Select desired modem 

Click Advanced 

Enter the initailisation string 

No user name or Password  (if you receive a hardware failure then put in 'meteorisp'  as the username and password. ) 

Then the phone number *99# 

UNTICK dialing rules.


Can anybody help me set this up in Linux.  I've tried just the basic setup by entering the phone number but the phones modem isn't auto-detected by Ubuntu.

Thanks for any help.

---

