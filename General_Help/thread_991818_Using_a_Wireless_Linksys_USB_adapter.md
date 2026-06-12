---
title: "Using a Wireless Linksys USB adapter"
date: 2008-11-24
forum: General Help
---

### Post by rmcellig on 2008-11-24
I posted a question about this in the Network and Wireless section but didn't receive a response. I have to get this working today because the customer is picking up his computer with Ubuntu 8.10. He bought a Linksys USB network adapter so he can hook up wirelessly. Will this work in Ubuntu? Is there something I have to do to get this working?

I'm new to all of this, so a clear explanation would be great. Thanks in advance!!!

---

### Post by blazemore on 2008-11-24
I have a Linksys WUSB54GS v2 Wireless USB adaptor. It works flawlessly out of the box in Ubuntu 8.10, but NOT in 8.04.
I think other ones do as well, do you have the actual model number?

---

### Post by rmcellig on 2008-11-24
Yes, it is the Linksys WUSB600N.I am running 8.10. Anything special I need to do to get it working?

---

### Post by blazemore on 2008-11-25
Well you could use ndiswrapper. Unplug the device and reboot first, so the device has "never" been plugged in.
```
sudo apt-get update
sudo apt-get install ndiswrapper -y
```

Download the Windows XP driver for the adapter from the crappy Linksys website.

```
sudo ndiswrapper -i /path/to/driver.inf
```
You have to use the relevant .inf file

```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

Then plug in the device. It should work, if it doesnt work out the box.

---

### Post by rmcellig on 2008-11-25
That seemed to work and was quite painless. What is happening is that from time to time the network drops, and I am always prompted with a window to click on the connect button. Is there any way to have the connection automaticall re-establish without me always having to click on the connect button?

---

