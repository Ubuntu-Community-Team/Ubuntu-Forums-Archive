---
title: "Need help with setting up Brother Printer (HL-L2380DW) via ad-hoc"
date: 2017-04-05
forum: Hardware
---

### Post by igknight on 2017-04-05
Hi all, 
  I am looking for help to set up my Brother Printer (HL-L2380DW) via ad-hoc method (direct connection with no router). I've done this successfully with windows using the MAC address of printer. In order to get the wifi connection established from my laptop directly to printer I had to disable IPV4 and IPV6. I installed the full package from the Brother website for the printer. I think my problem has to do with the device uri. I've tried putting the IP address the printer gave me, multiple different ways with no success. Is there a way to connect with the printer's MAC address like I did in windows or is there a certain way I need to input the IP address the printer gave me? Any help is greatly appreciated (I'd like to ditch Windows for good).

---

### Post by pdc on 2017-04-05
welcome to the Ubuntu forums;

what about going to the PRINTERS box and deleting the entry for your 2380; and using this dialogue

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#Printing_from_Ubuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#Printing_from_Ubuntu)

click on the ADD button and top-left and start again; and see how you go;

by default, Ubuntu doesn't have a firewall set up ..... did you install one?

did you set up a static ip address on the Brother? .... just asking, as a few folks do .......

________

this ubuntu guide on troubleshooting [https://wiki.ubuntu.com/DebuggingPrintingProblems#Network_printer](https://wiki.ubuntu.com/DebuggingPrintingProblems#Network_printer) might be of help?

if you paste this into a terminal, ```
dpkg -l Brother*
```  ....... can you copy and paste back what you get?

---

### Post by igknight on 2017-04-06
Thanks for the reply. I found out what was wrong. I went back to the Network Settings for the direct connection to the printer. I reset it to default, and under IPv4, I changed the setting to local link only. This was the only thing needed to be changed (just left IP address and everything else blank). The printer then popped up when I went to the find option. It now works!
Something so simple, yet I spent hours trying to find. :) (Bye Windows 10, your annoying, forced updates will not be missed.)

---

