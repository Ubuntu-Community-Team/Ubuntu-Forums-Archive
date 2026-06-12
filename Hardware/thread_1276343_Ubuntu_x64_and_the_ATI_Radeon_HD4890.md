---
title: "Ubuntu x64 and the ATI Radeon HD4890"
date: 2009-09-26
forum: Hardware
---

### Post by newtype06 on 2009-09-26
Hello, I have been doing a lot of research lately in hopes of being able to run Ubuntu x64 with my Radeon HD4890.
From what I have seen, people have been able to install the proprietary drivers on an x86 machine with no problems.
Any time I have tried, I get a very buggy interface with a whole lot of lag. I love Ubuntu, and it would make my day if someone could clear this up. 
Is there anything special I have to do to get this card working?
Also, I do have 8gb of ram, so I have a practical purpose for wanting to use x64.
I have also seen one or two threads saying that AMD GFX are simply not supported, a little clarity would be great.

Thanks ahead of time.

System build : AMD Phenom X4 2.66ghz Black Edition
8gb of 1066 G.Skill Ram
Sapphire Radeon HD4890

---

### Post by sideaway on 2009-09-27
Hi there, I'm running a 4870 on 32b crunchbang. However have run x64 previously, and installing drivers is as easy as enabling fglrx in Hardware under accessories.

Reports for AMD/ATi driver issues is largely related to the fact the latest fglrx drivers have dropped support for older models, x1**0 series and earlier have been dropped, and are being forced to use the less efficient and desirable open source driver - radeonhd.

---

### Post by newtype06 on 2009-09-27
Hello, I appreciate the quick response.
I have already attempted to activate the driver in the restricted drivers tab. I can't seem to get it to properly activate, thought it does show it as being there. This is the same problem I have been running into for a little while.
Again, thanks.

---

### Post by newtype06 on 2009-09-27
I found a way to get things working perfect. I had to go into synaptics and completely uninstall anything that had to do with my Ati drivers. I than went to ATI.com and downloaded there driver and installed. Even GPU scaling works!! My suggestion to anyone that has this card is to _**NOT DOWNLOAD UBUNTU'S RESTRICTED DRIVER**_ for this, this presents the problem of lag and the "unsupported hardware" symbol in the bottom right of the screen.
If anyone has any questions for me, feel free to send me a message.

---

### Post by markbuntu on 2009-09-28
The driver in the Jaunty repo, ie the one you get with hardware manager does not support the 4890 and a bunch of other newer cards because the driver, 9.4, came out before that card was released. Anyone who gets the "unsupported hardware" symbol should remove the driver and get the latest one from the ati site and install that.

---

### Post by newtype06 on 2009-09-29
Don't mean to be a jerk, but I just said that.

---

### Post by oluenxypvk3573 on 2009-09-29
attempted to activate the driver in the restricted drivers tab

---

