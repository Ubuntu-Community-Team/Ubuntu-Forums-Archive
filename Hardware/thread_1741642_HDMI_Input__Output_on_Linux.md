---
title: "HDMI Input / Output on Linux"
date: 2011-04-28
forum: Hardware
---

### Post by kamacharya on 2011-04-28
Hello Friends

I recently installed Ubuntu 10.10 and will upgrade to 11.04 tonight using update manager.

I have bought SE Arc yesterday and I am using Acer 6930G laptop which has HDMI socket. I was wondering if I can connect my SE Arc HDMI and run the display on my laptop monitor. I have HDMI cable which came with phone. 

Please advise on driver that would detect the hardware cause when I connect simply nothing happens.

Cheers

---

### Post by doas777 on 2011-04-28
> **kamacharya said:**
> Hello Friends

I recently installed Ubuntu 10.10 and will upgrade to 11.04 tonight using update manager.

I have bought SE Arc yesterday and I am using Acer 6930G laptop which has HDMI socket. I was wondering if I can connect my SE Arc HDMI and run the display on my laptop monitor. I have HDMI cable which came with phone. 

Please advise on driver that would detect the hardware cause when I connect simply nothing happens.

Cheers
what kind of video card do you have?
```
sudo lshw -C Display
```

if you go to the Hardware Drivers utility (System -> Administration i believe), do any propriietary drivers show up for your device?

---

### Post by kamacharya on 2011-04-28
Nvidia GeForce 9300m GS 256mb

---

### Post by kamacharya on 2011-04-28
I cant see any optio such as Drivers Utility

But I do have Nvidia X config


I just used the code but dont know what happened

---

### Post by kamacharya on 2011-04-28
weird part is that even SE Arc doesnt detect the laptop. Usually android mobile do respond when connected to hardware.

---

### Post by SeijiSensei on 2011-04-28
Find the "Additional Drivers" application in the system menu.  When you run it, it will detect your NVIDIA card and offer to install the proprietary driver.  Let it do so.  (If you have an nvidia-xconfig, it's possible you've done this already.)

After it's done, and you've rebooted, you'll find a new utility in the menus called NVIDIA X Server Settings.  (If you already installed the proprietary driver, you should have this already.)  You can use it to detect the second screen and choose between them.

---

### Post by kamacharya on 2011-04-28
cheers... I will try this... and get back here how it goes

---

### Post by Hedgehog1 on 2011-04-28
This may be helpful when the time comes: [**_Natty How To: Audio over HDMI for NVidia_**]("http://ubuntuforums.org/showthread.php?t=1741294")

Also - you can load Natty/11.04 and still use the other UI: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")

***The Hedge***

:KS

---

### Post by kamacharya on 2011-04-28
> **doas777 said:**
> what kind of video card do you have?
```
sudo lshw -C Display
```if you go to the Hardware Drivers utility (System -> Administration i believe), do any propriietary drivers show up for your device?

     description: VGA compatible controller
       product: G98 [GeForce 9300M GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0

Unable to install HDMI driver from nvidia website. Getting gedit error as it is unable to detect character encoder.

---

### Post by kamacharya on 2011-04-28
> **Hedgehog1 said:**
> This may be helpful when the time comes: [**_Natty How To: Audio over HDMI for NVidia_**]("http://ubuntuforums.org/showthread.php?t=1741294")

Also - you can load Natty/11.04 and still use the other UI: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")

***The Hedge***

:KS

Do not have nvidia HDMI audio which seems necessary for the steps in above link

---

