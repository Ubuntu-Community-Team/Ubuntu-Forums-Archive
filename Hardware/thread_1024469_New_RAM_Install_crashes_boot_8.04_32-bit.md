---
title: "New RAM Install crashes boot 8.04 32-bit"
date: 2008-12-29
forum: Hardware
---

### Post by AeroTITAN on 2008-12-29
I am trying to install 2, 1GB PC3200 184 pin memory in a 32-bit system. They type (PC3200), the pin number (184), voltage, etc. are all compatible with my hardware.

I have recently (a week ago) updated to 8.04 LTS from 7.10.

So I installed the memory and booted up. Ubuntu boots into a loop where it reaches the screen where the boot status shows you the progress, it will get to about a third of the way through and then reboots. If it's relevant the computer beeps when it does this.

My system is dual boot with XP Service Pack 2. Windows boots just fine.

Last week I also installed a new graphics card: Nvidia 8400 gs (PCI, not PCI-Express). That was a pain to get working, where I actually had to update to 8.04 to get the graphics card to work. Again Windows booted fine here too. Eventually both XP and Ubuntu worked after that, but Ubuntu seemed to work slower after than (I must have to optimize that somehow).

So here's what I've tried:
1) These commands:
sudo apt-get install linux-restricted-modules-server

sudo apt-get install linux-headers-server

sudo apt-get install linux-image-server linux-server

2) Removed new memory and added old. Ubuntu and Windows boots just fine which would make you think the memory could be bad, except Windows boots just fine with the new Memory.

3) Switched around placement of memory in different modules. No joy there. And again Windows boots fine.

4) I was once to enter the Recovery Mode (although now it crashes) where I typed in the command: $ free
The output showed all of the memory including the new memory as present.

5) The BIOS shows all the memory present. I saw a post regarding an "optimization" setting and I don't have one.

6) Currently trying to run the 8.04 32-Bit LiveCD. It seems to freeze at the same place in the loading bar as the HDD.

Sorry for the repeat post; can't figure out how to delete last one

I appreciate any help you can offer.

Thanks

---

### Post by igknighted on 2008-12-29
Did you try booting the mem-test option in grub?  It wouldn't be the first time one OS glitched on faulty hardware while another worked (can go either way).

---

### Post by AeroTITAN on 2008-12-29
Thanks for responding.  I ran the mem tester and no errors showed up.

I have now got the memory to work fine and even added the original 512 MB in as well.  I removed the new graphics card and tried both booting as well as the LiveCD.

So I don't understand why my system (both Windows and Ubuntu) could work all week and then the new memory disrupt the graphics card.

Any ideas?

---

### Post by impact on 2008-12-29
I would try the latest Ubuntu version (8.10) with the latest NVIDIA driver. I have experienced random crashes after adding memory which were probably related to an older version of kernel or NVIDIA driver. It is just a guess but the system probably wasn't allocating the memory properly (it was a laptop so BIOS options were pretty much non-existant) and the kernel or the graphics card driver wasn't able to deal with it.

---

### Post by AeroTITAN on 2008-12-29
It is definitely not the memory.  I am now trying to load the 8.10 LiveCD to install and the LiveCD won't boot.  It stops around the third square.

How do you install Intrepid on a system using a restricted driver?

---

