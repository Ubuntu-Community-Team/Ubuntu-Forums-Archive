---
title: "Cannot Connect via Remote Desktop"
date: 2008-08-11
forum: General Help
---

### Post by GmAz on 2008-08-11
I've been using UltraVNC (uvnc.com) on my Windows Vista machine for ages, but cannot get Remote Desktop on ubunto 8.04 at all.  I can connect to it when I am on my home network from my XP laptop and from my iPhone, but cannot get it to connect from the web at all.  

I know my external IP, I have port 5900 directed to my desktop's IP, and my desktop's IP is static so is not gonna change on me.  Is there a built in Ubuntu firewall I need to add port 5900 to or something.  If not, is there a good alternative I can use so I can remote to my home PC from anywhere?

---

### Post by timcredible on 2008-08-11
i recommend using xdm since it's what you use when you login locally.  click on my sig link for a how-to.

---

### Post by Vadi on 2008-08-11
Try enabling the port with Gufw ([http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)).

Let me know if that helps.

---

