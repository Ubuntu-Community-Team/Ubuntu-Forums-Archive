---
title: "Brother MFC-9120CN Network Printer"
date: 2012-08-07
forum: Hardware
---

### Post by JLUbunt on 2012-08-07
Hello I have installed Ununtu 12.04 LTS on my HP ProLiant ML110 G6 computer. 

 It is a network printer.  

It is a dual Boot system and has a version of Linux Susi which was installed by someone who understands Linux.  
There is also a laptop computer running Windows 7 plugged into the modem.  The laptop is not networked with the Linux system. 

The Brother Printer works on both Susi and the laptop.

I have only recently installed Ubuntu and propose to replace the Susi installation when and improve my skills in Ubuntu.  

The installation of 12.04 found the printer and installs the drive below.  But when I try to print the test page or anything else I get the error message below.

I've looked on the Brother site and found the Brother MFC-9120CN but do not know what to do.
Any ideas why 12.04 finds the printer to install the driver but not when I want to print.

Thanks Jeff


 Description 		Brother MFC-9120CN
 Location 		BRN001BA94E892E
 Device URI		lpd://BRN001BA94E892E/BINARY_P1
 Make and Model	Brother MFC-9120CN BR-Script3
 

 Error message 	Processing - Unable to locate printer "BRN001BA94E892E".

---

### Post by kurt18947 on 2012-08-07
Here is my experience with Brother networked MFDs.  They closely parallel HP.  I've had the best luck using HP's JetDirect.  I assign a static I.P. to the printer then in the device URI window type this:

```
socket://xxx.xxx.xxx.xxx:9100
```  where x=printer's i.p. address.  I've found this to be reliable.  If you find print speed slow, you can also substitute CUPS for BrScript3.  I had this issue with an older laser MFD.  It'd print about 3-4 pages/minute using BrScript3 and 20+pages/minute using CUPS.  Newer printers may not have this issue.

---

### Post by JLUbunt on 2012-08-08
Hi Kurt

 Thanks for the reply. The person who set up the Susi suggested that I a reassign the dynamic to static IP addresses for the Internet connection Router. I expect he also set the static IP address for the printer.  

I had a look on Google and understand that I need to find the current IP addresses. Select an address then enter a command to change them. Do you know a reference guide I should look at or, better still  a list of commands I should use to find the info.

Then those to to set the Static address.

Thanks 

Jeff

---

### Post by kurt18947 on 2012-08-08
Hi Jeff

Here is a page on Brother's site.  Look down a little and you'll see 4 pdf publications  listed.  The network user's manual will  tell you more than you probably wanted to know.

[http://www.brother-usa.com/SiteSearch.aspx?sk=MFC-9120CN](http://www.brother-usa.com/SiteSearch.aspx?sk=MFC-9120CN) 

You don't need to use Bradmin,  you can do what you want via the machine's display & keypad.  Once you  know/have assigned an i.p. address and establish a connection,  you might be able to do quite a lot of administration via a web browser.  I'm not familiar with the MFC-9102CN but here is the first 'page' of a MFC-7820N
[ATTACH]222413[/ATTACH]

It seems inkjet MFDs don't have the web administration.  Your machine is a laser so it may have the web admin.  If it does, you'll want to change the default user name and password.  Otherwise a networked printer can become an network attack point.

---

### Post by JLUbunt on 2012-08-09
Hi Kurt
Thanks for the info.  I'll have a look at the manual at the week end.  I'm not from an IT background. I've been casually using Linux for quite a while but never put enough effort in to reach a critical mass to feel comfortable with it.  I think learning how ot make a static IP address would be good for me particularly given your comment that the network printer can be a source of attack.

I've see some Linux courses on line which might let me learn in a less urgent way when there is a problem.  Will let you know how i get on. 
Thanks 
Jeff

---

### Post by joubejo on 2012-10-30
well I had spent a few days trying to connect to the printer after installing the necessary drivers and suing 
socket://xxx.xxx.xxx.xxx:9100 resolved the problem right away. thank you.

---

