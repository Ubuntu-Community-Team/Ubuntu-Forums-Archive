---
title: "DV6253CL Hang on Boot-up after Install"
date: 2008-03-31
forum: Hardware &amp; Laptops
---

### Post by mobilebuntu005 on 2008-03-31
Hi all, sorry for the extremely noobish post, recently develoing an interest in the Linux OS.  I'm fairly knowledgeable when it comes to al things Windows, but pretty much infant to Linux/Unix platforms.  

Anyways, long story short I'm having bootup hang with Ubuntu 7.10 on my Pavillion DV6352CL laptop.  I installed from CD using the "noacpi nolacpi" line added to the kernel parameter, while I have no idea what that did, now that I have it installed, it will hang after the Unbuntu boot up GUI comes up.  I tried after searching through forums by adding "noirqpoll" before splash in kernel parameter, it worked 2/18 boot ups, and now after many more reboots, I didn't get a single success.  

Can anyone help?  Is there something wrong with my kernel parameter something I need to add perhaps, or did I not install correctly.  

The two times i went into X, by looking at System Information it looks like it recongnized all the hardware, same problems others have had, wireless adapter not working and video resolution not available, something about some driver not enabled.

---

### Post by graingert on 2008-03-31
For the hp Pav's you don't need any bootup options.

If you want to see the progress remove quiet and splash from the grub bootup lines

---

### Post by mobilebuntu005 on 2008-03-31
You're right with the quiet/splash part thanks, but still doesn't resolve the problem with the system hang at bootup.  The only error message is at hardware startup when attempting to start the Wireless Card it gives me several errors, but once startup script finishes it hangs into black screen.   

Again like I said, there was actually 2 successful bootups into X and everything looked normal. (But all attempts after that until now still fails) 

Anyone else had this similar problem that knows a way around it?

---

