---
title: "Latest version of Ubuntu and my wireless card?"
date: 2009-05-26
forum: Hardware
---

### Post by Zer0 Suii on 2009-05-26
Hello good people of the Ubuntu forums! I have a slight problem here...

This is my first run on any Linux operating system. I have a Dell Inspiron 1200 laptop that I've installed ubuntu on. Besides the installation on Ubuntu, I've had this operating system for an hour. Everything onboard works (I hope. I heard a boot-up sound when it took me to the desktop, but none after.)

My problem is that I have a wireless card that I bought on eBay for this baby when I still had Windows (blech!), and Ubuntu doesn't recognize me plugging it in. This wireless card is a WPC54G v3 Linksys PC card. It worked with my windows platforms (I'm experimenting with my laptop since it only has 256 RAM, so I've had Windows XP (slow success), Windows 98 (partial success), and Windows 2000 (great success) right before installing Ubuntu (current)). I'm just worried that it will not work with this system now. I've Googled information on what to do, and it took me here. I downloaded a package for it, and nothing happened after installation. So I'm a little miffed. The card only cost me $12 USD I think. It wasn't expensive. That's all I remembered. I just need to be pointed in the right direction. Thanks!

But upon declaring that I needed to ask you all for help, I decided to play around with this systems features. I love them.

Thanks Ubuntu and Ubuntu community!

---

### Post by IcarusR on 2009-05-26
Hi, try searching the forum for WPC54G there are a lot of threads on how to do this.
Then if you have troubles then post with as much info as you can, ie what you've done & any error messages.

Icarus

---

### Post by 73ckn797 on 2009-05-26
If you have the driver disk that came with the card you can install those drivers in Ubuntu using "ndisgtk" (a GUI installer) found in Synaptic Package Manager. Or download them from the manufacturer site first.  Once installed copy the driver and all other files in the folder (possibly the Win XP driver folder) to a folder then run ndisgtk which you will find installed under System/Administration/Wireless Drivers. Select the driver (inf file) you copied and let it install it.

---

### Post by Zer0 Suii on 2009-05-26
> **73ckn797 said:**
> If you have the driver disk that came with the card you can install those drivers in Ubuntu using "ndisgtk" (a GUI installer) found in Synaptic Package Manager.

I didn't find any "ndisgtk" items when I searched the Synaptic Package Manager. Did I do something wrong? Sorry about being a newb. This is the first time I ran something other than Windows.

---

### Post by 73ckn797 on 2009-05-26
> **Zer0 Suii said:**
> I didn't find any "ndisgtk" items when I searched the Synaptic Package Manager. Did I do something wrong? Sorry about being a newb. This is the first time I ran something other than Windows.

Have you enabled all sources in Synaptic under Third-Party Software and the multi and universe repositories?

---

### Post by Zer0 Suii on 2009-05-27
Thank you VERY much, 73ckn797! I'm using my (finally) working wireless card to send this! Thank you very much! I forgot to reboot after the process, so I almost gave up while turning off my laptop. And now it works! Thank you!:mrgreen: Have a great day, now!

And thank you, IcarusR, as well!

I wish you both a great day!

---

