---
title: "Connecting to my server"
date: 2008-09-22
forum: General Help
---

### Post by JohnRP on 2008-09-22
Hi I am very new to Ubuntu I have just installed it within my windows vista laptop. When in Vista mode the internet connection is fine, but when in Ubuntu mode the modem is showing the green lights but I can't log on. My ISP (Tesco.net)says it has no support for Linux based OS Is there a work around for the not too tecnical? I'm writing this on my old XP Desk top  The laptop is wireless enabled. Can I solve the problem by setting up a  wireess home net work?If so which would be compatable?

---

### Post by theDaveTheRave on 2008-09-22
a couple of quick questions.

Is it a broadband or dialup, I know that it sounds silly (Especially with everyone on braodband nowadays) but historically it was a pain to access some dialup ISP's

If it is on broadband I would suggest the following.

get a wireless router, and add in the required setting for your tesco broadband connection - often done via a hard wire link into the back of the wireless unit - this i recomended as often wireless capabilities in Ubuntu can be "fun" to get working!

Your wireless router will act as the default pathway to the internet, and can act as a DHCP (in most cases I've heard about). Once sorted you can then use your desktop box as the LAN controller... blah blah blah... you'll need to get another thread going for that though as it is a while since I set it up, and I failed to make help screens - sorry!

Dave

---

### Post by Taxman415a on 2008-09-22
Assuming you have high speed internet, yes, you could solve this issue by setting up a wireless network.You basically just buy a wireless router such as a dlink or Linksys or whatever is available where you are, and connect that to your broadband (dsl or cable) modem and then follow the instructions that came with it for how to set it up. I have a dlink DIR-615 and that's all I did. I can't say it's the greatest thing ever for range, but it's been very reliable with no problems. It  came with manual setup information for use with Linux. I understand the Linksys routers work fine too.

Your other option is to figure out why your laptop isn't connecting to the internet currently. Try connecting it properly, boot into Ubuntu and then give us the output of ```
ifconfig -a
```
That should tell us if you are picking up a dhcp address or not.

---

### Post by JohnRP on 2008-09-24
Many thanks I will try this.

---

