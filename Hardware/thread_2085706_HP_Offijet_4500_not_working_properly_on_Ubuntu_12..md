---
title: "HP Offijet 4500 not working properly on Ubuntu 12.10"
date: 2012-11-18
forum: Hardware
---

### Post by sifel on 2012-11-18
My HP Officejet 4500 is not working properly on Ubuntu 12.10. I have HPLIP installed properly and it even reads the printer. But when I go to print..say a test page, it starts to print then stalls. 

I then get a message that I need to install a plugin. But when I follow the prompts the plugin installation fails.

I would be grateful for any help.

---

### Post by jester- on 2012-11-20
> **sifel said:**
> My HP Officejet 4500 is not working properly on Ubuntu 12.10. I have HPLIP installed properly and it even reads the printer. But when I go to print..say a test page, it starts to print then stalls. 

I then get a message that I need to install a plugin. But when I follow the prompts the plugin installation fails.

I would be grateful for any help.
I'm having the same problem. (worked perfectly on 12.04)
Starting to print hplip-gui would like to download the drivers from hp (camabiata policy driver open not open?) But does not install in the absence of the administrator's permission, I worked around the problem by terminal: sudo hp-plugin, the driver is installed but the printer still does not work.
The printer feature by installing an additional printer (print only) as CUPS printer from [http://localhost:631](http://localhost:631).
Scanner and fax still need to have the printer installed in hplip-gui with hpijs driver.
I would say that, in general, the open not open policy  driver generates  frustrating situations expecially to those who use ubuntu for work and it definitely does not help the spread of operating syatem

---

### Post by cdysthe on 2013-03-02
> **jester- said:**
> I'm having the same problem. (worked perfectly on 12.04)
Starting to print hplip-gui would like to download the drivers from hp (camabiata policy driver open not open?) But does not install in the absence of the administrator's permission, I worked around the problem by terminal: sudo hp-plugin, the driver is installed but the printer still does not work.
The printer feature by installing an additional printer (print only) as CUPS printer from [http://localhost:631](http://localhost:631).
Scanner and fax still need to have the printer installed in hplip-gui with hpijs driver.
I would say that, in general, the open not open policy  driver generates  frustrating situations expecially to those who use ubuntu for work and it definitely does not help the spread of operating syatem

Anyone found a solution to this? What I had to do was install the printer using the Printer installation interface in Ubuntu and then install the printer with hp-toolbox to be able to scan. I have two printers now, one for printing and one for scanning. The latter will not print since I get the error message saying I need a plugin that can't be installed. I really hope someone can figure out what happened to hplip in Ubuntu 12.10 which broke the functionality.

---

