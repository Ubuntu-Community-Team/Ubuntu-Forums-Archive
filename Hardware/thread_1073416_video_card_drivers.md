---
title: "video card drivers"
date: 2009-02-18
forum: Hardware
---

### Post by atb-nl on 2009-02-18
hello,

I want to know witch drivers are installed for my video card..
does anyone knows how to do that ?

---

### Post by spd106 on 2009-02-18
Hello,

If you have a card that has a proprietary driver available then you can view your options in System -> Administration -> Hardware Drivers.


Else you might want to open a terminal and run the following command.

```
sudo lshw -class display
```

In this case you don't really have to run with sudo, it just stops an warning message appearing.

---

### Post by atb-nl on 2009-02-19
oke, thanks

i did that and this is what i got back :

user@computer:~$ sudo lshw -class display
[sudo] password for user: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 cap_list
       configuration: latency=0
user@computer:~$ 

i can see its a SiS card :P
but i cant make out of it witch drivers are installed,
the hardware option in the menu lists nothing..

---

### Post by IcarusR on 2009-02-20
I believe this is what you want

```
lsmod | grep sis
```

Should list all modules with sis in the name

---

### Post by atb-nl on 2009-02-21
This is what I got back

```
user@computer:~$ lsmod | grep sis
sis_agp                15232  1 
i2c_sis96x             12420  0 
agpgart                42184  1 sis_agp
i2c_core               31892  1 i2c_sis96x
pata_sis               18436  2 
libata                178208  3 pata_sis,ata_generic,pata_acpi
sis900                 27904  0 
mii                    13440  1 sis900
user@computer:~$ 
```

---

### Post by spd106 on 2009-02-23
I don't have this card, but you could try the steps mentioned in this bug report.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/82940](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/82940)

Good luck

---

