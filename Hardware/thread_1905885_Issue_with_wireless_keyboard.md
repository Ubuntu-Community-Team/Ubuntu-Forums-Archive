---
title: "Issue with wireless keyboard"
date: 2012-01-07
forum: Hardware
---

### Post by thinkwired on 2012-01-07
I am thinking about installing Ubuntu on an old computer of mine but, I am concerned that my wireless keyboard does not offer Ubuntu support. What do people who run Ubuntu do when it comes to things like keyboard and mouse drivers? Are there any tricks?

BTW, my keyboard is a [http://www.iogear.com/product/GKM581R/](http://www.iogear.com/product/GKM581R/)

I apologize if this is not the most appropriate forum, I wasn't exactly sure where to post.

Thanks in advance.

---

### Post by lincoln32 on 2012-01-07
Currently using a logitech wireless with no issues other that I had installing batteries (non OS Issue) I have also used a MS bluetooth
desktop with success and several other 2.4 mice so you should be fine
and you could always test the live version fist to see what works but really
some wifi cards and some printers are the only real issues I have had with any ubuntu install and have done over 200 installs over the last 4 years :)

---

### Post by thinkwired on 2012-01-08
Does that logitec keyboard specifically state that it support Ubuntu? Some of the iogear keyboards do, mine on the other hand, says its for windows and mac only.

---

### Post by lincoln32 on 2012-01-08
I had all the wireless toys before my linux days or donated or just plain buy them and try it and sofar they have all worked fine---
I did get a usb 802.11n on ebay and had to wait a few months to be able to get a linux driver and after 6 months it was included in the new version of ubuntu. and 1 printer (lexmark that I never got to work) so I gave it to my kid  but they never even hooked it up so. I really never worry about linux support if it does not work now it will soon. and I only seem to have trouble with real new stuff and several printer lines:P

---

### Post by bluexrider on 2012-01-08
i went to the local 'wally-world' and picked up a wireless mouse and keyboard for under 30 bucks and they both work great with 11.04 the brand name is 'onn'

---

### Post by Cerin on 2013-01-22
> **thinkwired said:**
> I am thinking about installing Ubuntu on an old computer of mine but, I am concerned that my wireless keyboard does not offer Ubuntu support. What do people who run Ubuntu do when it comes to things like keyboard and mouse drivers? Are there any tricks?

BTW, my keyboard is a [http://www.iogear.com/product/GKM581R/](http://www.iogear.com/product/GKM581R/)

I apologize if this is not the most appropriate forum, I wasn't exactly sure where to post.

Thanks in advance.

Over a year later, but I thought I'd share my experience. I just bought this keyboard and am attempting to use it with Ubuntu 12.04. It generally "just works", but with a few major caveats.

First, after a few minutes of inactivity, the entire device turns off, requiring you to press an obscure "connect" button in order to reactivate it. I don't see any potential software solution to this.

Second, the mouse click buttons seem to have no debouncing, causing a single press to register multiple clicks. There might be a solution in Gnome/Xfce/Xorg's mouse settings, but I'm still researching it.

Third, if your power management settings or screensaver turn off the monitor due to inactivity, this keyboard appears unable to wake up the computer. I had to plug in a traditional USB keyboard to wake up my computer. Afterwards, I disabled the screensaver and editing my xorg conf to prevent the monitor from being automatically disabled due to inactivity.

Physically, the device feels very robust and of high-quality. However, the above three problems have made it incredibly frustrating to use, and unless I can find solutions, I'd generally recommend that no Linux user buy IOGear products.

---

### Post by RAMChYLD on 2013-01-23
Sorry for the necro, but since it was Necroed by someone else, I thought I should pitch in my experience.

Afaik, just because a keyboard doesn't say it's for Linux doesn't mean it wouldn't work. USB keyboards have to conform to a universal handling mode otherwise the firmware won't detect it at startup and thus the user cannot use it to go into the firmware setup or even use it to install an OS that doesn't come with drivers for it, which will of course anger many, many people. How much of the keyboard is functioning without the proprietary drivers is left to the manufacturer, but at very least the keyboard should be able to attain basic functionality without a driver on Linux. Just that all the fancy stuff (i.e. hot-keys, user-definable backlight color, external LCD display) won't work.

---

