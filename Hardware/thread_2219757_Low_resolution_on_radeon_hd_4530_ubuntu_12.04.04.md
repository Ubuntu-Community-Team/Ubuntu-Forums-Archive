---
title: "Low resolution on radeon hd 4530 ubuntu 12.04.04"
date: 2014-04-25
forum: Hardware
---

### Post by cadmy on 2014-04-25
I've just install Ubuntu and I can't solve the problem with low graphic settings. It isn't ugly low but it still not good enough. I did [this instruction]("https://launchpad.net/~makson96/+archive/fglrx") but it didn't work for me.
What should I do to improve resolution? I have no idea what to do.
I have ubuntu 12.04.04 and RV710/M92 [Mobility Radeon HD 4530/4570/545v] I'm ready to install older Ubuntu only to improve graphic if it would work.
The displays settings shows that is 1366*768 but I'm not sure about that it seems much lower. I used xrandr but it didn't help too.

---

### Post by coffeecat on 2014-04-25
> **cadmy said:**
> I'm ready to install older Ubuntu only to improve graphic if it would work.

Versions of Ubuntu prior to 12.04 are no longer supported on the desktop - that would not be a good idea. I have another suggestion. Rather than trying to get the proprietary Catalyst driver working with your graphcis card, have a look at the latest release, 14.04, with the default open source driver. Try it in a live session before you install. The open source ATI driver gets better with every release and, so long as you are not a gamer or have issues with fan speed control on a laptop, you may find that it fulfills what you need.

I have been using the ATI open source driver since before 12.04 with a number of different AMD cards and it has always served me well. The few times I've installed the Catalyst driver, I've promptly uninstalled it! :)

By the way - I've restored the default font and colour to your post. The font and colour you chose were hard to read. Please use the defaults except where you need emphasis.

---

### Post by cadmy on 2014-04-25
Thank you. I'll try to install 14.04. The only reason I need a higher resolution is I want to see more code per page.

---

