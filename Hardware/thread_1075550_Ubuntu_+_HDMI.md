---
title: "Ubuntu + HDMI"
date: 2009-02-20
forum: Hardware
---

### Post by -tc- on 2009-02-20
Hi there,
Ive had browse through othr forum topics covering hdmi and more resouces, i probably missed something, so if u know another topic where i can find the answer just post it, or you can try and help me out here :) It would be appretiated.

Ive installed ubuntu on my laptop (Sony Vaio VGN FZ21s), and it has a hdmi output. But when i plug the hdmi cable in, it does not recognise that it has been connected to the external screen (Acer x222w 22"). Its running an nVidia graphics card.

-tc-

---

### Post by jespdj on 2009-02-20
Are you using the nVidia proprietary driver? Install nvidia-settings and run it to setup your screens.

---

### Post by -tc- on 2009-02-21
Yes i have the nvidea proprietary driver activated. I got a message after installing ubuntu that there were drivers that were not open source etc.. do i want to activate it anyway, so i did.

How do i go about installing nvidia-settings, i had a browse to find out more and some people reported problems with it like it ruining X, is this still an issue?

Thanks.

---

### Post by _noob_ on 2009-02-21
I'm Having a problem with my laptop. Gateway P series. I'm not entirely sur on where to post this or the specs of my laptop. But it has an HDMI output. I plug it into the HD tv and I don't get any sound. Any suggestions? Sorry if this is posted improperly.

---

### Post by -tc- on 2009-02-21
Theres a couple of threads on these forums about getting the sound to work over the hdmi output, i would send you a link but i dnt have the urls anymore.
You are best searching or starting your own thread since your problem is different to the one that i am trying to get solved here.
My problem is that ubuntu doesnt even recognise the external screen when its plugged in via hdmi.

---

### Post by -tc- on 2009-02-22
can anyone else point me in the right direction to get this sorted?

---

### Post by highgeere on 2009-02-24
You can install nvidia-settings through synaptic. Once installed you should have a new menu item in the administration menu named 'nvidia x server settings'. You can launch it that way, but if you use 'sudo nvidia-settings' from a terminal then you will be able to save the changes to your x configuration when done. If you use the menu item you won't be able to mave the changes permanent. Launch nvidia-settings and configure the second display. If you use twinview you should be able to apply the changes immediately. If it doesn't work you can change it back. I've done it on multiple systems and it really isn't that tricky.

---

