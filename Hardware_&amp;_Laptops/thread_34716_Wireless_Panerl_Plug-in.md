---
title: "Wireless Panerl Plug-in"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by ddocta on 2005-05-16
I have been searching for a good wireless plugin to add to the GNOMe Panel to monitor my wireless card and the signal.  None seem to be included by default and I couldn't find one on apt-get.  Any suggestions?

---

### Post by daenney on 2005-05-16
[QUOTE=ddocta]I have been searching for a good wireless plugin to add to the GNOMe Panel to monitor my wireless card and the signal. None seem to be included by default and I couldn't find one on apt-get. Any suggestions?[/QUOTE]
 The plug-in you're probably looking for is GKrellM.
Open up System > Administration > Synaptic Package Manager and search for wireless.
There you'll find wireless-tools which is marked green, meaning it is installed (u need it anyway, otherwise u can't get a wireless connection up with WEP etc...) and mark the GKrellM plugin for installation. Synaptic will tell you gkrellm-common needs to be installed to. Accept and hit Apply to install GKrellM

If you want to use console:
sudo apt-get install gkrellm

it will tell you it also needs to download gkrellm-common. Just hit "y" and then enter and it will do the job for you

---

### Post by ddocta on 2005-05-16
[QUOTE=daenney]The plug-in you're probably looking for is GKrellM.
Open up System > Administration > Synaptic Package Manager and search for wireless.
There you'll find wireless-tools which is marked green, meaning it is installed (u need it anyway, otherwise u can't get a wireless connection up with WEP etc...) and mark the GKrellM plugin for installation. Synaptic will tell you gkrellm-common needs to be installed to. Accept and hit Apply to install GKrellM

If you want to use console:
sudo apt-get install gkrellm

it will tell you it also needs to download gkrellm-common. Just hit "y" and then enter and it will do the job for you[/QUOTE]

Actually I already installed the grellm and the wireless package looking for a monitor.  I am actually looking for something to put in my panel though, the gkrellm is not for the GNOME panel.

---

### Post by daenney on 2005-05-16
Right click on GNOME Panel > Add to Panel > Network Monitor
Maybe that's what you're looking for...

---

### Post by ddocta on 2005-05-17
Yeah, that seemed to do it.  I had added it before but was sure it didn't recognize my wireless card and didn't show signal strenghth.  Either I missed it ot somehow updated it but it works fine now.

---

