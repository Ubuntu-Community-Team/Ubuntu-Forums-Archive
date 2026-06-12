---
title: "how to use &quot; original&quot;  9.04 fglrx driver in my current desktop"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by mag00 on 2009-05-03
Hello guys,

I am in trouble here.

I am still a noob in linux but I really like this system, specially the Ubuntu distro, that is very user-friendly.

I was introduced to Ubuntu in 8.04 version and quickly updated it to 8.10, as it was released. Now I updated again to 9.04.

My problem is that I can not make my Gnome goes up.

I have upgraded it from Update manager and it was working "fine", except for some flashing of desktop area. I have read in many foruns that the drivers for this version of X was a little unstable, but accepted the risk to upgrade it.

Before I upgrade the Ubuntu, I have downloaded the CD version and write a copy of it to use as live system and try the compatibility with my hardware. And it works very well. Without the flashing desktop.

As the live sessions was working fine, I made a decision to solve this problem with my current installation and try to use the "same drivers" that the live cd was using. In this crusade, I dont know what I did here that my X now dont show anything unless a black screen.

Now, I want to know if anyone can help me to fix this problem with my current desktop installation with minimal losts.

What I mean with this? I noticed that the video drivers in live session works very fine, but the sound card not. Who knows what more does not work fine. I just want to try to fix the video card to continue using my PC like before.

I make some google searches to verify what are the command lines to remove all the informations of my video card and drivers from my current installation and what are the command lines to download and install the "drivers" that came originally in live session, but I didnt find nothing that go direclty to the point.

I have tried some things, like:

```
sudo aticonfig --initial -f
```
or
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

My video card is an ATI X600 pro PCI-E. This is not the best card in the world, but is what I have now.

There is any chance to solve this problem without reinstall all the system?

For now, I can say thank you, and offer to you my apologies for my bad english and the big post.

[]' s

---

### Post by Mark Phelps on 2009-05-05
You can't use any 9.04 fglrx driver with your desktop because AMD/ATI has dropped fglrx support for your card.  You will have to remove any fglrx driver and use the open source driver instead.

The link below shows you how to remove the fglrx driver:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

