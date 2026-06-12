---
title: "I need kind of terminal server"
date: 2008-10-27
forum: General Help
---

### Post by Green_Star on 2008-10-27
Hi,

I have two laptops, I guess there are errors in my hard drive so it is not working well. I do not want to buy another hard drive because these machines are too old, and could die any time.

So what I am thinking is, I have minimum os installed on CD(no USB)and laptop boots from CD, loads the wireless network card. then it connects to my desktop machine located in basement, and boots again from iso located in desktop machine. And all/major CPU operation should be done in my desktop and I work from laptop, all sound , playing movies should work. (for now this current laptop can even pay youtube properly, it stuck frequently with high cpu usage).

do you have any solution for that?

---

### Post by greatgoogamooga on 2008-10-27
You can do what you are asking by using an Ubuntu Desktop CD to boot your Laptop, then log into another Ubuntu computer using XDMCP at the login screen.  The only downside (and this would apply to most any way you choose to do a remote login) would be the lag time from your network.

Goog

---

### Post by Green_Star on 2008-10-27
> **greatgoogamooga said:**
> You can do what you are asking by using an Ubuntu Desktop CD to boot your Laptop, then log into another Ubuntu computer using XDMCP at the login screen.  The only downside (and this would apply to most any way you choose to do a remote login) would be the lag time from your network.

Goog

Thanks for your reply. Some time back(7.10 I guess) I tried, and my XDMCP is not working, I guess Gnome bugs!!. I am not sure about 8.04. 

I am thinking about NXClient/Server. Because I am using this right now with some online computer located at my ISP, and I do not see any lag time when I click. But I have problems with sound. 

I am open to any kind of solution which is easy to setup(I love the idea of XDMCP) and multimedia should work.

---

### Post by koenn on 2008-10-27
look up LTSP, they do something like that. 
The usual way is that you boot of a network card, but that can often be replaced by an other bootable medium

---

