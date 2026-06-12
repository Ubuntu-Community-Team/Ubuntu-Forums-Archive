---
title: "Dell Reinstall not working. cannot boot. formatt HDD??"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by captainron042 on 2009-05-16
I recieved my Dell XPS M1330 a few days ago. Update manager was acting funny and said that I needed to get something manually. After that, I had problems booting, mainly the error Kernel Panic - not syncing, attempted to kill init!

Sometimes I get stuck on a screen that says (initramfs)

ubuntu 8.04 CD not installing, and neither is the dvd I made with the dell reinstall on it. I sometimes get to the messege that asks if I really want to erase all data and install ubuntu again and I type ERASE, but I still get hangups and errors.

Dell wants me to get a windows CD so they can help me format and start from scratch, but I cannot get one. 

Will another program work, such as gparted-live-0.4.4-1.iso, which I have dowloaded and am ready to try if I get a go ahead by someone. (and maybe a walkthrough of the choices I need to select.

thanks in advance, guys.

Dell XPS M1330, solid state HDD, Intel Core 2 Duo T5850(2.16GHz, 667Mhz, 2M L2 Cache)

---

### Post by captainron042 on 2009-05-17
Well, I tried Gparted. I deleted everything off of the HDD, created a partion with ext3 as the filesystem.

I try to install the dell reinstall cd and the factory-shipped ubuntu CD, and I'm still getting errors. I can't even "try ubuntu without changes to my computer"

I'm getting stuck at these errors, ect:

* Kernel Panic not syncing attempted to kill init
* Fixing recursive fault but reboot is needed 
* (initramfs)
* freezing up at the Ubuntu splash screen (the orange bar doesn't move)

I don't understand how I can get these problems whe there is nothing on the HDD. I ask dell for help, and they're telling me that there's no problem with the hardware so it's my problem. I can send it back, but then I'm looking at wasted shipping costs and possibly a 15% restocking fee.

Can someone please help? I'm at a loss

---

### Post by supershin on 2009-05-17
If you can run it the live cd i guess its not the hardware. Maybe you can try running a check disk for any disk errors. e3fdsk i think, I'm not sure on the actual command but its something you could look into until someone else helps.

---

### Post by captainron042 on 2009-05-17
thanks for the reply, supershin

I cannot run a live CD. I get the same errors.

I also did a diagnostics check, and it passed all tests.

could the RAM be screwed up, and since the Live Cd uses ram, it would give me the same errors?

---

### Post by captainron042 on 2009-05-17
I'm on the phone with them right now to have it sent in. Dell's ubuntu upport guy stayed on the line with me as he transferred me over to the hardware support, who is the only dept. that can authorize a return. That guy tried to give me crap about it being Ubuntu, and the diagnostics test passes, so it's a software problem, but the Ubuntu guy spoke up and told him that he needs to authorize a return to the depot and stop transferring me around. It was quite funny!

Hopefully, they actually replace the hardware instead of somehow getting it to barely work again.

Thanks for your help, guys.

---

