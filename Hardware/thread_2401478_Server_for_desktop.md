---
title: "Server for desktop?"
date: 2018-09-18
forum: Hardware
---

### Post by Randymanme on 2018-09-18
I don't presently have a computer, but I'm looking for an used one. If I can find something like, say, quad core, 3.0 GHz, 8 GB, 500 GB Hdd, with hyperthreading and hardware virtualization for under $100, I'd be excited.

Browsing online, I happened upon: "... HP DL385 G6 Server with dual 2.20 Ghz AMD 2427 6 Core Processors (12 Core total). Has 32GB of RAM installed. NO HD or OS. 4X 1GB Network w/iLo. HP Smart Array P410 Controller. Comes with rails. Has single 460W power supply. Will included the 2nd power supply but it recently failed.  Asking price is $100."

My question, is would it be practical for me to use this to run desktop operating systems?  

If memory serves me correctly, I once downloaded an Ubuntu Server OS by accident and had it installed before discovering it; so it seems like I could use a server for my daily driver. 

If it wouldn't be practical to install desktop operating systems bare metal, how about installing a hypervisor first?  I can find hdds.

---

### Post by mastablasta on 2018-09-19
> **Randymanme said:**
> 
My question, is would it be practical for me to use this to run desktop operating systems?  


yes you can run desktop on "server" pc and vice versa. 

server in OS terms mean the OS is optimised for computers that serve other computers various services.

server in PC term means the computer has optimised hardware to be able to server multiple computers usually working 24/7. server usually have better ram (ECC), RAID options, some have hot swap drive bays (so you can exchange drive while the PC is on), uusally they have more durable components, and are made even more modular than PC (case is often optimised to be easy service) but on the other hand they are also more expensive. they also do not (usually) have a strong GPU, since that is usually not a requirement (server OS usually runs in CLI). however many servers have expansion options though PCIe slots and microservers also USB ports (for example my microserver has 9 USB ports by default).

so with that in mind old (or new) server can actually serve as desktop. if you plan on gaming you likely need to add good GPU. you might (but not necessarily) also need a GPU upgrade if you plan to watch some HD movies. but for office work it will probably be just fine.

---

### Post by Randymanme on 2018-09-19
Hello. 
Thank you for answering my question. I appreciate it. 
Google is my friend. I also found an answer at:  [https://www.makeuseof.com/tag/difference-ubuntu-desktop-ubuntu-server/](https://www.makeuseof.com/tag/difference-ubuntu-desktop-ubuntu-server/)

“... After Ubuntu 12.04, both Server and Desktop variants use the same kernel. Previously, Desktop and Server used different kernels. Because both Ubuntu Desktop and Ubuntu Server employ the same kernel, you can add any packages to either variant. This means that while default installation varies, you can customize your Ubuntu flavor accordingly.

So you might start with Ubuntu Server and install a desktop environment if you decide you can’t run it headless. Alternatively, you could begin with Ubuntu Desktop and add the necessary packages to create a server. Since Ubuntu Server and Desktop share a core Ubuntu kernel, default installation differences don’t preclude future software package installs.”
So, now, I just need to make sure the server isn't on the incompatibility list.  
I've been forewarned on another forum that I'll want to run the server in a different room because it's rather noisy (but not a closet because of the need for air flow). 
When I saw the advertisement for the abovementioned server, I didn't look any further until later. When I did look further, I found that the party selling this one has another one for sale:
“Used HP Proliant DL380 G5 Server with dual Quad Core 2.33 Ghz CPU and 6GB of RAM. All drives have been removed. Has dual power supplies. Asking price is $55.”  This one may not be as noisy and it is more affordable. 
Thanks

---

### Post by mastablasta on 2018-09-20
servers with large fans are not noisy. the fans are usually of better quality. 

servers can get noisy (just like desktops) if they have small fans mounted and if you task the CPU a lot.

---

