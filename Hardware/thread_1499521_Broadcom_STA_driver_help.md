---
title: "Broadcom STA driver help"
date: 2010-06-02
forum: Hardware
---

### Post by Brn6267 on 2010-06-02
Ok, I'm on a dell 1525, and ubuntu doesn't detect my wireless card, so i downloaded the Broadcom STA driver. Everything runs fine until i enter the command make in the terminal and it sends back the following error:
 
Relocatable linking with relocations from format elf32-i386 (/home/brendan/hybrid_wl/wl.o) to format elf64-x86-64 is is not supported. 

I've scoured the forums but have not seen any help regarding this particular error. The other problem is that i don't have a LAN connection to use, i have to switch over to the Windows partition to get internet access.

---

### Post by Brn6267 on 2010-06-02
Can somebody help me please???

---

### Post by ridz on 2010-06-02
You probably dont have the 'make' program installed - this is part of the software development package. I assume that you are trying to build the Broadcom driver from the source & is probably why you are using 'make'. I am not familiar with that Dell model and building the driver from source, but I have had experience in getting the Broadcom STA driver to work on a netbook and several notebooks with Ubuntu. For a detailed look on what I did, refer to [http://ridz1ba.blogspot.com/2009/11/howto-install-ubuntu-netbook-remix-910.html](http://ridz1ba.blogspot.com/2009/11/howto-install-ubuntu-netbook-remix-910.html) - this would give you some pointers on getting the STA driver to work on Ubuntu (Karmic in my case but will also apply to Lucid).

Hope this helps.

---

### Post by Sepero on 2010-06-18
I solved this problem for a friend in a slightly different way. I hope this helps.


1. Add the LiveCD as a repository and Uncheck ALL other repositories.
System> Administration> Software Sources

2. Update software sources. This can be done when you close the Software Sources window, or by using Synaptic.
System> Administration> Synaptic Package Manager> Reload (button)

3. Use Synaptic to Remove bad packages if they are installed.
System> Administration> Synaptic Package Manager> Search (button)
* bcmwl-kernel-source
* b43-fwcutter
* linux-image-2.6.32-22-generic (any linux-image 2.6.32-22 or greater)

4. Use Synaptic to Lock the kernel package linux-image-2.6.32-21-generic, and lock the package linux-headers-generic to version 2.6.32-21.32. (This will prevent the problem from occurring again with future upgrades).
System> Administration> Synaptic Package Manager> Package (menu)> Lock Version

5. Reboot (restart)

6. Install the wifi driver.
System> Administration> Hardware Drivers

7. Reboot (restart)

8. Remove the LiveCD as a repository, and Recheck all the repositories that were unchecked in step #1.
System> Administration> Software Sources

---

