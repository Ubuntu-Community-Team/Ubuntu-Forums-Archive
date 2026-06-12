---
title: "Fan Issue"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by wasteoftime on 2007-02-02
Hi i've been told to post here due to a hardware issue i'm experiencing.

I use my laptop to dual boot ubuntu and windows, in windows everything is fine but when i'm booted to ubuntu the cpu fan is in overtime and doesn't stop going. It has to been something in ubuntu but i have no, idea what. 

Please help as i'm afraid that if i continue to run ubuntu it will brake my laptop.

---

### Post by tribaal on 2007-02-02
I'm not sure how the laptop fan management works, but save for the noise level your PC has no risk of breaking if your fan spins too much :)

You might want to install a temperature monitoring applet to ease your mind? If your laptop is ACPI capable, a simple "acpi -t" should show you how hot it's running. I guess your fan isn't managed properly somehow, and so it defaults to full speed, regardless of the actual CPU temperature.

Hope this helps :)

- trib'

---

### Post by wasteoftime on 2007-02-02
Thats a weight off my mind ill try that later im a work now so will get back. 

Just out of interest what is acpi? And what does "acpi -t" do?

Sorry if this is a stupid q but i'm a noob and if you don't ask you don't know! thanks:D

---

### Post by Yoeri on 2007-02-02
Are you sure it is the CPU fan?
I had the same issue with my laptop and in the end it was my video-card fan. I have an ATI Radoen mobility 9700 and my fan problem was solved by installing the proprietary ATI drivers.

Which video-card do you have (laptop-specs)?

---

### Post by wasteoftime on 2007-02-02
Ill get back to you tonight i dont have them with me at the moment.

---

### Post by wasteoftime on 2007-02-02
My laptop is a Fujitsu Siemens AmiloPro V2055 and the onboard  graphics card is

'fujitsu siemens computers VIA/S3G UNICHROME PRO IGP'

Plus i've notice that at boot time linux is picking up a PCI BUG so i assume that has something to do with it.

Please help thanks.

---

