---
title: "RTL8188CU driver"
date: 2012-07-02
forum: Hardware
---

### Post by chesaro on 2012-07-02
Hi there, i'm having a problem with the RTL8188C driver for my enuwi-1x45 usb wireless adapter, it's a realtek chipset and worked very well on lucid lynx (10.04) but after the update of the kernel the driver its just installed on the moment, after a restart the driver isn't there anymore, it works fine but i have to install over and over.

This is the realtek page of the driver:
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=2&PNid=21&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true#2772](http://www.realtek.com/downloads/downloadsView.aspx?Langid=2&PNid=21&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true#2772)

---

### Post by ahallubuntu on 2012-07-02
You probably have to add the module to your module list.  Put the name of the module on a line by itself at the end of this file:

```
sudo gedit /etc/modules
```

What's the name of the module?  I have a similar adapter (not using it at this moment), and it actually uses the 8192cu module.  Do "lsmod" to confirm the actual module name.

Also, you may need to re-build it each time you update the kernel.

---

### Post by chesaro on 2012-07-02
> **ahallubuntu said:**
> You probably have to add the module to your module list.  Put the name of the module on a line by itself at the end of this file:

```
sudo gedit /etc/modules
```

What's the name of the module?  I have a similar adapter (not using it at this moment), and it actually uses the 8192cu module.  Do "lsmod" to confirm the actual module name.

Also, you may need to re-build it each time you update the kernel.

Yeah it's the same module, i'm trying right now, i'll post back if it works
Thanks

---

### Post by kurt18947 on 2012-07-02
> **ahallubuntu said:**
> You probably have to add the module to your module list.  Put the name of the module on a line by itself at the end of this file:

```
sudo gedit /etc/modules
```What's the name of the module?  I have a similar adapter (not using it at this moment), and it actually uses the 8192cu module.  Do "lsmod" to confirm the actual module name.

Also, you may need to re-build it each time you update the kernel.

I've had very good success with RealTek's RTL8188Cus module.  On distros prior to 12.04 I was having to blacklist the 'native' driver.  It was sort of counter-intuitive to blacklist an rtl81* driver (the 'built-in' one) but that's what it took.

---

### Post by chesaro on 2012-07-02
> **ahallubuntu said:**
> You probably have to add the module to your module list.  Put the name of the module on a line by itself at the end of this file:

```
sudo gedit /etc/modules
```

What's the name of the module?  I have a similar adapter (not using it at this moment), and it actually uses the 8192cu module.  Do "lsmod" to confirm the actual module name.

Also, you may need to re-build it each time you update the kernel.

It worked!!! Thanks a lot, see ya
So close and yet so far... :P thanks again

By the way this was on ubuntu 12.04
Kernel Linux 3.2.0-26-generic-pae

---

### Post by ahallubuntu on 2012-07-02
I'm surprised you needed to compile a driver for 12.04.  I haven't installed 12.04 yet (except as a server) but just last night I tried the live CD and my RTL8188 dongle was recognized and supported automatically - I was able to connect to my wireless network easily.  Are you saying after a kernel upgrade you lost this automatic support and had to compile a driver?

---

### Post by chesaro on 2012-07-02
> **ahallubuntu said:**
> I'm surprised you needed to compile a driver for 12.04.  I haven't installed 12.04 yet (except as a server) but just last night I tried the live CD and my RTL8188 dongle was recognized and supported automatically - I was able to connect to my wireless network easily.  Are you saying after a kernel upgrade you lost this automatic support and had to compile a driver?

Nop, since 11.04 ubuntu recognize the wireless adapter but doesn't work properly (the nets are shown but can't connect to any), i was hoping the 12.04 version would work by default yet was the same, don't know what could be happening

---

### Post by jki84 on 2012-08-17
Hi,

I have a similar problem with the OP. I have a quick question regarding the lsmod, when i type in lsmod i get a series of information. which line do i need to look for for the actual mod name? 

Also once i have identified the name do i just insert the name as a new item within the /etc/modules file?

Please advise.

Thank you

---

### Post by jki84 on 2012-08-17
Hi,

to provide further information for the issue i am facing. when select additional drivers from launcher, it lists the rtl usb driver but it also state that: "the Driver is activated but not in use".

Please advise.

Thank you

---

### Post by chesaro on 2012-08-17
> **jki84 said:**
> Hi,

to provide further information for the issue i am facing. when select additional drivers from launcher, it lists the rtl usb driver but it also state that: "the Driver is activated but not in use".

Please advise.

Thank you
It's not a necesary information, its just to confirm de module, if the "RTL8188CU" appears, then its confirmed, if not, then you may have to use/compile other driver.

For the "the Driver is activated but not in use" it covers what i said in the earlies replies, it detects the wireless adapter, but doesn't work properly, it may mean it's installed but its not working with the adapter.

Hope it helps

---

