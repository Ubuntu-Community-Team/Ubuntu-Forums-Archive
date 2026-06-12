---
title: "Dual monitor with Intel and Nvidia graphics card"
date: 2009-10-11
forum: Hardware
---

### Post by spinoza666 on 2009-10-11
Hey people,

I have a bit of problem getting my PC monitor and TV set up and was hoping the esteemed ubuntu community might help me out.

I have an Intel grapchics card on the motherboard, and installed a Nvidia GeForce 9800 GT card as well. My PC monitor is hooked up to the Nvidia card by VGA and running fine. The integrated Intel card has a VGA output, while the Nvidia has DVI and HDMI.

I'm trying to hook this up to my TV which has a DVI input already occupied by my DVD-recorder, and a VGA input.

If I use the the integrated VGA to connect to my VGA input on the screen I get a blank screen. I realize that I need to configure my xorg.conf, but finding this pretty damn hellish... Does anybody know how to do this?

Or does anybody have any other ideas that might be a bit simpler?

Cheers

---

### Post by spinoza666 on 2009-10-14
Bump.

Anyone?

---

### Post by rmic on 2009-10-20
Hi !

I wrote a post some time ago about this : [http://www.rmic.be/5-easy-steps-to-enable-dual-screen-in-Ubuntu](http://www.rmic.be/5-easy-steps-to-enable-dual-screen-in-Ubuntu)

it's just a matter of installing nvidia-glx and configuring your screens.

Hope this helps !

---

### Post by spinoza666 on 2009-10-20
Will installing the nvidia-glx package actually let me run output from both my integrated Intel graphics card and my Nvidia card? One screen each at the same time.

I mean I already have the driver for my Nvidia card installed by the Ubuntu proprietary driver installer. And by running nvidia-settings I automatically set my xorg.conf file, but this did not adjust it so that both the integrated and external graphics card would be active.

Sorry if I'm a bit slow here. I just don't get how this will work?

---

