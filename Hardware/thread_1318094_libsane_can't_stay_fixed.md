---
title: "libsane can't stay fixed"
date: 2009-11-07
forum: Hardware
---

### Post by ecowan on 2009-11-07
After months of tinkering and searching I finally got my scanner to work properly - for about a day and a half. Then it started complaining again about a variety of things, although still working in its simplest mode, if I powered it off and on agin after a fault.

I was running the following packages on both server and laptop:
libsane    1.0.19-23ubuntu7
sane-utils 1.0.19-23ubuntu7
xsane      0.996-1ubuntu2

I have an HP Scanjet 8250. It has a document feeder and a transparency/negative scanner built in. It's connected by USB to my server which runs a fully up-to-date Ubuntu Jaunty.

I want use my laptop (up-to-date Kubuntu Jaunty) to access it over my wifi. With the latest Jaunty upgrades, I was able to use it remotely, in flatbed, Automatic Doument Feeder and Transpaerncy scan modes. It worked with Kooka and Xsane, although when Kooka ran the Automatic Document Feeder it made a horrible grinding noise. Mostly I prefer Xsane as the front end. Life was beautiful.

In a rage of frustration I tried purging and reinstalling everything in sight to do with scanning.

Finally, after downgrading the server to libsane_1.0.18-23ubuntu1_i386.deb and then upgrading to ...19... again, things started working again. (A reinstall of libsane...19... alone didn't do it.)

I hope someone who understands these things will read this and pass it on to someone who knows how to fix it permanently.

- Erny

---

### Post by ecowan on 2009-11-09
I just had to 'recycle' the libsane version on my server again.
That is, when I first brought up Xsane on my client, the 'scan source' list had only 'normal' and 'ADF front'. 'Transparency' was missing.
So, using my work around, I went ssh to my server, did a dpkg --force-downgrade to libsane..18.. followed by an apt-get install libsane to bring back libsane ...29....
Voila! Now I can see all options from my client.
- Erny

---

### Post by ecowan on 2009-11-20
A little more description.
It doesn't seem to matter which version of libsane I install. I can either force a downgrade to ...18... when I have ...19... installed, or vice-versa. It helps to do a reboot after the reinstall before I attempt to access the device.
Perhaps libsane gets out of sorts because the HP 8259 ScanJet goes into sleep mode after 40 minutes or so.
- Erny

---

### Post by ecowan on 2009-12-03
More symptoms - 

A better workaround to keep full functionality is to make sure that the scanner is awake and ready to work BEFORE trying to access it via xsane (or any other fron end) and libsane.

It seems that, once libsane tries to access the scanner while it is dozing, it wakes up grumpy and has a headache until reset properly, refusing to acknowledge that it has a Trancparency/slide reader or to operate the Automatic Document Feeder. Powering down and up the scanner and/or rebooting Ubuntu in various permutations that I have tried do not seem to restore it to good humour.

The most reliable recovery that I have found so far is to boot my server into Windows 2000 Pro and access the server using the HP software. When I go back to Ubuntu and libsane, all functions are restored, until next time.

I'd be glad to turn on debug or check logs, if someone could tell me exactly how or where. - Erny

---

