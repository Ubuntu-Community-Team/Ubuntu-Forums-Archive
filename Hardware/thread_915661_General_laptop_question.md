---
title: "General laptop question"
date: 2008-09-10
forum: Hardware
---

### Post by chuuk on 2008-09-10
I'm a fairly new user of Ubuntu, I installed it a few months ago so that it dual-boots along with XP on my ageing laptop - it works beautifully and despite some apprehension, I've found using Ubuntu to be quite a pleasant experience.

In a few months, I'll be off to college and the college PCs dual boot with XP/Vista and Ubuntu as well. Now I'm looking to buy myself a laptop which I'll be able to use around college, which will be cost effective as well. I don't game at all - I use the laptop to surf the internet, and will be using it for programming once I do begin my course. For my usage, Ubuntu is perfect. It will also offer me great savings in terms of cost and allow me to focus more on performance.

So I was just wondering whether it's too much of a problem installing Linux on laptops with only DOS preinstalled. Are there many driver issues? I read about this on some forum and I'm not too keen on having to spend too many hours fiddling with the laptop if there are, and would rather go for something dual-booting.

Sorry if I'm asking stupid questions - while I'm not a complete beginner, I don't know too much either. Any guidance is much appreciated.

---

### Post by amo-ej1 on 2008-09-10
Oh, the typical things apply, don't spend too much money on a laptop, they will die eventually or end up being worthless. Typically a bit more aged hardware is better supported than bleeding edge, and before you purchase one, just throw the type of the laptop and the word linux together in google. 

The main points your attention should go to is the support of the wifi driver.

---

### Post by kpkeerthi on 2008-09-10
[http://ubuntuforums.org/showthread.php?t=910087](http://ubuntuforums.org/showthread.php?t=910087)

---

### Post by Idefix82 on 2008-09-10
I guess the safest thing you could do is go for a laptop with Ubuntu preinstalled. Dell offers some, as do others.
Try to avoid Broadcom hardware, especially WiFi cards, Intel is a safer option. As for other pieces of hardware, not dual booting will increase your chances of it working flawlessly.

---

### Post by IntuitiveNipple on 2008-09-10
If you'll be using it for programming then having fast dual-core processors and plenty of RAM, and the ability to expand, will help when you get to the point of building large packages, or running IDEs like Eclipse.

I would also recommend you choose one that has a CPU that has hardware support for virtualisation (VT) *and* (this is important!) that VT is pre-enabled or selectable in BIOS (Most Sony Vaios don't have the option to enable VT and have to have a one-timer NVRAM 'hack' applied). This will help if you want to write/test code in isolation, or for alternate operating systems (hardware VT makes virtual machines run close to phyiscal machine speeds).

Virtualisation infers a 64-bit CPU which is useful, especially if you install the amd64 build of Ubuntu (not the i386 build).

Be wary of the video chip-set. For preference most Nvidia chip-sets have good (proprietary) driver support. Intel have good open-source drivers. ATI still seem to have a variety of issues although that appears to be improving very recently. Avoid Silicon Motion or VIA video chip-sets.

I would strongly recommend taking an Ubuntu Live CD and USB memory-stick to a showroom and running it on a potential machine, and then copying the /var/log/dmesg file to the USB stick along with the results of:
```

sudo lspci -vnn

lsusb -v

lshal

```
From those you can do some final research to ensure there isn't hardware that had drivers issues.

---

### Post by chuuk on 2008-09-10
Yeah things work beautifully on my old laptop at home - absolutely no problems. Will take the CD to the showroom and see if they let me fiddle around with it. And if not, I guess it's just giving it a shot. Will keep your advice in mind. Thanks ;)

---

