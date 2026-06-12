---
title: "&quot;Input Not Supported&quot; when installing Nvidia proprietary drivers - Ubuntu 22.10"
date: 2023-02-11
forum: Hardware
---

### Post by walkmancut on 2023-02-11
Hi all, I recently purchased a GTX 1080 after my AMD RX570 died. I try to install Linux, and it only seems to work if I do not use the proprietary drivers. Works perfectly fine in windows however. If I use the open source Nvidia drivers, it works perfectly fine. If I plug my PC into a TV, I can see the desktop and use it perfectly fine. Thank you all for reading, I currently have windows installed and also tried to install PopOS, Mint, Kubuntu, etc. All have the same issue. Only windows works or Linux without proprietary drivers.

AMD Ryzen 2300x : CPU
 Acer SA230 : Monitor
 Nvidia GTX1080 : GPU
 MSI A320M Pro M2 V2 : Motherboard

---

### Post by TheFu on 2023-02-11
Any chance that GTX 1080 is fake?  There's a thriving community of online sellers flashing inferior GPUs to show the model in the BIOS that you bought, but it could be an older GPU worth about $50, if that.
The nouveau drivers will work with a wide range of nvidia GPUs because it doesn't support all the extras that newer cards provide.
So, how are you trying to install the proprietary Nvidia drivers?  Hopefully, with 'sudo ubuntu-drivers autoinstall'.  I don't know if 22.10 supports the 'autoinstall' option.  May need to look up the exact driver version and specify that instead. There's a GUI tool for doing this too. I just don't know the name, sorry. Something about "Additional Drivers" would be my search.

Exactly where is the error being shown?

BTW, thanks for posting images as attachments. Could you remove them from the main post to save people who pay for bandwidth by the byte some money?  It isn't like that big black login screen is really useful.

---

### Post by walkmancut on 2023-02-11
Hi, thank you for the reply. Appreciate it. I don't believe the GTX1080 is fake. I bought it locally off a friend of mine, he got it brand new from what he told me. I was trying to install the drivers using the Driver Manager on Ubuntu. I didn't use the command "sudo ubuntu-drivers autoinstall" There is no error shown. It actually works fine. I feel like it may just be my monitor bugging out. I plug it into my TV and it works perfectly. No issues, my monitor? Just says "Input not supported".

Also, I didn't add any attachments. Did something add when I posted it?

---

### Post by TheFu on 2023-02-11
> **walkmancut said:**
> Hi, thank you for the reply. Appreciate it. I don't believe the GTX1080 is fake. I bought it locally off a friend of mine, he got it brand new from what he told me. I was trying to install the drivers using the Driver Manager on Ubuntu. I didn't use the command "sudo ubuntu-drivers autoinstall" There is no error shown. It actually works fine. I feel like it may just be my monitor bugging out. I plug it into my TV and it works perfectly. No issues, my monitor? Just says "Input not supported".

Also, I didn't add any attachments. Did something add when I posted it?

Perhaps I'm confusing posts. Sorry. Just ignore that.  Haven't had any caffeine today.  I need to brew some B'fast tea, I suppose.

Before assuming it is the monitor, try a different cable.  Hopefully, you have DP and HDMI as options. I'd try 1 of the same you are already using and one of the other type the monitor supports.  

Based on buying the GPU from a friend, you're probably fine - not a fake.  Never know where people are finding stuff in these forums. ;)  

OT:
We've had a few people with fake GPUs, Fake SSDs, fake SDHC cards over the last few years.  If a 10TB SSD is $39, isn't that suspicious?  It wasn't to the poster.  [https://arstechnica.com/gadgets/2023/01/64gb-microsd-cards-are-posing-as-16tb-portable-ssds-on-amazon/](https://arstechnica.com/gadgets/2023/01/64gb-microsd-cards-are-posing-as-16tb-portable-ssds-on-amazon/)  They are/were being sold in "market places" Walmart/Amazon/Ebay/Alibaba ... Different sizes from 4TB to 30TB.  After all, they only have a few no-name SDHC cards inside that accept data, but never return it, beyond the last X GB written ... based on the actual size of the SDHC flash storage.

More OT: 
About a year ago, I switched from VGA connections to HDMI in a KVM-switch, but my main monitor doesn't have HDMI inputs, so I needed an HDMI-to-DisplayPort cable/adapter.  That's been working well all this time with the 2nd HDMI going to an HDMI-switch (4x2 matrix) to let me output and record anything to a second monitor from any of 4 input devices.

A few months ago, I swapped a Ryzen 2600 + Nvidia 1030 for a Ryzen 5600G APU and pulled the Nvidia GPU out of the system.  I need to put it into a 3rd box that I'd planned to retire 2 yrs ago, but just can't get the storage/disk array moved to any other systems here with a failing 430GT GPU.  The 1030 would be an upgrade, I suppose.  I barely use the console on that system. It is mainly a storage and backup server accessed over ssh 99.9999% of the time.  Actually, today would be a good day to do that swap. My weekly patching doesn't say that system needs to be rebooted, but both Ryzen systems do need to be rebooted. Hummmm.  I don't like rebooting without a need.

---

### Post by walkmancut on 2023-02-11
No worries. I have seen some weird listings on eBay of fake GPUs HDDs. I even saw a few fake cameras pretending to be a EOS 5D Mk4 for like $30.

 I actually did try multiple HDMI cords, my monitor does not have Display Port. Just HDMI and VGA. Still has the issue that when I go to install Nvidia proprietary drivers. I get that error "Input not supported" on my monitor. It is weird that my TV seems to be perfectly fine with the output from the GPU though. The stock open source drivers do work great though on both monitors. Just not optimized enough for playing games.

---

