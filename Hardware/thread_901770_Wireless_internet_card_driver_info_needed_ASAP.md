---
title: "Wireless internet card driver info needed ASAP"
date: 2008-08-26
forum: Hardware
---

### Post by 73ckn797 on 2008-08-26
OK. 3 week Newbie. Hardy has installed flawlessly on my desktop and laptop. The only problems are usually due to my inexperience with the OS.

Installed Hardy Studio 64 on another computer. It does not recognize the wireless card. Have found several options to correct, most fail. When I boot a live CD for Hardy 64 the wireless is working.

My questions are:

Why couldn't I get the driver off of the Hardy 64 disk and install it into the Studio 64 system? If it works on the Ubuntu 64 live CD why couldn't it work in Studio? It seems obvious that there is a native driver in the Ubuntu 64 disk. Is it the different kernels that would affect the ability to migrate/install the driver from one into the other? My searching only results in a file from Ralink but upon further reading it seems that I would have to compile a driver. I found no driver "inf" file in the compressed file. I do not know enough to program a driver!

To do that I would need to know where the driver resides on the CD. Is there a particular file to look for? 

Is there any info about what and where different file types are stored within the directories so I might find it?

---

### Post by jbrown96 on 2008-08-26
no point in sniffing around the cd. Ubuntu doesn't use .infs (unless you are using a Windows driver via ndiswrapper). What type of card is it? ```
lspci | grep Network
``` should be able to find it.

---

### Post by 73ckn797 on 2008-08-26
Card is Linksys WMP54G v4.5.

I will try the info provided.

I had problem connecting with a cabled connection but that is working fine now. Having a connection is more important than which type I have. That solution was accomplished just after posting this thread. Knowing that a cable can go bad will make me continue to resolve the wireless issue.

Thanks.

---

