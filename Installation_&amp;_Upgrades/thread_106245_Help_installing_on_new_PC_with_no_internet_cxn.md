---
title: "Help installing on new PC with no internet cxn"
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by zi99y on 2005-12-20
Yuletide greetings to all!

A small and hopefully easy question I hope someone can help me with:

I just moved into a new house and have to wait up to a month for a phone line & broadband (thanks bulldog :???: ), and have 2 networked pc's running another OS I care not to mention. I would like to reinstall these machines with Ubuntu using the installation boot CD that I have and will want to install other packages afterwards.

As I have a laptop running ubuntu with all of the packages installed that I will want to install on the other pc's, is there a way I can use synaptic or apt-get to download these files from my laptop instead of attempting to download off the internet.

This is all assuming I can setup the network properly on these pc's, but they are old-ish IBM machines with integrated ethernet so I think they are popular enough to be supported.

thanks in advance :)

---

### Post by kairu0 on 2005-12-20
If the packages are installed programs on your laptop, you probably won't have any luck. If you have .deb files that have been saved and cached by Synaptic, then they should be installable. Which are they?

---

### Post by zi99y on 2005-12-20
they're installed so maybe no good. where can I find the deb's if they are cached? I'm at work at the moment and will have no internet when I get home....

---

### Post by kosmic on 2005-12-20
it should be in /var/cache/apt/

---

### Post by zi99y on 2005-12-20
[QUOTE=kosmic]it should be in /var/cache/apt/[/QUOTE]
Thank you so much, I'll check this out tonight. So now I'm wondering if ```
apt-get install xxxx
```will download the debs and store them in /var/cache/apt before installing, or does it just store them in a temp directory and delete after install - well I'll answer that question when I get back.

Next part of my question - how can I get apt-get to find the debs on my laptop? Or will I have to use dpkg -i ? But then I'm concerned that it won't pickup the dependencies automatically?!!! :confused:

---

### Post by kosmic on 2005-12-20
It will store all your debs in /var/cache/apt/ and it only delete the cache when you do sudo apt-get clean or sudo apt-get autoclean or every n days :)

---

### Post by zi99y on 2005-12-20
good news then as I've never (afaik) done a clean. 

So am I forced to use dpkg -i ? or is there an easier way?

---

