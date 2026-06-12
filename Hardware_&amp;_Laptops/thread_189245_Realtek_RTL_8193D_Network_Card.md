---
title: "Realtek RTL 8193D Network Card"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by sarangbapat on 2006-06-05
Hi All,
I just installed Breezy on my moderately recent :)  machine. Everything went just fine, installation, boot loader configuration, and I could get ubuntu running. 
The only problem is: I have a relatively cheap Realtek RTL 8139D Ethernet NIC which I am using to connect to my Internet Provider. I know how to configure the network settings using the GNOME Network application. But I dont see the Ethernet Card antry, so looks like that it did not get detected. So now I am unable to browse the internet, and do all the ```
sudo apt get 
``` commands that [this]("http://ubuntuguide.org/") guide suggests. 
Any ideas how to fix this issue?
Thanks,
Sarang

---

### Post by monchichi on 2006-06-05
i know for a fact the realtek 8139 chipset is supported. there are 2 or 3 different kernel drivers for this nic... so maybe the wrong driver is being loaded. paste the following string of commands into a terminal and paste the result back here:

```
sudo lspci | grep 8139;sudo lsmod 8139 | grep 8139;sudo ifconfig
```

---

### Post by sarangbapat on 2006-06-06
Hi,

```
sudo lspci | grep 8139
``` didn't return anything.

I could not copy the output here, since:
1. Ubuntu (Breezy) mounted my windows partition in read-only mode by default. So could not create a text file there. Saving text file on linux partition doesn't help since I cant read it from my windows partition. But as far as I understand there is no driver loaded, and [FONT="Courier New"]ifconfig[/FONT] returned me the local loopback address(127.0.0.1). I didnt have much time to configure ubuntu to mount windows partition in r/w mode, so I am just giving u the result of the first command that you suggested.

Does this help you in identifying the problem?

-Sarang

---

### Post by monchichi on 2006-06-06
if lspci isnt showing the device, something is seriously wrong. try "lspci | grep ethernet." You can load the kernel module with something like "modprobe 8139too"

as far as the windows/linux sharing issue, its a good idea to have a 3rd partition formatted fat32, so you can swap files on a dual boot system.

---

