---
title: "harware question for a new laptop"
date: 2005-12-02
forum: Hardware &amp; Laptops
---

### Post by ger3d on 2005-12-02
Hi all
I'm about to by a new laptop and I would like to check if these hardware spesifications work with Ubuntu/kubuntu

    * Centrino™ ALVISO teknologi
    * Intel®  915GM Express Chipset
    * 15.4" WXGA+ Skjerm 1280x800  
    * Intel® Graphics Media Accelerator 128MB   
    * Intel® Pentium M Sonoma prosessor 
    * 3 x USB 2.0 Porter, 1 x Firewire
    * VGA OUT,
    * Realtek®  ACL250 lydkort IN/OUT  
    * Intel® Pro/Wireless 2915ABG 54Mbit,  
    * Innebygget SD/MMC/Memory Stick kortleser 
    * Gigabit 10/100/1000 Mbit nettverk,
    * TV-Out (S-VHS) , 56K modem
    * Inkl. lader og batteri, Vekt kun 2.9kg
    * 360mm x 265mm x 32.2mm

or that one

# Centrino™ ALVISO teknologi
# Intel®  915PM Express Chipset FSB 533Mhz 
# 15.4" WSXGA+ Skjerm 1680x1050 
# ATI Radeon X600 128Mb Grafikkort  
# 3 x USB 2.0 Porter, 1 x Firewire
# VGA OUT
# Realtek®  ACL250 lydkort IN/OUT  
# Intel® Pro/Wireless 2915ABG 54Mbit,  
# Innebygget SD/MMC/Memory Stick kortleser 
# Gigabit 10/100/1000 Mbit nettverk,
# TV-Tuner innebygget med fjernkontroll(Se TV direkte på din notebook)
# TV-Out (S-VHS) , 56K modem
# 360mm x 265mm x 32.2mm,vekt 2.9kg 

not shure about the TV tuner and I dont need it plus the second costs more

Thanks for you help

Gerhard

---

### Post by RdM on 2005-12-02
See if you can find any of those laptops in the [Wiki]("https://wiki.ubuntu.com/CategoryLaptop"). There you can see general problems and what works for different models.

---

### Post by hw-tph on 2005-12-02
Some general thoughts on the hardware you posted:

[LIST][*]Judging from posts in this forum, the 915 chipset is not easy to get going with 1280x800 resolution.
[*]ATI graphics on laptops running Linux can also be a major obstacle if you're unlucky. nvidia graphics seem to work better on Linux laptops, speaking generally.
[*]The sound and network devices "should" work. They may need some extra attention to get going though.
[*]Built-in SD readers are usually a pain in the behind, needing decrypted firmware in order to work. This firmware is often only available encrypted (the Windows driver decrypts the firmware and uploads it to the device), making it just some extra dead weight to your laptop.
[/LIST]


Håkan

---

