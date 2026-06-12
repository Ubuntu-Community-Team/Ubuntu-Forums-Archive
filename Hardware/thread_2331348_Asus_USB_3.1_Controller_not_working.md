---
title: "Asus USB 3.1 Controller not working"
date: 2016-07-21
forum: Hardware
---

### Post by redking3 on 2016-07-21
Hi, I just bought a Asus PCIe USB 3.1 type-a controller, but I am having some issues with it and I think it might be DOA. Need help figuring that out I am running Ubuntu 16.04 as distro.


If I do the command: "lspci -nn | grep USB", I cant see it at all, and its the same if I just do "lspci -nn". I have not installed any drivers for it or anything like that, but should I not be able to see it anyways with lspci?


I thought maybe it was my motherboards firmware, but I have a working usb 3.1 type-c controller integrated, so 3.1 should already be working fine, or is my logic broken here?

motherboard is "Gigabyte GA-Z170MX-Gaming 5" if that could be relevant


Any ideas? could this be DOA or am I just not doing it right? Thanks!


Thanks!

---

### Post by gordintoronto on 2016-07-21
Try: lsusb

Or:
cd Desktop
sudo lshw -html > config.htm

Then use your browser to peruse config.htm

---

