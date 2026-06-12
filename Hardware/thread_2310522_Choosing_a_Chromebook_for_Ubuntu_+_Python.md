---
title: "Choosing a Chromebook for Ubuntu + Python"
date: 2016-01-20
forum: Hardware
---

### Post by verdigris2 on 2016-01-20
Hello everyone,

I am hoping to get a cheap and light little laptop to do some Word Processing, browsing and Python coding.
I a new to Python and am not sure how complex it would get (I am following the Natural Language Toolkit Book [here]("http://www.nltk.org/book/")).

I figured the best way to go would be to load Ubuntu over a Chromebook.

Which of the following would you recommend? Has anyone tried loading Ubuntu over similar hardware? Have you experienced any problems with compatibility?

[Asus C201: Quad-Core Rockchip 1.8GHz + 2GB RAM]("https://www.asus.com/ca-en/Notebooks/ASUS_Chromebook_C201/specifications/")
or
[Acer CB3-111-C6NE: Dual-Core Intel Celeron 2.16GHz + 4GB RAM]("http://www.acer.com/ac/en/CA/content/model/NX.MQNAA.007")

Which would you recommend?

Thank you!

---

### Post by newbie-user on 2016-01-21
I personally have an Acer C720 Chromebook that I use with Ubuntu. I just used Crouton ([https://github.com/dnschneid/crouton]("https://github.com/dnschneid/crouton")) to install Ubuntu alongside Chrome OS rather than doing a dual boot. If you want to do this, you'd be better off getting an Intel-based Chromebook like the CB3-111 you mentioned.

---

### Post by robertusa on 2016-12-06
Dual boot is the way to go to get a clean and full Linux install, and maintain the ChromeOS distro properly. "Sideloading" makes for easy Ubuntu-like installs, but doesn't really provide the best of each native environment from a long-term use and flexibility perspective. Decoupling OS variants is often the best approach to achieving the value from each distro.

However, there are some installation glitches with the current model Acer and Samsung Chromebooks.

[COLOR=#000000]I found in necessary to use [/COLOR][https://etcher.io/](https://etcher.io/)[COLOR=#000000] to burn the ISO image to USB, as the standard Ubuntu tools would not work reliably, seemingly building an incompabible boot stack configuration.[/COLOR]

[COLOR=#000000]Having accomplished this, the next hurdle is that the native hardware USB keyboard-mouse is completely non-functional. I imagine a USB keyboard-mouse might work, but I do not have them available to test.[/COLOR]

[COLOR=#000000]These are very popular devices in education and business. These devices could be useful for R&D and software development with 4G RAM and dual core. Not the fastest, but certainly something usable while lowering the cost of entry for software development to $100 to $200. The Samsung xe500c13-K02 would be much more useful with Ubuntu, Mint, or GalliumOS installed.[/COLOR]

[COLOR=#000000]Can someone take the lead in updating-fixing the boot-config-stack to support the Samsung xe500c13-K02us?[/COLOR]

[COLOR=#000000]I'm happy to participate in testing of the Samsung xe500c13-K02 or Acer [/COLOR][COLOR=#417394]CB3-111[/COLOR][COLOR=#000000]. I also have access to many other models of Chromebook, Dell, and other machines to test. [/COLOR]

[COLOR=#000000]What is needed is someone to coordinate the release of "debug mode" Ubuntu OS so we can get these popular machines up and running Ubuntu vs. ChromeOS.[/COLOR]

---

