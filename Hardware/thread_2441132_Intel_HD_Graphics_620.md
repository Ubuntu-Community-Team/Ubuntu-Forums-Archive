---
title: "Intel HD Graphics 620"
date: 2020-04-19
forum: Hardware
---

### Post by timtonix on 2020-04-19
Hello everyone!

I decided to migrate from Win 8.1 to Ubuntu.
Tell me with what screen resolutions will the video card driver work on my Asus VM65?

[https://www.asus.com/Mini-PCs/VivoMini-VM65/specifications/](https://www.asus.com/Mini-PCs/VivoMini-VM65/specifications/)
[https://ark.intel.com/content/www/us/en/ark/products/95443/intel-core-i5-7200u-processor-3m-cache-up-to-3-10-ghz.html](https://ark.intel.com/content/www/us/en/ark/products/95443/intel-core-i5-7200u-processor-3m-cache-up-to-3-10-ghz.html)

---

### Post by mörgæs on 2020-04-19
HI, welcome to the fora.

If you do a live boot you can see the resolution for yourself.

---

### Post by CelticWarrior on 2020-04-19
> **timtonix said:**
> Hello everyone!

I decided to migrate from Win 8.1 to Ubuntu.
Tell me with what screen resolutions will the video card driver work on my Asus VM65?

[https://www.asus.com/Mini-PCs/VivoMini-VM65/specifications/](https://www.asus.com/Mini-PCs/VivoMini-VM65/specifications/)
[https://ark.intel.com/content/www/us/en/ark/products/95443/intel-core-i5-7200u-processor-3m-cache-up-to-3-10-ghz.html](https://ark.intel.com/content/www/us/en/ark/products/95443/intel-core-i5-7200u-processor-3m-cache-up-to-3-10-ghz.html)

It should work with exactly the same resolutions as in Windows.

---

### Post by timtonix on 2020-04-19
Unfortunately, I can't see it now because I will buy a 24" monitor next week. Ubuntu inside Virtualbox gives a lot of screen resolution options (I attach a screenshot), but what will happen when Ubuntu will stand directly on the computer?
Now I have 17" and despite the possibility of a monitor, Win 8.1 resolution of more than 1280*1024 60Hz does not give.
Appealed to the support of Intel, said that Intel HD Graphics 620 is supported only by Windows 10.
The driver description for Ubuntu has the characteristics of the supported resolution for Intel HD Graphics 620?

---

### Post by CelticWarrior on 2020-04-19
> **timtonix said:**
> 
The driver description for Ubuntu has the characteristics of the supported resolution for Intel HD Graphics 620?

Again, YES.

And what happens in a VM doesn't matter. In a VM you're using virtualized hardware, not the real one.

---

### Post by timtonix on 2020-04-19
Thanks for the answer!
 I am not an expert, where can I see the description of possible Ubuntu drivers for the Intel HD Graphics 620 video card?

---

### Post by CelticWarrior on 2020-04-19
> **timtonix said:**
> Thanks for the answer!
 I am not an expert, where can I see the description of possible Ubuntu drivers for the Intel HD Graphics 620 video card?

I don't know.
Intel drivers are open-source and installed by default. I never had to install anything, it just works.

---

### Post by Yellow Pasque on 2020-04-20
You can see maximum resolution details on Intel's site. For example: [https://ark.intel.com/content/www/us/en/ark/products/95451/intel-core-i7-7500u-processor-4m-cache-up-to-3-50-ghz.html#tab-blade-1-0-4](https://ark.intel.com/content/www/us/en/ark/products/95451/intel-core-i7-7500u-processor-4m-cache-up-to-3-50-ghz.html#tab-blade-1-0-4)
Again, this is a property of the GPU and not specific to an OS.
Other than that, I'm not sure what you're asking for.

---

### Post by timtonix on 2020-04-20
> **Yellow Pasque said:**
> You can see maximum resolution details on Intel's site. For example: [https://ark.intel.com/content/www/us/en/ark/products/95451/intel-core-i7-7500u-processor-4m-cache-up-to-3-50-ghz.html#tab-blade-1-0-4](https://ark.intel.com/content/www/us/en/ark/products/95451/intel-core-i7-7500u-processor-4m-cache-up-to-3-50-ghz.html#tab-blade-1-0-4)
Again, this is a property of the GPU and not specific to an OS.
Other than that, I'm not sure what you're asking for.


You are right, but only partially.
Official Asus / Intel support response: your video card is only supported by Windows 10.
At the moment I have Win 8.1 gives the maximum screen resolution of 1280*1024 60Hz, the question remains the same:
what screen resolutions will the Ubuntu video card driver give me?

---

### Post by CatKiller on 2020-04-20
> **timtonix said:**
> Official Asus / Intel support response: your video card is only supported by Windows 10.

They are clueless; Intel is a massive contributor to the Linux graphics stack, and their graphics hardware is the best supported. 

The resolutions you'll have available are exactly those that your hardware - GPU and display - are capable of, exactly as you'd expect.

---

### Post by Yellow Pasque on 2020-04-21
> **timtonix said:**
> You are right, but only partially.
Sorry, I didn't account for old versions of Windows. Anyway, your Asus link ( [https://www.asus.com/Mini-PCs/VivoMini-VM65/specifications/](https://www.asus.com/Mini-PCs/VivoMini-VM65/specifications/) ) doesn't list support for Windows 8, so why are you running that on it?

> Official Asus / Intel support response: your video card is only supported by Windows 10.
That contradicts your screenshot where it says "Linux -- Yes". I'm not sure what point you're trying to make here...

> At the moment I have Win 8.1 gives the maximum screen resolution of 1280*1024 60Hz, the question remains the same:
what screen resolutions will the Ubuntu video card driver give me?
Since you don't seem to believe what responders are telling you, then you should do as mörgæs suggested, and boot a LiveUSB to see for yourself. You'll get your answer faster that way and there will be no second guessing.

---

### Post by MartyBuntu on 2020-04-21
Linux drivers are not magic. 
Yellow Pasque is correct on you being hardware-bound by the physical limitations of your devices.

---

