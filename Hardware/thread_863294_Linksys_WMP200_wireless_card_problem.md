---
title: "Linksys WMP200 wireless card problem"
date: 2008-07-18
forum: Hardware
---

### Post by mvanstone88 on 2008-07-18
I'm running Ubuntu 8.04 and trying to install a Linksys WMP200 wireless adapter. I figured it would pick up that i installed it on boot and ask me to authorize the use of restricted drivers, but I got nothing. I just installed a WPC54g on a laptop and it worked fine out of the box.

I've heard about using the ndiswrapper, but not sure if that will fix my problem, and i don't know how to configure it. Can anyone help me out here ?

---

### Post by icarus42 on 2008-07-18
ndiswrapper usually works really well, what you need to do first is install it via synaptic, you can install ndisgtk which gives a graphical interface. Once that is installed exit synaptic and then go to system --> administration, then select ndisgtk. You are going to need your wireless drivers also.

Hope that this helps you

---

### Post by mvanstone88 on 2008-07-18
Should I be at all worried that nothing got found when I booted the first time ?

---

### Post by icarus42 on 2008-07-18
Do you mean the wireless wasn't found on initial installation?

I honestly don't think that should be a problem, as long as ndiswrapper supports your wireless card.

---

### Post by mvanstone88 on 2008-07-18
Yes i mean when i installed the card and booted into ubuntu I expected some sort of hardware recognition, is that wrong to assume ?

---

### Post by icarus42 on 2008-07-20
sorry for the really late reply; sometimes ubuntu will not recognize the card, that is ok.

---

