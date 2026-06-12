---
title: "HP Pavilion ZV 5000 external display pink and blocky"
date: 2010-02-15
forum: Hardware
---

### Post by KI6ILS on 2010-02-15
Well it was an easy fix. The wrong nvidia driver was installed. I changed it to the nvidia-glx-96 and restarted X and all is well. 
[INDENT]
Sorry if this is already posted but I wasn't able to find any posts regarding this problem. 

I am running Ubuntu 9.10 as a LAMP server and for a while I was using VNC to go in and make changes. I wanted to hook it up to an external keyboard, monitor, and mouse and keep the laptop under the desk. When I plug the external monitor into the VGA port the screen turns pink and oscillates with pixels of purple and there are blocks that are blue, green, or other random colours. The best way to describe it is it is like yanking the cartridge out of an Atari to watch the colors. 

The VGA port is not broken since it worked perfectly when Windows XP was installed on the laptop. I did the Function key to switch between internal and external monitor. I tried adjusting the resolution, frequency, and color depth. I have also tried detect monitors but nothing will bring the external online.[/INDENT]

---

### Post by ogranadino on 2011-05-30
Hello I have same issue in my pavilion dm4, any fix for this external monitor problem?, cos I have same pinky screen.

THanks
Oscar

> **KI6ILS said:**
> Well it was an easy fix. The wrong nvidia driver was installed. I changed it to the nvidia-glx-96 and restarted X and all is well. [INDENT]
Sorry if this is already posted but I wasn't able to find any posts regarding this problem. 

I am running Ubuntu 9.10 as a LAMP server and for a while I was using VNC to go in and make changes. I wanted to hook it up to an external keyboard, monitor, and mouse and keep the laptop under the desk. When I plug the external monitor into the VGA port the screen turns pink and oscillates with pixels of purple and there are blocks that are blue, green, or other random colours. The best way to describe it is it is like yanking the cartridge out of an Atari to watch the colors. 

The VGA port is not broken since it worked perfectly when Windows XP was installed on the laptop. I did the Function key to switch between internal and external monitor. I tried adjusting the resolution, frequency, and color depth. I have also tried detect monitors but nothing will bring the external online.[/INDENT]

---

### Post by KI6ILS on 2011-05-30
> **ogranadino said:**
> Hello I have same issue in my pavilion dm4, any fix for this external monitor problem?, cos I have same pinky screen.

THanks
Oscar

Hi Oscar, 

It was just a matter of installing the correct NVidia driver for my laptop. I logged in through VNC so I could see the display and went to the synaptic package manager and found the NVidia driver for my laptop. After that was installed I ran
sudo dpkg-reconfigure xserver-xorg
then restarted and it was fine

---

### Post by ogranadino on 2011-05-30
Thanks for the response, the problem is that pavilion dm4 has integrated intel video card with intel core i5, so there is no place to download the driver. I`m using ubuntu 11.01. 
Its weird because the max resolution I should have its 1920x1080 with the external screen but when I put turn off the portatil screen to work with the external screen Im getting the pinky screen but when its selected the both screens as mirrors both screens works at 1024x768.... 

Oscar.



*-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:b0000000-b03fffff memory:a0000000-afffffff




> **KI6ILS said:**
> Hi Oscar, 

It was just a matter of installing the correct NVidia driver for my laptop. I logged in through VNC so I could see the display and went to the synaptic package manager and found the NVidia driver for my laptop. After that was installed I ran
sudo dpkg-reconfigure xserver-xorg
then restarted and it was fine

---

