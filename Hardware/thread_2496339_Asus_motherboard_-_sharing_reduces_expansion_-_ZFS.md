---
title: "Asus motherboard - sharing reduces expansion - ZFS involved"
date: 2024-03-24
forum: Hardware
---

### Post by aljames2 on 2024-03-24
I should have researched the MB a little closer. Trying to figure out how to get more storage connections.

I have the Asus Rog Strix B550-A Gaming motherboard.  The CPU is Ryzen 5600x (no onboard video)
[https://www.asus.com/us/supportonly/rog%20strix%20b550-a%20gaming/helpdesk_manual/](https://www.asus.com/us/supportonly/rog%20strix%20b550-a%20gaming/helpdesk_manual/)

It has 1 video card slot PCIe 4.0 x16.  I have to use a video card due to the CPU I chose. This means I can't use the Asus hyper m.2 expansion card in there, which otherwise would be an option.

It has 1 other PCIe x16 slot that runs in x4 mode, and it is being used by a 4 port Intel NIC that has to run in at least x4 mode. This also, disables the other 3 PCIe x1 slots so they can't be used for a SATA expansion card.

I have 6 SATA connections max, but I lose 2 of them if I use the 2nd m.2 connection on the motherboard, which I do have both of my m.2 slots occupied, so this reduces my SATA connections to only 4.

I had thought about pulling one of the m.2 NVMe and inserting an m.2 to SATA expansion card in it's place but the m.2 currently is the zfs mirror of my primary m.2 card which has some storage pools on it.

I have 2 HDDs I wanted to add to it for some media serving. Nice MB but not much room to expand storage given what I'm throwing at it.

Lesson learned when shopping for MBs, read the manual first, don't just look at the pictures :)

---

### Post by MAFoElffen on 2024-03-24
Dang. 

Yes. Honestly... That is why I didn't go which ASUS on my workstation. I went with MSI. (MSI MPG Z790 WiFi) ASUS does some strange things on their ports and slots.

So which slots and ports are left active now?

---

### Post by him610 on 2024-03-24
Just a thought...
If you were to exchange the 5600X for a 5600G you would not need the video GFX card. 
I recently upgraded to a 5600G for about $120.

---

### Post by aljames2 on 2024-03-24
yeah, now I have 1 onboard SATA connector left to use. I've only used 3 SATA + the 2 m.2's.  
Because I am using that 2nd m.2 port I can only use 4 of the 6 SATA ports.  
I'll have to think about what to do next, pull out some more cash I suppose, LOL
BTW, nice mobo you got there MAFoElffen !!

---

### Post by aljames2 on 2024-03-24
> **him610 said:**
> Just a thought...
If you were to exchange the 5600X for a 5600G you would not need the video GFX card. 
I recently upgraded to a 5600G for about $120.

Ahh, good point, I hadn't thought of that !!

---

### Post by MAFoElffen on 2024-03-24
> **aljames2 said:**
> 
BTW, nice mobo you got there MAFoElffen !!

Thank you. I did my research and shopped around. (A whole lot.)

Bifurcation would have added another $200, but is still in it's infancy. I can wait until they work those problems out, and gets past the growing pains.

Both ASUS and Gigabyte didn't pass my scrutiny for what I was looking for, and make some strange choices when you start plugging in things for upgrades. A lot of that was with devices in other places dropping out if you added this in that slot... Or bus speeds that dropped drastically when you used certain devices in certain slots.

It was mind boggling going through all the user manuals to make sense of what they were doing... I didn't want to later regret what I had bought.

The one thing I should have done, is waited a bit longer on maxing out my RAM. I added 4x32GB DDR5 sticks. Later MSI found out that board will work with 64GB Sticks. Dang. LOL. Oh well.

---

### Post by TheFu on 2024-03-25
I have 2 Asus B450 MBs with the same m.2 vs 6 SATA ports issue.  I got the 2nd one with that full knowledge. Both have 5600G CPUs.  

One has an addon PCIe 4-port eSATA/SATA card with Marvel 9215 chips. Only 2 ports can be use at a time. They claim the connection is SATA-3 (6.0 Gb/s), but wish I'd have spent more and gotten an _LSI 2-port SAS HBA_  - that would support 8 SATA HDDs by using $13 SAS-to-SATA cables.  The cheap PCIe SATA card is slow. The system also has a 4-port Intel GigE 82575GB NIC inside.

---

### Post by aljames2 on 2024-03-25
> **TheFu said:**
> …wish I'd have spent more and gotten an _LSI 2-port SAS HBA_  - that would support 8 SATA HDDs by using $13 SAS-to-SATA cables.  The cheap PCIe SATA card is slow. The system also has a 4-port Intel GigE 82575GB NIC inside.

Thanks TheFu !  I think this is what I am going to do for now.  I’ll need to get a 5600g or 5700g since those prices have dropped quite a bit, that will free up the primary PCIe x16 slot that I can use for an expansion card.

I normally reinstall my root OS when I replace a motherboard and CPU.  Now though, since I can drop in a CPU, do you think it would be wise to do a fresh install of my host OS after doing this swapping out the CPU?  Well, and I guess I’ll be removing an Nvidia video card and putting an expansion card in its place.  So more than one moving part here.

---

### Post by MAFoElffen on 2024-03-26
Complete Reinstall? Maybe not...

If you removed your NVidia drivers... Changing the CPU in the board, the opensource amdgpu drivers should kick in. If not just a few boot parameters will force them.

On ZFS-On-Root, with the notes we shared for your install, you used Unique Drive IDs, so the pools should come up fine with them, when the system init's and finds those. (That is why we don't use device names that can change over boots.) 

