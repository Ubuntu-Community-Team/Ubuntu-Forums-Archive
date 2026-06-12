---
title: "HP Wireless Driver Help Needed"
date: 2008-09-18
forum: General Help
---

### Post by Retyred on 2008-09-18
I just bought a new HP Pavilion S3421P Slimline Desktop with Windows Vista installed - needless to say Vista had to go, so I installed ubuntu - everything went smoothly and all the drivers were found except for the wireless adaptor - HP reports it as a "Lite On" USB 802.11b/g wireless adaptor - after searching and only finding Vista drivers for this adaptor I decided to seek help in finding a driver that might work - at this time I can connect via hardwire but might need to connect wireless in the future and not be able to because of this driver - any help out there would be greatly appreciated.

Thanks

---

### Post by leef on 2008-09-18
If I were you I would do "lspci -nn" and find the wireless adapter in that list, you should get out put similar to this;

02:00.0 Network controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [[COLOR="Red"]11ab:4364[/COLOR]] (rev 20)

and then enter the number highlighted in red into a search engine like google using quotes to see what drivers others have been using for this card. if you don't get any results I would give ndiswrapper a try with the windows drivers.

---

