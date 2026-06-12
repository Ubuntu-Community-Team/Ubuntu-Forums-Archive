---
title: "MSI K8MM-V compatibility with ubuntu"
date: 2006-01-26
forum: Hardware &amp; Laptops
---

### Post by manish_m on 2006-01-26
hi
i m planing to buy a pc based on AMD64. I wanted to know if MSI K8MM-V is well supported under ubuntu.
Kindly tell me any issues if present, with using this motherboard.

---

### Post by eeried on 2007-02-05
However late my message after the possible event of your purchase, I ought to say this motherboard may or may not work well.

In an instance I know of because I'm trying to have it work with Ubuntu right now, here's my experience.

When I first installed Ubuntu Dapper everything was fine: sound and LAN, in particular while the graphic card i found out later is an ATI Radeon 9200Pro.

Later the screen froze anytime, out of the blue and it was impossible to get behind X (that is use the keyboard and the Crtl+alt+F1).

After reconfiguring Xserver-xorg in different ways, I came to the conclusion that the problem lay perhaps with the graphic card and Xorg or with the screen and Xorg, after an upgrade.

I tried to install Kaella (Frenchified Knoppix) to see what Xorg.config file it would create. Using the Live-CD was fine but when I installed Kaella I got the same instability. After a few minutes or even less, the screen froze.

Mandriva 2007 was even worse. It installed fine but the screen froze almost immediately after booting.

Finally I thought the solution was to move to Edgy and update it immediately. I'm on dial-up and only have an Alternate Xubuntu Edgy CD. So Installed it on a different partition from Ubuntu Dapper and we spend a delightful afternoon playing two DVDs. The sound card is quite a change from that on my old computer. We were able to listen to some music as weel. We used Xmms and xine. (I installed xmms off line from the various files present in the Ubuntu Dapper installation on another partition, as well as libdvdcss2 which was useful for xine). BTW a great thing Xubuntu has moved to xine instead of Xfcmedia).

This morning, the screen froze after a couple of minutes on Firefox.

So I upgraded outside X, (i removed OOo-writer and dependencies for a less bulky upgrade) and I'm now scribbling away. Let's hope things are all right now.

So I'm not sure the motherboard is at fault. It could be the graphic card, couldn't it?  I haven't installed any additional drivers because the person who uses it doesn't care for 3D effects and doesn't play games.

A Fedora  user posting on the French-speaking forum has pointed out Ubuntu runs on "old" kernels, so I hope moving to a less old kernel + newer Xorg version may do the trick.

I'll report in some moments or tomorrow. let's keep our fingers crossed :guitar: 

cheers

---

