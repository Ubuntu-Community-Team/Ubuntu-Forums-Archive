---
title: "[SOLVED] New user questions"
date: 2008-08-18
forum: General Help
---

### Post by 73ckn797 on 2008-08-18
Greetings,

First, I am not certain into which discussion forum this should be placed.

I am a new Ubuntu user and love the system. 

Currently running 8.04 32 bit on a Toshiba M115-S3094 laptop. Only issue has been the card reader is not recognized or usable. A USB card reader fixes that issue easily. Any other fixes for this?

I run 8.04 32 bit on an AMD 64 bit board with AMD Dual-core 4000+, 2gigs Ram, a 250gb and 160gb HDs with a 40gb drive for back-ups and Windows paging file. Win XP is on the 250 drive and Ubuntu on the 160 drive. I have loaded the 8.04 64 bit but have Java issues using Aurigma image uploader. It simply will not load. I have read other posts of this similar Java applet problem. I ran Synaptic and completely removed all Java installations then changed the order in which I installed the 4 suggested Java versions. No resolution to the problem (this also occurred with the 32 bit version but it worked there). I followed the Firefox 3.0 32 bit installation guide but that failed. I printed out all of the instructions and ran through them several times to no avail. I wiped the drive and re-installed 8.04 32 bit and all works fine.

I would like to load 8.04 64 bit on the XP drive. I know how to do all of that stuff but wonder whether I could have a triple boot system successfully installed. The 8.04 loaders are on the XP drive and I dual boot with no problems. I installed off of the live-CD, not through Windows. Would the additional 64 bit system be written into the loaders automatically ro edited during the install? I know how to edit the XP "boot.ini". I just did not know if the 8.04 32 loader (the wubldr files) should reside on it's own drive or where it is currently at. I am too new to Linux to know much about GRUB or other necessary stuff. My plan is to eventually eliminate XP, keep the 64 bit until I can work out the java issue, and continue using the 8.04 32 bit version. That would be a dual boot system again.

I am looking for a good command reference and/or book to read up on Ubuntu.

Any suggestions or help available?

Thanks in advance.
73CKN797

---

### Post by Pro-reason on 2008-08-18
This looks like an issue for the Wubi forum.

---

### Post by 73ckn797 on 2008-08-18
*"This looks like an issue for the Wubi forum."*

Could someone move this over there?

---

### Post by overdrank on 2008-08-18
Moved to Wubi :)

---

### Post by minhmeoke on 2008-08-19
Welcome to the Ubuntu community!

For the card reader, you could try finding out the manufacturer and model using the "dmesg" or "lspci" commands (use "dmesg | more" or "lspci | more" if you want to step through), then search for third-party drivers.

For java applets in 64-bit ubuntu, I use the "icedtea-gcjwebplugin" package, and it works very well. You should be able to install it in synaptic package manager if you enable the restricted or multiverse repositories in synaptic's settings > repositories.

For the last question, I think that a standard (non-wubi) installation will install the grub bootloader, (only Wubi can use the windows bootloader), but still let you chain-load to the windows bootloader, from which you can select wubi or windows.

As for reference materials, I mostly use the ubuntu wiki ([https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)) and these forums.

---

### Post by 73ckn797 on 2008-08-20
Thanks,

I will try those things. 

I have found, in the 32 bit Ubuntu, that I had to uninstall some Java stuff then reload with a different version to eventually get Aurigma to load. The options given when firefix requested Java were 4 different versions. It was a process of elimination until one would load the image uploader. I found that it required a restart of Firefox each time which makes sense and is not a problem.

From my reading I believe that icedtea may be the latest version that will work in the 64 bit. Is that correct?

The card reader is a minor issue and not on the top of the priority list since using a USB reader does the trick.

---

### Post by 73ckn797 on 2008-08-22
> **minhmeoke said:**
> Welcome to the Ubuntu community!

For java applets in 64-bit ubuntu, I use the "icedtea-gcjwebplugin" package, and it works very well. You should be able to install it in synaptic package manager if you enable the restricted or multiverse repositories in synaptic's settings > repositories.



I have tried all of the Java packages with no success for using the Aurigma Image Uploader.

---

