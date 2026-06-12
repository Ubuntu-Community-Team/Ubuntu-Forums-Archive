---
title: "loading wlan-ng modules??"
date: 2004-10-24
forum: Hardware &amp; Laptops
---

### Post by senectus on 2004-10-24
I have just used synaptic to install the wlan-ng drivers for my laptops inbuilt prism2 wireless, how do I make the system load the drivers?

---

### Post by sfw5000 on 2004-10-25
To start with, have you tried installing and activating your card through teh GUI. Go to Computer--> System Config --> Networking and click the ADD+ button. Many people can get it up and running through there. Post back your results.

Sam

---

### Post by senectus on 2005-02-12
I'm now running Hoary on that laptop..

Its very strange.. when I ran the live CD I had working wireless... for at least 35-45 mins..

Then I installed hoary and now wireless doesn't work.. in exactly the same way that wireless didn't work in warty..

It load the three modules:
orinoco
orinoco_pci
hermes

for the wireless.. the eth0 comes up for about 30 seconds then drops again (I also  noticed that it calls the device a "Prism I" when its actually a "prism2.5").
I can get the same result by loading just the orinoco_pci module, but I get nada if I load the other two on their own.

I had the p80211 module from wlan-ng loaded and working under warty for a few days.. but then it stopped working completely.. and now I can't get it to work under the current setup.

:-( 
I miss my wireless.. does anyone have any idea how to make a PCI laptop prism2.5 work?

---

