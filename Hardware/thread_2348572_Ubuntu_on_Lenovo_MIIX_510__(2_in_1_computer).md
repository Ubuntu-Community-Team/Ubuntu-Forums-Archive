---
title: "Ubuntu on Lenovo MIIX 510  (2 in 1 computer)"
date: 2017-01-05
forum: Hardware
---

### Post by phi1ip on 2017-01-05
Hello,

I was wondering if I can get Ubuntu to install on Lenovo MIIX 510? (it's similar to a suface pro 4)

Has anyone had any luck on this?

---

### Post by nontro on 2017-09-13
> **phi1ip said:**
> Hello,

I was wondering if I can get Ubuntu to install on Lenovo MIIX 510? (it's similar to a suface pro 4)

Has anyone had any luck on this?

Hi I did it, I have a MIIX 510 and Kubuntu.

it works fine but I had some problems with the wifi card. 
 
It was blacklisted and you have to unlock it with this command
sudo tee /etc/modprobe.d/blacklist-ideapad.conf <<< "blacklist ideapad_laptop"

Second issue, the touchpad freeze constinuosly and I have to disconnect (phisically) and reconnect the keybord from the pad.
I am trying to figuring out how to solve but at the moment I have no idea.

---

### Post by Weisskrautbrautkleid on 2017-12-29
Hey nontro,

I experience the same touchpad freeze issue with my MIIX 510. Have you been able to find a solution to this since your last post?
Thanks for any help.

---

### Post by sev8 on 2017-12-30
I've just bought a Miix 510 and had a problem running Ubuntu and Kubuntu with the trackpad freezing too.  It would get stuck in scroll mode and I wouldn't be able to move the pointer.  Sometimes I could recover it, but couldn't work out how to do it reliably.  I'm now running Ubuntu and I managed to fix it by turning off 2 finger scroll, it's been working fine for the last 24 hours using edge scrolling only.

Other than the wifi blacklisting, the only other thing that doesn't work are the cameras.  There's a kernel driver for the front facing camera (OV2680) in staging, so I'm trying to compile my own kernel to see if I can get it working.

If anyone has got the camera working already I'd love to know how.

Cheers,

sev

---

### Post by sev8 on 2017-12-30
Just to add, disabling 2 finger scroll makes tablet mode a lot more difficult to use as you'll need to scroll using the window scroll bars

---

### Post by doenit on 2018-05-25
Hi
I'm also struggeling with camera, you got a solution jet?

---

