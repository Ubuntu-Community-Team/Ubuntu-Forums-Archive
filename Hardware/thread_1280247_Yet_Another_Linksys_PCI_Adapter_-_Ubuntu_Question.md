---
title: "Yet Another Linksys PCI Adapter - Ubuntu Question"
date: 2009-10-01
forum: Hardware
---

### Post by Vietminh on 2009-10-01
I -just- installed my very first ubuntu (9.04) this morning. I naively assumed that the linksys WRT54GS v1.1 pci adapter would be easily installed with the linksys disc. Of course, I was wrong. :P

I have searched through the forums diligently and have even consulted the wifidocs. I have installed ndisgtk and ndiswrapper. I have installed the necessary driver but when i check it through ndiswrapper's windows wireless drivers a pop up box comes up and says "unable to see hardware"; when i click ok, the box disappears and shows the window and wrt54gs driver hardware: yes.

I have blacklisted the b43s like [wifi docs says]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and have put the .sys and .inf in the same directory. 

My networks all show disabled when i run -c network. Ubuntu isnt reading any wireless networks at all. 

I am eager to get started and any help is greatly appreciated!! :smile:

---

### Post by cariboo on 2009-10-01
It would help if you posted the output of:

```
sudo lshw -C network
```

---

