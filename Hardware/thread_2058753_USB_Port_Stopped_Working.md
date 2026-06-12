---
title: "USB Port Stopped Working"
date: 2012-09-16
forum: Hardware
---

### Post by Shadius on 2012-09-16
Hey everybody! :)

It seems that one of my USB ports stopped working. Is there a way that I can check for sure?

---

### Post by cwsnyder on 2012-09-16
Plug something into that port, go to the terminal and type: ```
$ lsusb
```If the item is listed, the port is working.  Your computer could also think the port is 'tied up' if you plugged something in and didn't properly unmount the device prior to removing the device.

---

### Post by Shadius on 2012-09-16
> **cwsnyder said:**
> Plug something into that port, go to the terminal and type: ```
$ lsusb
```If the item is listed, the port is working.  Your computer could also think the port is 'tied up' if you plugged something in and didn't properly unmount the device prior to removing the device.

It's not showing up, but it is showing up on the other USB ports.

---

### Post by Shadius on 2012-09-16
I don't get it. It was working just a few minutes ago. My USB receiver for my keyboard was plugged into it then I had to use the other computer (Compaq) so I plugged in the USB receiver into that one (Compaq) and it worked. Now when I plugged back the USB reciever into it (ASUS) that port doesn't work. All the other ports work except this one now. I don't get it!

---

### Post by acefromspace on 2012-09-16
Is the port on front of computer? Sometimes they are not reliable (bad wiring?) I always use rear ports or would consider rewiring front ports myself.

---

### Post by Shadius on 2012-09-16
> **acefromspace said:**
> Is the port on front of computer? Sometimes they are not reliable (bad wiring?) I always use rear ports or would consider rewiring front ports myself.

Yeah, the port is on the case. The case has 4 USB ports, two or which are 3.0. One of the 2.0 ports just stopped working. How could this one port just stop working just like this? I really don't understand this. 

I plugged in my WD Elements external HDD and it seems to be supplying power to the HDD because the blue light is lighting up when the USB wire is plugged into the port, but that's it! 

I wonder if reinstalling Ubunut would fix it? Did I somehow lock up the port?

---

### Post by Shadius on 2012-09-16
So I plugged in my phone via the USB port and it's charging the phone. I plugged in a Flash drive and the light on the Flash drive lit up. So the USB port has power, but for some reason it's not working as it should.

---

### Post by Shadius on 2012-09-17
Any ideas?

---

### Post by SlugSlug on 2012-09-17
have you powered down / back up?

---

### Post by Shadius on 2012-09-17
> **SlugSlug said:**
> have you powered down / back up?

Yupp, tried that. I'm at my wits end. >_<

---

### Post by cwsnyder on 2012-09-22
There are 4 wires to the USB port, 2 power and 2 data.  If you can't get data to transfer, check first to see that none of the little contacts are broken.  If you can't see anything, there may be wires broken in the connector cable on that port.

---

### Post by cwsnyder on 2012-09-23
Another thought, you may have pulled a connector loose on the back of that port, if it is a front panel USB connector.

---

