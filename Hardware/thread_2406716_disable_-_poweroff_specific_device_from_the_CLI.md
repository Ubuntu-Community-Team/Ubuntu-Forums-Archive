---
title: "disable - poweroff specific device from the CLI ?"
date: 2018-11-24
forum: Hardware
---

### Post by alex346 on 2018-11-24
Hello,


I am using (not correctly working now) PciExpress GPU passing to VM solution. That was made basing on some websites and forums. The GPU is blacklisted using vfio-pci, and blacklisting amdgpu driver at bootloader.


And I am using tplink powerplug with power meter. 


So, I have discovered that my host power usage is about 80-90W without (physically) installed the GPU, and 120-130W with installed GPU. That is in idle. 


I understand that when I am putting the GPU into the system the power usage even if I don't use it can increase about 10W, but not about 50...




That host works 24/7. It is in remote location. 
GPU - AMD Rx580 is only for Windows VM which are not working correctly ([post here]("https://ubuntuforums.org/showthread.php?t=2406719&p=13818699#post13818699")). 


_**I would like to stop - poweroff as many unused devices as possible, going to green IT :). Of course, when I need more resources I would like to manually start it. Without restarting the host.**_

_**Is that possible? **_
I have readed lot of info on forums about manipulating 


echo 0 > /sys/bus/pci/slots/$NUMBER/power
but that doesn't work for me.


**Why?**
The idea of this post was observation that my GPU when not loaded with kernel (GPU passthrough to VM, VM down) is lightly warm and the fans rotating on low speed. I suppose that rotating is results from the other than temperature (PC case is really huge ). Fans rotating from the very beggining when loading Ubuntu.
What is important here - under Windows host before, when using 2D graphics the fans was long time off and the GPU was warmer than when not using in Linux.








I am also using lot of other PCI and PCI-Ex cards as that MOBO (Asus H97Plus) has even PCI slots.
I have bought it due to largo form-factor (ATX) and PCI slots mentioned above ;)
That is my small lab which I would use to some games in the free time.



Best!

---

### Post by alex346 on 2018-11-28
bump

---

### Post by alex346 on 2018-12-03
bump again

---

