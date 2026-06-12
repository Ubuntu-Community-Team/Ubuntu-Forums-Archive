---
title: "Problems with wireless network card on sony vaio laptop"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by murtaza on 2008-01-14
I have a Liknsys WPC54G ver3. network card, I managed to install the drivers and get it working two times but the problem is that I can't save the settings untill I boot the computer after.
I have problems when I type the following:
echo ndiswrapper >> /etc/modules

I get Permission Denied or something like that. 

I use the Windows Wireless Drives graphical interface to install the drivers. I just takes me a while to disable eth0 and activate wlan0. I have been following these instrustions to install the LSBCMNDS.inf driver.

1. Run "sudo ndiswrapper -i lsbcmds.inf" and enter your password (or run the ndisgtk program)
2. You will see some messages saying "Forcing parameter RadioState|0 to RadioState|1"
3.Now run "sudo modprobe ndiswrapper"
   and "echo ndiswrapper >> /etc/modules"
4.Now right-click the Network settings on the toolbar, select properties, configure, then deactivate eth0
5. Remove your ethernet card, put in the WPC54G wireless card
6. Run "dmesg" and you should see some messages at the bottom, like "wlan0: ndiswrapper ethernet device 00:0f:aa:bb:cc:dd:ee using driver lsbcmds"
7. I need to run "sed ..." to set Radio... to 0 (as described in the link below)
8. The following assumes you have WEP configured on your router (and if you don't, why not???)
9. The next two steps are optional: run "sudo iwconfig essid somewhere" (where 'somewhere' is the name of your wireless network)
10.now run "iwlist scan wlan0" and you should be able to see your network (and maybe your neighbor's)
11. Once you have the driver loaded and running, the built-in Ubuntu networking settings can do the rest
12. Just open up the Network Settings dialog, then go in to wlan0 and make the appropriate settings
13. Note: the built-in configuration tool only supports WEP at the moment. It is possible to get WPA support with the wpasupplicant package, but configuring that is a whole other story 

I also get problems running dmesg in Terminal. Sometimes it doesn't go through successfully. It worked only twice and I was able to go online.

Can any help me out? Thanks.

---

### Post by murtaza on 2008-01-17
Can anyone help me eith my problem? or there's nothing I can do

---

