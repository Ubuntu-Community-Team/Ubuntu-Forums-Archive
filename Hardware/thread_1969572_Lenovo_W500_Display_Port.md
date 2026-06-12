---
title: "Lenovo W500 Display Port"
date: 2012-04-30
forum: Hardware
---

### Post by smuthavarapu on 2012-04-30
Hi All,

I have got Lenovo w500 with Ubuntu 12.04 64bit.

Recently I got a Display Port Adapter to HDMI to connect to TV.

But, Ubuntu is not detecting the DP1 port and in Displays I am not seeing the second monitor.

Can you guys please help to me get this working

---

### Post by smuthavarapu on 2012-05-01
After thourgh search in the internet, Thanks to this post : 

[http://forums.linuxmint.com/viewtopic.php?f=49&t=59601](http://forums.linuxmint.com/viewtopic.php?f=49&t=59601)

> In short, for anyone viewing this thread in the future (and indeed this  may likely be applicable to all laptops with dual "dynamic" switchable  GPUs):

On the Thinkpad W500 there is a BIOS option for either  "discrete", "integrated" or "switchable"... by default my laptop was  configured to "switchable" however this feature has only been  implemented in Windows 7 (at least thus far Linux has no means of  switching GPUs at runtime) it defaults to the "integrated" (in my case  the Intel GMA MHD4500 controller) GPU and hence when I installed the ATI  drivers (and restarted) I no longer had the correct drivers installed  for the default integrated GPU. 

The solution was to boot into the BIOS and manually change the selected GPU to "discrete". Now I have got the TV displaying the screen in 1920X1080.   

But the Problem continues.... Now I have issue with Sound, I need to look how can i enable the Audio through this Display Port.

Any suggessions from any one....

---

### Post by smuthavarapu on 2012-05-09
Its been confirmed that W500 mother board does not support Audio through DPort.

So, I have ended up using Auxillary Cable from Laptop to TV.

---

