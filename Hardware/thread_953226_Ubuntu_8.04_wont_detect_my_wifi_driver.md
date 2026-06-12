---
title: "Ubuntu 8.04 wont detect my wifi driver"
date: 2008-10-19
forum: Hardware
---

### Post by jordanae on 2008-10-19
For some reason my laptop won't connect to the internet anymore. First, I booted up my computer and tried to get onto the internet. Nope, won;t work. And so I go to System> Administration> Network and saw that there was no wireless connection menu.

In my last desperate attempt before the forums I checked my hardware drivers. It says the only driver I have is my NVIDIA graphics card is all I have. Nothing about my wireless driver.

And also, it wont connect to a local connection.

Please help!

---

### Post by Bucky Ball on 2008-10-19
Have you tried hardwire ethernet cable?
Open a terminal and paste or type this:

**lspci**

See if you can find your wireless card in there. Could you also supply the exact model of your machine. :)

---

### Post by jordanae on 2008-10-19
I'm not so sure on the specs, but the model is an HP Pavilion dv6000.
By the way, I didn't get anything that looked like a wireless card when I typed in lspci into Terminal.

---

### Post by Bucky Ball on 2008-10-20
You have virtually the same machine as myself I suspect. 

Go to Systems->Admin->Hardware Drivers

Is there anything in there, the Broadcom B43 Driver by any chance? Can you get a cable connection so you can download updates and ubuntu-restricted-extras? You can find the latter in Synaptics Package Manager or by pasting or typing:

**sudo apt-get install ubuntu-restricted-extras**

in a terminal. 

You are looking for something that mentions Broadcom in the result of **lspci** in the terminal. Here's mine:

```
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

It will be somewhere near the bottom probably.

---

### Post by jordanae on 2008-10-20
> **Bucky Ball said:**
> You have virtually the same machine as myself I suspect. 

Go to Systems->Admin->Hardware Drivers

Is there anything in there, the Broadcom B43 Driver by any chance? Can you get a cable connection so you can download updates and ubuntu-restricted-extras? You can find the latter in Synaptics Package Manager or by pasting or typing:

**sudo apt-get install ubuntu-restricted-extras**

in a terminal. 

You are looking for something that mentions Broadcom in the result of **lspci** in the terminal. Here's mine:

```
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

It will be somewhere near the bottom probably.

That's the problem. I cannot find any of that. Up until last night it's all been there and now it's all gone. It's like my NIC doesn't even exist.

---

### Post by Bucky Ball on 2008-10-20
Just the NIC? Nothing else? Everything is as normal just no wireless card appearing anywhere?

Wondering if it may have died, but then, it might possibly still show up even though inoperable. I would have thought the machine would have made more of a song and dance about a hardware problem like that.

---

### Post by jordanae on 2008-10-22
Everything's the same. The only problem is connecting to the internet. Not even connecting through ethernet works. I'm afraid my NIC is fried :/

---

