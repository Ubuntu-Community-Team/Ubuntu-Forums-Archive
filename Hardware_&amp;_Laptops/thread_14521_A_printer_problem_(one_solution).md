---
title: "A printer problem (one solution)"
date: 2005-02-08
forum: Hardware &amp; Laptops
---

### Post by taffy on 2005-02-08
I hope this may help people experiencing the same printer configuration problem I had.

When I first installed Ubuntu everything worked fine until I installed the NVIDIA graphics driver. After rebooting I couldn't get the printer configuration program to recognize the printer automatically or manually. After consulting all the forums here at the Ubuntu site I experienced several small levels of success at different times. However all the various attempts fell short, and I was convinced the problem was a security one until I found this advice at:

[http://channels.lockergnome.com/linux/archives/20020709_kernel_configuration_part_ix.phtml](http://channels.lockergnome.com/linux/archives/20020709_kernel_configuration_part_ix.phtml) 

I've cut the relevant part out to include here:

Be aware - this kernel configuration option only makes a driver available for the parallel port. The computer’s BIOS sets the mode for the port - ECP, EPP, or
Auto. On the majority of modern computers, the Auto mode is the default and will
work just fine. However, if you have problems communicating with your printer following a kernel recompile, try changing the mode of your printer in the BIOS.

I rebooted, changed the setting of my parallel port in the BIOS and after logging in and running Menu/Computer/System Configuration/ printing my printer was detected automatically. :smile: 

I'm really glad because I was almost about to re-install Fedora 2 or 3.

Hope this helps one person at least,
taffy

---

### Post by y6FgBn)~v on 2005-02-10
Thank you Taffy, it did help me  :-) 

I could not figure out why my printer would not print <HP Deskjet 500> even though it was detected. Did a search and found your post and reset my parallel port in my bios. Worked like a charm.

Much appreciated

---

### Post by Wombat on 2005-02-24
Taffy or any kind soul,
I did what you said and it made no differance for selecting the printer ,but it got me thinking what I had done sinse I had the printer hooked up and was working.Well I downloaded the hoary new image K7 to correct the problem of the computer not shuting down from the logoff control,which it does now but that is where my printer would not work.So I rebooted into the i386 kernel and it was reconized and worked.I am using the gimp driver and cups.Now what do I fix in the hoary K7 kernal to make the printer work there.Anybody who reads this is welcome to give ideas.I have Simply Mepis on one pc and Ubuntu on the other and find it a lot faster and easier to fix problems in but this one  has me stumped,
Wombat PS I checked the option to email me if someone prefers this

---

