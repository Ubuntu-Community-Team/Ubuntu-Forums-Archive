---
title: "Ubuntu 12.10 without internet"
date: 2013-02-13
forum: Hardware
---

### Post by c.pfarher on 2013-02-13
Hello, I have a notebook with Ethernet Controller: Atheros AR8161 Gigabit ethernet (rev10), and Realtek Semiconductor co. Ltd. Device 8723 (wireless)
When I boot Ubuntu12.10 64bits from a live usb, it´s doesn´t recognize any of them, and I haven´t internet access and then I cant install boot-repair utility... Are there any image of ubuntu 12.10 that come with the drivers for this cards?
Also I tried to install the packages with a script that I found in internet that download the packages in other pc and then with a usb device I install in the pc without internet,  but I don´t have success because it said: update-initramfs is disabled since runnin on ready-only media....
Thank you!

---

### Post by ManamiVixen on 2013-02-13
You will first have to install Ubuntu before you can fix the devices. The Live CD is a fixed medium and cannot be modified during use. There is also Casper Mode which treats the Live CD like a full install, but I have no clue how as to what would happen if you used the script in Casper Mode. 

Casper, by the way, is a virtual partition that is created on the USB that allows reading and writing to it. Any mod to the Live medium itself will be stored there like updates or software leaving the original ubuntu image copy alone as it is technically counted as a seperate read only partition. 

You can do a Casper install using the Ubuntu Live Disk Creator Utility.

---

### Post by c.pfarher on 2013-02-14
I understand, but my problem is what I do if I can't boot (grub fail) because I have a UEFI machine... and  If I don't have internet to boot live cd and install boot-repair software for solve this inconvenience, I can't repair the grub... do you understand?
Thank You

---

### Post by c.pfarher on 2013-02-17
My target is have internet with ubuntu live cd in order to proceed with the installation in uefi system, because Olfred in [http://ubuntuforums.org/showpost.php?p=12515712&postcount=20](http://ubuntuforums.org/showpost.php?p=12515712&postcount=20) recomended me to have internet when install it.

I post the  abs-network.txt (2.4 KB) with the output of:

lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt

any help?
Thank You!

---

