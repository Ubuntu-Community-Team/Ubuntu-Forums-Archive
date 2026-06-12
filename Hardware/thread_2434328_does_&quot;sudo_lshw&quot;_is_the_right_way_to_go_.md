---
title: "does &quot;sudo lshw&quot; is the right way to go for showing my hardware specs?"
date: 2020-01-03
forum: Hardware
---

### Post by ronjjjg8885 on 2020-01-03
i need it to determine what kind of graphic card will i need for light video editing with Resolve 16

thanks!

---

### Post by Autodave on 2020-01-03
The command will show your specs, but I am not seeing where that is going to tell you what GPU you are going to need.

---

### Post by TheFu on 2020-01-03
There are many different ways to get different HW information.  Sometimes, you just need an overview.  **inxi** is good for that, but it might miss some devices, like a USB network connection.
Sometimes you need HW + drivers + driver versions - **lshw** is good for that.
Sometimes you don't have lshw loaded, so you are stuck with **lsusb** or **lspci**.  Then getting the data you want can be more complex.
Some commands that might be useful:
```
# ###############################################
#      Network Device 
lspci -vk |egrep --after-context=8 'Ethernet|Network'
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 
sudo lsusb -v  |egrep 'Ether|Network'
lsmod |grep usbnet
sudo lshw -C network

# ###############################################
#      GPU Devices   (need diff commands for cameras)
lspci -vk |egrep --after-context=10 VGA
lspci -vk |perl -lne 'print if /VGA/ .. /^[\w]*$/'
sudo lshw -C video

# ###############################################
#      Audio Devices
lspci -vk |egrep --after-context=8 Audio
lspci -vk |perl -lne 'print if /Audio/ .. /^[\w]*$/'
sudo lshw -C multimedia
```

On one of my systems, lshw will lock up when scanning storage. Never figured out why.  Other systems running the same flavor and version of Ubuntu don't have that issue.

When trying to share an overview, **inxi -Fz** isn't too bad.

---

### Post by ronjjjg8885 on 2020-01-04
thanks...

someone told me about "sudo lshw -short"
i will try it later when im on my desktop

---