The only thing I can think of it the boot sequence and Grub might change with the drives attached to the HBA card, instead of through the MB. So dealing with that would be to change the boot order in the BIOS, and maybe having to mount and chroot into it to change that.

Nothing major. You are used to that by now.

Good call by TheFu...

I've found some good used LSI SAS controllers on EBay for a good deal. You can't really go wrong with "LSI". LSI controllers have been the industry standard for decades. I like that they have their own flash-able BIOS for setup, that their firmware can be updated without too much troubles.

In the past I found a few GUI utils for them for RedHat... And converted them from rpm to deb packages and used them on my management consoles. I know, I was bored and looking for a challenge. Still not as useful as command line and the API's.

EDIT: Afterthought... The MachineID will be the same, but not sure with a new CPU, if ZFS is going to see it as the same unique 'system' that it was tied to. If not- You might have to export and import the pools to refresh that.

If you do end up doing a complete reinstall, search my posts on some work-arounds for updates to the bpool creation options... There was a bug on some machines with bpool, Grub2 & snapshots of bpool. Changing the bpool creation options fixes that.

---

### Post by aljames2 on 2024-03-26
Alrighty, I just ordered a replacement CPU & SAS controller card & cables. I won't need to move my root SSDs (2) or NVMe's (2) which is where all the zfs stuff is.
I'll need to remove the nvidia drivers, the reboot without those, then shutdown & pull the nvidia card & swap out the CPU and try to boot.
Thanks for the afterthought MAFoElffen, because I think changing the cpu will be where problems happen, if any.
I'll post back with an update soon.  Thanks everyone !

BTW, here's the SAS card I got, some of these come with RAID controllers which I didn't want, so hopefully this one will be all that I need.
[https://www.amazon.com/gp/product/B008J49G9A/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B008J49G9A/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1)

---

### Post by Yellow Pasque on 2024-03-27
> **MAFoElffen said:**
> Yes. Honestly... That is why I didn't go which ASUS on my workstation. I went with MSI.

My MSI B550 board also has some PCI-e slot and/or lane width limitations when using the second M.2 slot. I know Asrock does the SATA 5/6 and M.2 sharing on at least one of their B550 boards. The bottom line is that the mobo chipset only has so much connectivity and so many PCI-e lanes. So the manufacturer can give you some flexibility or they could just give you less slots or SATA ports. In general, I'd rather give up a couple SATA ports than lose a PCI-e slot or have it running at reduced speed.

---

### Post by aljames2 on 2024-04-07
All done.  I uninstalled the Nvidia driver and pulled the card & replaced the CPU with the 5700g. Upon startup, I went into the Bios to check everything and I did have to put back my original settings which seemed to all be reset with the new CPU. The boot device and all other drives remained unchanged thanks to the original root on ZFS install using descriptive device names.  The only things I had to adjust after first bootup were my network interface names in my netplan config file, they were all given new names by the system. The SAS card is running with a few new drives now installed, plenty of room to grow now, and for less money and trouble. Now I have a 5600x left-over to get rid of. :)

---

