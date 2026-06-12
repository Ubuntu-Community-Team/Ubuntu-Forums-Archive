---
title: "Strange network behavior and I need some help.."
date: 2011-11-14
forum: Hardware
---

### Post by utp216 on 2011-11-14
I upgraded the motherboard/processor/ram of my 10.04 system this weekend. This is what I have for my Ubuntu linux box now.

- Kernel version 2.6.32-34-server

- ASRock 890FX Deluxe5 motherboard
- AMD FX 4100 Quad Core processor
- 8 GB RAM (Can't remember make)


This new board has a Realtek RTL-1111E onboard gigabit network device.

Everything works flawlessly except for the network. I see output for it when I "lspci -v", etc. but it won't load a module for it apparently or I am doing something wrong.

Out of desperation I disabled this onboard device and installed a SMC gigabit PCI card that I had in my spares. That card has a Realtek RTL-8169 chip. This card also does not work.

The strange thing (to me that is) is that if I boot the 10.04 LiveCD the network on either of these devices works fine. 

I did some searching and found out about hitting ESC while grub loaded to select the recover kernel. I did that and then used the option to drop to a shell with network. With that the network came up fine.

I am lost. I've spent a ton of time trying to get this working on my own and figured I would ask here. I must have broken something when I was trying to compile and install the network module for the card from Realtek's website.

I would think that if the network worked with the LiveCD it would have worked with the full install. When it didn't I tried to compile the driver from some search results.

Thanks again for any help/tips getting one of these network devices working!

---

### Post by vidtek on 2011-11-14
> **utp216 said:**
> I upgraded the motherboard/processor/ram of my 10.04 system this weekend. This is what I have for my Ubuntu linux box now.

- Kernel version 2.6.32-34-server

- ASRock 890FX Deluxe5 motherboard
- AMD FX 4100 Quad Core processor
- 8 GB RAM (Can't remember make)


This new board has a Realtek RTL-1111E onboard gigabit network device.

Everything works flawlessly except for the network. I see output for it when I "lspci -v", etc. but it won't load a module for it apparently or I am doing something wrong.

Out of desperation I disabled this onboard device and installed a SMC gigabit PCI card that I had in my spares. That card has a Realtek RTL-8169 chip. This card also does not work.

The strange thing (to me that is) is that if I boot the 10.04 LiveCD the network on either of these devices works fine. 

I did some searching and found out about hitting ESC while grub loaded to select the recover kernel. I did that and then used the option to drop to a shell with network. With that the network came up fine.

I am lost. I've spent a ton of time trying to get this working on my own and figured I would ask here. I must have broken something when I was trying to compile and install the network module for the card from Realtek's website.

I would think that if the network worked with the LiveCD it would have worked with the full install. When it didn't I tried to compile the driver from some search results.

Thanks again for any help/tips getting one of these network devices working!

New kernels load the RTL8169 driver instead of the RTL8168.  It's a known bug and hopefully will soon be fixed.

Tony.

---

### Post by utp216 on 2011-11-14
Even if it's a kernel bug how would the LiveCD and the rescue kernel allow the network to work fine? 

Is there a different kernel I need to install to get this working if you know?

I just tested the latest Knoppix LiveCD and that also allowed the network to work fine.

I think I'm taking crazy pills or something!

---

### Post by vidtek on 2011-11-14
> **utp216 said:**
> Even if it's a kernel bug how would the LiveCD and the rescue kernel allow the network to work fine? 

Is there a different kernel I need to install to get this working if you know?

I just tested the latest Knoppix LiveCD and that also allowed the network to work fine.

I think I'm taking crazy pills or something!

Live cd always seems to detect hardware better than a proper install, don't ask me how.  You 'aint any crazier than the rest of us.  It's only the newer kernels that stuffed it up.
I used a spare usb network adapter I had lying around the workshop to assist with the install, then I had to download all the usual kernel source, headers, gcc etc etc etc to get the proper driver to load.  Go to the Realtek site for the linux driver.
Tony.

---

