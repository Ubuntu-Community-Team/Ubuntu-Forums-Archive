---
title: "ARM Based Processors"
date: 2017-05-02
forum: Hardware
---

### Post by kelvinator on 2017-05-02
I am thinking of buying one of the cheap ARM based processor notebooks. What software limitations can I expect when trying to run Ubuntu on them?

---

### Post by Bucky Ball on 2017-05-02
Well, as standard Ubuntu ISO will not install or run on ARM processors, quite a few! A Ubuntu custom spin needs to be available for the specific device/ARM processor as I understand it (but I'm no guru). There are a few spins about for the Raspberry Pi and the Odroid and other things, but they are specific to the device and processor, community developed (not officially supported by Canonical so you take your chances) and come in various levels of successful.

If you're running an ARM processor on a laptop, you are probably looking at Android or some Franken-OS that the manufacturer's have developed for the machine. What OS does the machine you are looking at come with?

Have you done a search for '[ubuntu arm processor]("https://duckduckgo.com/?q=ubuntu+arm+processor&t=h_&ia=web")'??? Might throw some light on it for you. ;)

* There is a [Ubuntu Server version for ARM]("https://www.ubuntu.com/download/server/arm"), but not sure if that will install on any ARM processor, like a laptop, or even if it would be usable as a regular desktop system. Hopefully someone can give you some more clues. Good luck.

---

### Post by mastablasta on 2017-05-03
avoid it. get a celeron based one instead or an AMD A4 or E based APU would do just as well.

otherwise software compiled for ARM will run on it.
if nothing else debian has very good ARM support.

---

### Post by sp40140 on 2017-05-04
Why are you looking at arm based laptop?
What is your budget?

---

### Post by mail-2o on 2017-08-22
> **kelvinator said:**
> I am thinking of buying one of the cheap ARM based processor notebooks. What software limitations can I expect when trying to run Ubuntu on them?This really depends upon what you want to do with your notebook. I use both a Raspberry Pi and an Odroid. They are both very capable bits of hardware, but you should expect to struggle with a few things:
**Odroid XU4** - Fast, quirky, not that easy to set up. Great for web, mail, Kodi, dual boot ie DietPi and Android 7. Has USB 3, eMMC, doesn't share USB with ethernet bandwidth. Tiny, v. low power consumption, slightly irritating fan. Community small which assumes good knowledge of Debian and CLI. Would have to use the slightly less powerful C3 for a notebook.
**Raspberry Pi** - Not so fast, easy to set up. Great for web, mail, Kodi, dual boot through excellent Berry Boot. Tiny, v. low power consumption, great user community, mature OS (Raspbian).
My take is that the Ubuntu community has yet to see that the ARM community is growing fast and the X86 community is shrinking, except for gamers and for some high power applications. I'd love to see some of the Ubuntu experts (I'm not one) embrace the ARM community as the way ahead. There are several other low cost ARM based netbooks appearing. It would be great to hear from some Ubuntu users and how they faired.
**Pinebook 64**. Has anyone any experience of this very low cost ARM netbook? It sounds interesting. [Pinebook]("https://www.pine64.org/?page_id=3707")
**Ceres.** You might be better off by paying a bit extra and playing safe with a [Nimbusoft]("https://nimbusoft.com/product/ceres/") laptop

---

