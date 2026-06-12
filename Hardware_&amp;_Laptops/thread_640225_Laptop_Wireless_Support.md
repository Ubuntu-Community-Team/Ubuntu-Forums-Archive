---
title: "Laptop Wireless Support"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by JeffoOfMetal on 2007-12-13
I'm using an Acer Aspire 3680 with an Atheros AR5007EG wireless adapter. With a Celeron and 512MB of memory, it struggles with Windows Vista Basic, so I want to switch it to Xubuntu or any other Linux distribution. I've already run the live CD's and checked the wireless support to find that wireless in Ubuntu doesn't work. I've read about using ndiswrapper to run with the driver, and I already use it on my other desktop, but I wanted to ask if there was a distribution of Linux with great driver support that I might be able to use with no modifications.

Thanks for any replies.

---

### Post by sbodas on 2007-12-14
Switching to another distro will likely not solve your problem.  If you look at the madwifi page, it says that your card is supported through a patch that hasn't been incorporated into the main branch yet:
> 
Notes:  Works perfectly with latest madwifi snapshot and this patch --> [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)


Here's the wiki link: [http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5007EG](http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5007EG)

Most likely, the fix for your card hasn't made it into the latest version of madwifi on most distros as the ticket in question is dated 2 weeks ago.  There's also some discussion about the origin or the patch. so there may be an extra delay while they work things out.

---

