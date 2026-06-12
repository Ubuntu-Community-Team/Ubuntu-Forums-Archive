---
title: "Wireless on HP Pavilion dv4000"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by korona100 on 2005-12-06
I just installed Ubuntu on my dv4000 laptop and the 2nd OS. (XP is the other). I can't seem to get Ubuntu to recognize the Centrino. I can't even turn on the wireless button when booted up in Ubuntu. Anyone ran across this?
Thanks,
Mark

---

### Post by Mikeynewbie on 2005-12-06
I had the same problem with compaq laptop with amd wireless

you need to find out first what company made your wireless for mine it was broadcom which as I have found on Ubunut forums is a pain.  Anyhow if this is the case that you have broadcom or some other manufacturer that does not support linux with a linux driver you need the driver which is an inf file, for broadcom mine was bcmwl5.inf so you get that down loaded and then you have to use ndiswrapper to use the windows driver.  If you have to do this go to the ubuntu wiki home page in the search type in ndiswrapper and then click ndiswrapper set up it should be the second from the bottom link.  There are lots of resources that can be found there as well as on google search searching for manufacturer of wireless device + Ubuntu.

Hope that helps some

---

### Post by Grungy_Hamster on 2006-03-26
I have the same problem. It's quite a frustration.

---

### Post by jml on 2006-03-26
I have a couple of thoughts/suggestions for you.  After Ubuntu is installed, the wireless card, even if is detected is usually not configured or activated.  Go into the Network Manager and see if your wireless card is listed.  If it is, highlight it and click on the properties button.  Configure your cards setting here and close out the dialog box.  After that highlight the card again and click on the activate button.  It may take several minutes for the activation to occur so be patient.  After its done, your card should now be listed as activated.  Close out of the Network Manager and see if you can connect.  If it still does not work, reboot your system ant then check it out.  Another suggestion, setup your connection first as an unencrypted wireless network connection.  Just turn off encryption on the access point you are trying to connect to.  Once that is up and running, then enable encryption.  Hope this helps.

Joe

---

### Post by sequimbob on 2006-08-02
I have a HP Pavilion dv4000 with a PRO/Wireless 2200BG and I cannot get it turned on.  When I run sudo lshw I get the following configuration under network 0 
" *-network:0
                description: Wireless interface
                product: PRO/Wireless 2200BG
                vendor: Intel Corporation
                physical id: 5
                bus info: pci@06:05.0
                logical name: eth0
                version: 05
                serial: 00:15:00:00:27:3b
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.0.6 firmware=ABG:9.0.1.5 (Oct 15 2004) link=no multicast=yes wireless=radio off
                resources: iomemory:b0106000-b0106fff irq:20" 
This tells me the wireless is turned off which is also indicated by the lack of a lit wireless light on the keyboard.  I can not find out how to turn it on under linux.  I run a dual boot system with XP as the alternate.  The Wireless turns on fine with the keyboard switch under XP, but not under linux.  Does anyone know how to turn the wireless radio on under Linux?  I have searced all over but haven't seen an answer to this situation.  All help is appreciated as I am a real newbie to Linux

---

