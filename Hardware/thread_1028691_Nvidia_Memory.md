---
title: "Nvidia Memory"
date: 2009-01-02
forum: Hardware
---

### Post by Martin Marshalek on 2009-01-02
This isn't really a problem, but a bit of a curiosity. I have a Compaq Laptop with a Nvidia GeForce Go 6100 graphics card that came preinstalled with Windows Vista (I now dual-boot). It's one of those that are part of the main motherboard. I recently upgraded my memory and then went into the BIOS to up the RAM devoted to Video from 64MB to 128MB (that's as high as it would go). Now that I have Ubuntu, when I go into the Nvidia X Server Settings window, I am told that I have 512MB of Video RAM. Are my BIOS right or is Ubuntu that awesome that it increases the VRAM on its own?

---

### Post by TheLions on 2009-01-02
> **Martin Marshalek said:**
> This isn't really a problem, but a bit of a curiosity. I have a Compaq Laptop with a Nvidia GeForce Go 6100 graphics card that came preinstalled with Windows Vista (I now dual-boot). It's one of those that are part of the main motherboard. I recently upgraded my memory and then went into the BIOS to up the RAM devoted to Video from 64MB to 128MB (that's as high as it would go). Now that I have Ubuntu, when I go into the Nvidia X Server Settings window, I am told that I have 512MB of Video RAM. Are my BIOS right or is Ubuntu that awesome that it increases the VRAM on its own?

your GPU is probably using shared memory. Maybe you should check in BIOS if is possible to set fixed amount of shared memory.

or maybe in ubuntu it's properly shown amount of memory

---

### Post by 2hot6ft2 on 2009-01-02
> **Martin Marshalek said:**
> I have a Compaq Laptop with a Nvidia GeForce Go 6100 graphics card. when I go into the Nvidia X Server Settings window, I am told that I have 512MB of Video RAM. Are my BIOS right or is Ubuntu that awesome that it increases the VRAM on its own?
My HP G60-125NR has the GeForce Go 5200M and has 512MB RAM on the graphics card so I believe yours has the same. Once it starts running out of room on the cards RAM it starts using some of the systems RAM so what it says in the nvidia-settings is correct for your graphics cards RAM.

---

