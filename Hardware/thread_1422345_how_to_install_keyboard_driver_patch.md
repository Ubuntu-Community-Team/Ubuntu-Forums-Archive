---
title: "how to install keyboard driver patch?"
date: 2010-03-05
forum: Hardware
---

### Post by dwl99 on 2010-03-05
I'm a noob running Ubuntu 9.10 and am having difficulty getting my Ortek WKB-2000 wireless keyboard installed. I found a patch [http://patchwork.kernel.org/patch/74366/](http://patchwork.kernel.org/patch/74366/) but have no idea how to install it. Google hasn't helped much either :-(

Can anyone please help?

Thanks

---

### Post by markabey on 2010-03-14
I'm an Ubuntu beginner too and didn't know how to make a specific patch. I managed to get my keyboard to work by upgrading to ubuntu kernel 2.6.34.rc1   

I followed instructions on[ this link]("http://www.ramoonus.nl/2010/02/25/linux-kernel-2-6-33-installation-guide-for-ubuntu-linux/") but used 2.6.34-rc1 instead as it had the patch rolled into it on the changelog     

Kernel files are [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") 



**1.** Download [linux-headers-2.6.34-020634rc1_2.6.34-020634rc1_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc1/linux-headers-2.6.34-020634rc1_2.6.34-020634rc1_all.deb")
   **2. **Download your kernel headers package;       
I386: [linux-headers-2.6.34-020634rc1-generic_2.6.34-020634rc1_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc1/linux-headers-2.6.34-020634rc1-generic_2.6.34-020634rc1_i386.deb")
AMD64: [linux-headers-2.6.34-020634rc1-generic_2.6.34-020634rc1_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc1/linux-headers-2.6.34-020634rc1-generic_2.6.34-020634rc1_amd64.deb")
   **3.** Download your kernel compile;       
I386:  [linux-image-2.6.34-020634rc1-generic_2.6.34-020634rc1_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc1/linux-image-2.6.34-020634rc1-generic_2.6.34-020634rc1_i386.deb")
      AMD64: [linux-image-2.6.34-020634rc1-generic_2.6.34-020634rc1_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc1/linux-image-2.6.34-020634rc1-generic_2.6.34-020634rc1_amd64.deb")
**4. **Install the files in the same order (else it won`t work!)    
**5. **In the terminal run:       sudo update-grub  
   **6. **Reboot and select the kernel from the bootloader menu (mine loaded automatically, check with "uname -r" in a terminal window)

All driver settings such as nivida needed reconfiguring, but the keyboard worked fine


Next step is to get the touchpad multitouch  twofinger scroll working, I can't figure out how to get the synaptics driver to work.

---

### Post by danellisuk on 2011-04-16
Any news getting two finger scrolling to work?

---

