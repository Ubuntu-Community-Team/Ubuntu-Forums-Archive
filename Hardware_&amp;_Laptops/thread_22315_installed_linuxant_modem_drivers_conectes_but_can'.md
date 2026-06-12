---
title: "installed linuxant modem drivers conectes but can't surf the internet"
date: 2005-03-26
forum: Hardware &amp; Laptops
---

### Post by jollygreen on 2005-03-26
ok i have a hcf linuxant modem loaded the linux-headers and build-essentails pakages loaded driver go into network manager activate pppo it conects to isp but can't go anywhere in firefox  anyone have any sugestions? by the way i just downloaded and installed the horay preveiw.

---

### Post by jollygreen on 2005-03-27
ok i got on linux using wvdial after following these instructions The ABCs Internet Tutorial Protection 

Settings & Misc



Worldnet Settings Quick Reference Find Your Account Info WURD Site Map 

Help Wurd



Provide Feedback Make a Submission



Credits & Copyright



©2005 AT&T Corp. Home » Setup » Dialers » wvdial  





wvdial and AT&T Worldnet Service

The wvdial dialer is an intelligent PPP dialer, which means that it dials a modem and starts PPP in order to connect to the Internet. It uses heuristics to guess how to dial and log into your server rather than forcing you to write a login script.



Intelligent programs are frustrating when they don't work right, and I never did get wvdial to work out-of-the-box for connecting to Worldnet. I've got it working now but here are some of the places that need a little tweaking to get it going.





--------------------------------------------------------------------------------



Initial Configuration

wvdial will first need to find and probe your modem, and then set up a standard configuration file. Then you will need to edit it to work with AT&T Worldnet.



As root, in a terminal window, type this command: 

# wvdialconf /etc/wvdial.conf 

This will identify the port your modem is on, establish an initialization string for your modem and save the results in the /etc/wvdial.conf directory. 

Edit /etc/wvdial.conf to reflect your local Worldnet phone number, logon ID and password. As root, use your favorite plain text editor to remove the ; from in front of Phone, Username, and Password, then change those lines to reflect your situation. For example: 

Phone = 1234567 

Username = [email]123456789@worldnet.att.net[/email] 

Password = abcdefg-hijklmn 

Note: For these entries you need to replace the parts after the = with your individual number to call, username, and password. The above items are just example of the format your information should be in. 

Check your wvdial.conf file for these two entries: 

Stupid Mode = 1 

Auto DNS = 1 

If they are not there, add them or make other appropriate changes so they are there. With Stupid Mode turned on, wvdial will bring up pppd right away. 

Save your customized wvdial.conf and exit the text editor.



can't remember exactly where i got them thanks for the links in the forums kept searching for the internet and this is what i found 
thanks for you guy answering post

---

