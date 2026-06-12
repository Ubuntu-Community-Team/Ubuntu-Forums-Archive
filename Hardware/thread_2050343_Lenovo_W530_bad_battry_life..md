---
title: "Lenovo W530 bad battry life."
date: 2012-08-30
forum: Hardware
---

### Post by musdem on 2012-08-30
I recently bought a laptop for school as I am going off to university in the next couple of days. I removed windows and put Ubuntu 12.04 on in it's place. I've heard about linux having battery issues with laptops before but I have also heard that 12.04 solved a lot of those issues. However with minimal screen brightness its still only has about 2 hours of battery life after a full charge. Are there any programs or config files to change that would extend the life for another 6 hours? Or are there any distros that are laptop friendly?

---

### Post by romjethebear on 2012-09-01
Hi Musdem,
I don't have this laptop yet and i am not using Ubuntu but Linuxmint LMDE instead but I am using Lenovo laptops since 3 years now on Linux and I have big requirements for battery life...
As far as I can say , I would suggest not to use the Optimus Nvidia graphics card and use rather the intel integrated , you may save a lot of power if the many GPus of the NVidia card are off!!!
For any laptop I can recommand to install through synaptic apt-get or any other front  end the laptop-mode tool, which may bring you an easy to save power regarding:
- CPU saving mode
- ethernet
- USB 
- disk power management (you don't have the SSD version isn't it ?)
- brightness settings

I use this tool with my X201 and battery life went from 3hours to 7 hours after tuning the configuration of the tools...
But dealing with the W530 you should defintely switch off the Optimus card , I guess that like all other new cards it's not managed correctly by Linux stuff...

Hope this helps
Jerome

---

### Post by musdem on 2012-09-01
Thanks for the sugestion romjethebear. :)

Though when I have installed it and hoping it will work. Though after looking around and posting on the Lenovo forums I think I may have a bad battery. Do you know if there is a way of testing this? I'd be getting a new battery if it is I would just like to know if all the batteries would be like this or it really is just this one.

---

### Post by Mikeb85 on 2012-09-02
What Kernel are you using?  You need at least 3.4 to fully support the Ivy Bridge chipset...  

Also, either disable the nVidia graphics or get Bumblebee working.  

And which battery did you get?  I have a 9 cell on a T530 (1080p screen) and it lasts 9 hours.  

If you have the standard 6 cell battery and are running default 12.04 with nVidia then 2 hours sounds about right.

---

### Post by musdem on 2012-09-06
No I don't have the new Kernel nor have I disabled the nVidia graphics, I will do both. Oh and I have a 9 cell battery.

Thanks for the ideas. :)

---

### Post by musdem on 2012-09-11
Alright I have figured out that it is indeed the battery that is bad. I have received another battery and it now has 6-7 hours at a full charge.

Thanks for all your help.

---

