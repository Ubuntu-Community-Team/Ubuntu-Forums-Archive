---
title: "Dell Inspiron B130 wireless troubles"
date: 2006-03-11
forum: Hardware &amp; Laptops
---

### Post by bklebel on 2006-03-11
I am trying to get my wireless working on my Dell Inspiron B130 laptop but its not working. Any help would be greatly appreciated.

thanks

The wireless adapter is an internal: Dell Wireless 1370 WLAN Mini-PCI Card

---

### Post by teeb on 2006-03-11
this might help

[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

---

### Post by K.Mandla on 2006-03-12
I got one of these to install on a 600m. There's a good step-by-step here ...

[http://ubuntuforums.org/showthread.php?t=120383](http://ubuntuforums.org/showthread.php?t=120383)

for making one work. I see there are also a few people who've had problems with it beyond just *ndiswrapper*, but it looks like they usually got it to work.

Good luck!

---

### Post by bklebel on 2006-03-14
I followed the instructions teeb posted and they seemed pretty straigh forward.   

I went through the steps and when i went to list the installed drivers in ndiswrapper it says its its an invalid driver.  I am pretty sure this is the correct driver because my wireless works when I am running windows.  I am not sure what do now??? ](*,)

---

### Post by bklebel on 2006-03-14
any ideas?

---

### Post by teeb on 2006-03-15
Which driver file did you use?

I copied the addon directory to my home directory and then pointed ndiswraper at the bcmwl5a.inf file

the addon directory is here on my system:
/media/hda2/drivers/network/addon

I have a Dell Inspiron B130 and it works great :p

---

### Post by bklebel on 2006-03-15
the driver i was using is the bcmwl5.inf, I seen there was a bcmwl5a.inf so im guessing if thats the driver that worked for you it must work for me.  ill give that a try and see what it tells me, thanks!

---

### Post by bklebel on 2006-03-15
do you have a link for the driver from dell, im looking and i cant find bcmwl5a.inf

---

### Post by teeb on 2006-03-15
try:
[http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R115321&SystemID=Inspiron1300/B130&os=WW1&osl=en&deviceid=8911&devlib=0&typecnt=1&vercnt=6&formatcnt=1&fileid=152055](http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R115321&SystemID=Inspiron1300/B130&os=WW1&osl=en&deviceid=8911&devlib=0&typecnt=1&vercnt=6&formatcnt=1&fileid=152055)

hope this helps

---

### Post by bklebel on 2006-03-20
well i gave that driver a try and still no luck.  When i install the driver it comes back tell me: **cp: cannot stat `bcmwl5a.inf': No such file or directory**

this is what i do:
I first remove the old driver - ndiswrapper -e bcmwl5.inf
list the drivers to make sure i removed it - nidwrapper -l
then i install the new driver that I placed on my desktop - ndiswrapper -i bcmwl5a.inf 

it installs the driver but it gives me an error: cp: cannot stat `bcmwl5a.inf': No such file or directory

what am I doing wrong :confused:

---

### Post by teeb on 2006-03-20
bklebel have tried using ndisgtk to install the driver? you can find it in synaptics or
do
sudo apt-get install ndisgtk
I think :-k 

Also is the bcmwl5.sys in the same dir as bcmwl5a.inf.  bcmwl5.sys is really the driver. bcmwl5a.inf points ndiswrapper to it.

terry

---

### Post by bklebel on 2006-03-20
well i finally got the driver to install. but when i reboot my wireless light does not turn on and when I go into admin - networking wlan0 doesn't show up. I did modprob ndiswrapper but nothing.  I justed tried both bcmwl5 and bcmwl5a and neither seemed to work.  im soo lost now :(

---

### Post by teeb on 2006-03-21
bklebel which Ubuntu are you using? I had mine working in breezy and dapper but the steps are a little different.

---

### Post by bklebel on 2006-03-21
im using breezy. you have a dell b130 correct? do you think you could write me up a quick step by step that worked for you or atleast try and help me through the process?  I followed the directions step by step with both bcmwl5 and bcmwl5a and still nothing. aim sn: drklebel

---

### Post by teeb on 2006-03-22
After four or five days of trying this what worked for me.

1.	reboot 
press F2 during the dell boot screen to enter setup.
In setup go to onboard devices and turn the integrated NIC off (I could not get wireless to work until I did this)
go to wireless and make sure Wireless control is not 'off' and wireless devices is 'on'
save setup and continue to boot.

2.	in your desktop (I use gnome so these steps need gnome)
Open ndisgtk - system menu System->Administration->Windows Wireless Driver
if a driver is present select it and press remove driver.
then press Install New Driver
point it to the directory where bcmwl5a.inf and bcmwl5.sys are. select bcmwl5a.inf.
wireless light may flash here.
then press Configure Network this will open Network settings

3.	Hopefully you will have a wireless showing now :) select it.
press configure or Properties and configure your wireless according to your router setting
to get things going set you router's security to WEP the key to hex and enter the key I started out with this key '1234567890' until I had wireless working
click ok and then Activate.


Hope this works for ya.
You can turn your onboard NIC back on now. If you deactivate your wireless and reboot or shutdown the system you will have to redo steps 2 & 3. If the wireless is active when you shutdown or reboot it should come back up.
	
terry

---

### Post by bklebel on 2006-03-22
thank you Teeb, Your instructions seem pretty straight forward. If I understand this correctly, I have to turn my intergrated NIC 'off' and make sure my wireless adapter is turned 'on' (Fn + f2(wirless adapter)) then I can continue to install my driver. 

I am in class now so i dont think I will try and tackle it now but I will tonight and let you know how it goes.  I want to get my wireless to work so I can use the internet in class!!

---

### Post by jml on 2006-03-22
I hate to be the bearer of bad news, but the name of the driver that you are using suggests that you are trying to connect to a wireless card that uses the Broadcom chipset.  Ubuntu 5.10 does not support thisa chipset.  Dapper Drake may.  I recently purchased an HP nx6110 laptop from Spider tools.  This laptop uses the same chipset and drivers.  I asked the vendor to try to install Ubuntu (my preferred distro) on it and configure wireless.  After two weeks of trying, they said that they could not do it.  These are profesional Linux geeks talking.  I gave up and ordered the laptop with Mandriva 2006 installed.  It was delivered and has complete wireless connectivity, including WPA encryption!

The point of this is to suggest that you may want to at least temporarily stop trying to get the built in wireless card to work and follow one of two paths.  Wait until Dapper Drake ships and see if it will work with your card (I sure hope it will,) or buy a PCMCIA card that has the Atheros chipset (like the NetGear WG511T,) and use that.  Hope this helps.

Joe

---

### Post by teeb on 2006-03-23
Don't give up. I'm writing this on my B130 using the Dell 1370 (Broadcom) wireless. It does work! :p 

terry

---

### Post by jml on 2006-03-24
Way to go Terry!!!:p

---

### Post by Family_Guy on 2006-08-08
> **teeb said:**
> try:
[http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R115321&SystemID=Inspiron1300/B130&os=WW1&osl=en&deviceid=8911&devlib=0&typecnt=1&vercnt=6&formatcnt=1&fileid=152055](http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R115321&SystemID=Inspiron1300/B130&os=WW1&osl=en&deviceid=8911&devlib=0&typecnt=1&vercnt=6&formatcnt=1&fileid=152055)

hope this helps

All I found was an exe and when I double click it I get a 'can't open' error.

Edit: nevermind, I forgot to install Wine...

---

