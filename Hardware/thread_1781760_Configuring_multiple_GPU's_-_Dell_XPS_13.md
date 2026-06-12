---
title: "Configuring multiple GPU's - Dell XPS 13"
date: 2011-06-14
forum: Hardware
---

### Post by fenderr357 on 2011-06-14
Hi all,

I am running a Dell Studio XPS 13 with 11.04. This laptop comes with hybrid SLI, which works well in Windows but I am thinking that Ubuntu is powering up both GPU's and using my battery life FAST (about an hour.. compared to Windows at 3+ hours).

So basically I am wondering if there is a way to effectively shutdown one of the GPU's (either the 9400m or G210m) to save power (Nvidia "powermizer" shows both as active). I was thinking their might be a setting I can put in Xorg.conf, but I have no idea where to start. Also, I have checked the BIOS and there is no setting for this.

Thanks!

---

### Post by desktorp on 2011-06-14
I'm guessing it has some wonky Dell BIOS if it doesn't give you a pretty clear option for "Hybrid GPU - Enable/Disable" :mad:  That's usually in there somewhere, in a normal BIOS anyhow.. Beyond that, I can't imagine it would be easy, if nvidia-settings isn't letting you do it either.  Good question - keep us updated if you find a solution.

---

### Post by fenderr357 on 2011-06-16
Well, I found a "fix" but it didn't seem to work, at least for my specific GPU's. 
[URL="http://luizfar.wordpress.com/2010/06/29/how-to-switch-off-xps1340-discrete-video-card-on-linux/"]
http://luizfar.wordpress.com/2010/06/29/how-to-switch-off-xps1340-discrete-video-card-on-linux/[/URL]

When I enable the module, my computer begins locking up every 2-3 seconds.. Any ideas?

Thanks in advance!

---

