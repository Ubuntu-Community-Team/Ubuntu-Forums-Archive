---
title: "Brother mfc-L2700DW printer. Kub 16.04,  Driver installed, Won't store &quot;Duplex&quot;"
date: 2017-05-21
forum: Hardware
---

### Post by cackerso on 2017-05-21
I got a new printer, Brother MFC-L2700DW.  I'm running Kubuntu 16.04.  The Brother linux driver seemed to install ok.  But I can only get it to print Duplex by setting it for each document in LibreOffice.  When I try to change the configuration in "System settings - printer" to Duplex the change isn't saved.  I assume there is a script file somewhere that I can't write to because its takes root permissions to write to it.  I am fairly new to Linux.

---

### Post by pdc on 2017-05-22
1) so if you go to your PRINTERS folder; and select the icon for your L2700DW; and right-click on it and select PROPERTIES; what does MAKE & MODEL say please? ......... you may need to drag the window to the right to see all ............

2)> The Brother linux driver seemed to install ok. .........so you didn't have to download anything ..... the computer just set it all up?

---

### Post by cackerso on 2017-05-23
Thanks for the reply.  I was able to solve the problem by going to localhost:631/printers and changing the settings there

---

