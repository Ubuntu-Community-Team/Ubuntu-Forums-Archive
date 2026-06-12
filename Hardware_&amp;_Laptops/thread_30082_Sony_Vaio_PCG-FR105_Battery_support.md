---
title: "Sony Vaio PCG-FR105 Battery support"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by MarcelB on 2005-04-27
I installed Kubuntu on my Sony Vaio PCG-FR105 but the indicator sees no battery. If I plug out the adapter KDE shuts down immediatly. I can't work with battery.

---

### Post by dave9191 on 2005-04-27
Try loading up the sonypi module. It handels battery, mem stick, Fn keys, jog wheel. 

sudo modprobe sonypi

KDE has its own deamon to monitor that module once its loaded. So it might sort out the battery problem. I have a sony viao too, but it sees my batt without the need for that module tho. You can also use spicctrl to check battery status, but that wont be much help if kde doesnt see the battery and shuts down.

---

### Post by MarcelB on 2005-04-27
When I type 'sudo modprobe sonypi' nothing happens. Weel of course my pwd is asked, but after that... nothing.
'spicctrl' results in the message command not found.

---

### Post by dave9191 on 2005-04-27
If nothing happens then the module has been loaded, you will only see a message when the module is not found or fails to load. As for spicctrl, you need to install it first. You should be able to get it from the repositories, or you might need to add a few more sources to your list. Alternativily, downlaod the source and compile it from  [here](http://popies.net/sonypi/)

---

### Post by MarcelB on 2005-04-27
okay, I installed spicctrl via Synaptic.

spicctrl -c gives 0 (battery capacity)
spicctrl - r gives 4224 (battery remaining)

Strange, isn't it? No capacity but still remaining.

The KDE battery monitor stiil says 'no battery'. Should I remove that monitor and with wich program I should replace that?

---

### Post by dave9191 on 2005-04-27
Thats not only weird and strange, its also gotted me stumped. My hope was that when the sonypi module was loaded, kde would pick up on the battery for you. I dont know about any replacements that there might be. 

What does it say in control panel > system administration > sony vaio about you battery?

---

### Post by MarcelB on 2005-04-27
Hmmm... it says..

Cannot find the Sony Programmable Interrupt Controller. If this is a Sony Vaio Laptop, make sure the sonypi driver module loads without failures.

And the screen is disabled.
Looks something is not right... so how do I make sure the driver loads without failures?

---

### Post by dave9191 on 2005-04-27
Well there is still hope that once the module loads then your batter stuff will work. As for how to get kde to see the module is a tough one. I used to have that problem, but it just went away and I dont know why (im pretty new to this stuff). You could try to get the module loaded up on start up by adding sonypi to your /etc/modules file. Then restart and see if the control center says that its detected the module.

---

### Post by MarcelB on 2005-04-27
Okay, the module loads now. I get no error message in the control center now and the screen is enabled.
But the battery indicator still sees no battery, which is of course not charging.

---

### Post by dave9191 on 2005-04-28
In that case I'm lost for ideas. Sorry. 

It does work under windows right? Just to make sure its not a hardware issue. And if it does. Then maybe it would work with Gnome?

---

### Post by MarcelB on 2005-04-29
Yes it does work right under Windows.

I downloaded the Ubuntu livecd and that doesn't work either. I hope somebody  has more ideas. At least you poited me out the sonypi driver. Hmmm.. do I have to activate something in the kernel to make it work? And how should I do that?

---

### Post by dave9191 on 2005-04-30
it should just detect your battery anyway, even with out sonypi loaded. Maybe it doesnt detect your computer as a laptop.

---

### Post by MarcelB on 2005-05-01
Hm. And how can I check that?

---

### Post by dave9191 on 2005-05-01
You need to make sure that laptop mode is turning on without failours. And someone else will have to tell you how to do that cause i dont know. Maybe its on the forums.

---

