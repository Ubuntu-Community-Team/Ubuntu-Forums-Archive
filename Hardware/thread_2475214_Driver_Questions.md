---
title: "Driver Questions"
date: 2022-05-19
forum: Hardware
---

### Post by rusty.hinge on 2022-05-19
Who writes drivers for Linux devices.  The chipset's manufacture?  Linux developers?  New Drivers how are they integrated into the distribution?  If a new driver shows up in an update will my laptop see it or do I look for it from time to time?

Purchased Lenovo IdeaPad 3 15.6" Touchscreen Laptop - AMD Ryzen 7 5825U - 1080p - Windows 11.   Dual boots fine, running Ubuntu now with KDE Desktop.  Except the built in Wifi adapter wasn't found it is a RealTek RTL8852BE.  As I learned from researching on the Windows side.  The camera is also not right with stripes and snow over the image.   Though a very long time Linux user I'm not deep so any guidance will be appreciated.   My workaround is to add a Wifi dongle.

Thank you in advance.

---

### Post by TheFu on 2022-05-19
> **rusty.hinge said:**
> Who writes drivers for Linux devices.  The chipset's manufacture?  Linux developers?  New Drivers how are they integrated into the distribution?  If a new driver shows up in an update will my laptop see it or do I look for it from time to time?
 

Yes. All of them.

New drivers are included in the kernel, so when a new kernel is provided, the new drivers will come with it.

It is possible that some random developer has an itch to make the same device work on their system that you do. Typically, they will fork a very similar device's driver software and tweak some of the code to work well enough. When they are happy, they would post it on github or gitlab (depending on their dislike of certain companies) for the world to use, test, improve.  Sometimes, that's the end of it and people using that device or devices with the same chips will always need to manually grab the code, recompile it locally after each kernel update on their system.  Since more of these people aren't paid, it is a labor of love ... or itch.  They can always take their toys away if they are mistreated.

Different vendors have different stances on Linux support and all have different QA histories.

If you want to run the latest kernel, you can, but it will likely bring other issues to your system. Just depends on your requirement to support any specific bleeding edge hardware.  Some hardware will never gain any Linux support.  I have a fingerprint reader built into a laptop that will never work under Linux. OTOH, fingerprint readers are notorious for terrible security, but I'd still like to have the choice.

---

### Post by #&amp;thj^% on 2022-05-19
> **rusty.hinge said:**
> Who writes drivers for Linux devices.  The chipset's manufacture?  Linux developers?  New Drivers how are they integrated into the distribution?  If a new driver shows up in an update will my laptop see it or do I look for it from time to time?

Purchased Lenovo IdeaPad 3 15.6" Touchscreen Laptop - AMD Ryzen 7 5825U - 1080p - Windows 11.   Dual boots fine, running Ubuntu now with KDE Desktop.  Except the built in Wifi adapter wasn't found it is a RealTek RTL8852BE.  As I learned from researching on the Windows side.  The camera is also not right with stripes and snow over the image.   Though a very long time Linux user I'm not deep so any guidance will be appreciated.   My workaround is to add a Wifi dongle.

Thank you in advance.

I have the same problem with my "Realtek RTL8111/8168/8411" it was working with kernel 5.11 but becomes very unreliable with newer kernels.
As a work-around I put my system in "Suspend" mode and after a few seconds I will wake it to see my WiFi again. :o
I test for Lenovo and they are aware, seems our systems were written for Window's only. (Possibly a Deal was made with MS_)
Devs are working very hard right now to correct things, and I have no ETA for that yet.

---

### Post by TheFu on 2022-05-19
[https://github.com/lwfinger/rtw89](https://github.com/lwfinger/rtw89) looks to be the 'testing' version of that driver. Carefully read the README.md file.

"Realtek RTL8111/8168/8411" is about 20 different chips/versions with different drivers. I've seen multiple versions of the driver over the decades.  Always check the revision of the hardware with realtek.  

After having issues with realtek, I simply avoid them, at least for network stuff.  That worked fine, until Intel put out some 2.5Gbps NIC chips that may now, 2+ yrs later, finally have stable Linux drivers. 

Even last fall, the solution for that with Ubuntu distros was to buy a 1Gbps Intel NIC (there are a few extremely well supported models) and disable their 2.5Gbps chips in the BIOS.  I even bought an older motherboard to avoid getting a 2.5Gbps NIC.

---

### Post by #&amp;thj^% on 2022-05-19
> **TheFu said:**
> 
"Realtek RTL8111/8168/8411" is about 20 different chips/versions with different drivers. I've seen multiple versions of the driver over the decades.  Always check the revision of the hardware with realtek.  


Yep right now I toggle between driver: r8169 and driver: r8168.
This will probably be my last year with Lenovo, the direction they seem to be heading in is not promising as whole for Linux. Some lower end or affordable models will be just fine, but thinkpads, ideapadas and alike will be a hit and miss.:(
EDIT:
```
rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


```

---

### Post by #&amp;thj^% on 2022-05-19
Ok I got all wound around the axle on this one and found a setting I did not like, the fix that worked for me was:
```
sudo tee /etc/modprobe.d/blacklist-ideapad.conf <<< "blacklist ideapad_laptop"


```
lets us know if it did for you as well. (Restart is needed)
```
inxi -N
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169
  Device-2: Intel Wi-Fi 6 AX200 driver: iwlwifi

```

---

### Post by mIk3_08 on 2022-05-20
> **rusty.hinge said:**
> Who writes drivers for Linux devices. 

> **TheFu said:**
>  Typically, they will fork a very similar device's  driver software and tweak some of the code to work well enough. When  they are happy, they would post it on github or gitlab (depending on  their dislike of certain companies) for the world to use, test, improve.   Sometimes, that's the end of it and people using that device or  devices with the same chips will always need to manually grab the code,  recompile it locally after each kernel update on their system.  Since  more of these people aren't paid, it is a labor of love ... or itch.   They can always take their toys away if they are mistreated.


Yes, I definitely agree with TheFu. I experienced this kind of scenario where I grab some code from gitlab and modify it to improve the performance just to make my device work completely. The Love of Linux is Free. No one can take it from you. Thanks TheFu and regards. Cheers.

---

