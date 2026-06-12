---
title: "New motherboard (VIA K8M800 chip set)"
date: 2005-01-18
forum: Hardware &amp; Laptops
---

### Post by marcadams on 2005-01-18
Hi;
I am about to build a new PC, and was wondering about the compatiblity issues with Ubuntu. The main iissues will come from the 754 socket motherboard - thinking of getting a MSI K8MM-ILSR (has VIA K8M800 chipset). The issues will be ubuntu understanding:

1) Ingetrated graphics (S3 Graphics UniChrome)
2) SATA controller 
3) integrated ethanet
4) integrated sound card - Realtek ALC655

I expect Ubuntu will not find all these striaght away (although I really hopes it immediately finds the SATA hard drive!!), however, VIA does seem to have Linux drivers (main reason I chose this chip set). 

My question; these Linux drivers are for Red Hat, Mandrake, Fedora - how easy is it to convert these drivers and install onto Ubuntu?

EVEN better, has anybody used this motherboard or a simular motherboard with the same chipset?


Your help will be greatly appreciated!
Marc

---

### Post by merc on 2005-01-26
Hey, I have a motherboard with the same chipset. Everything on it works fine. SATA, Audio, Ethernet, USB. Haven't tried Firewire (I dont own any FW devices). I did read that the native video (S3 Chrome) is flaky under linux. Meaning it doesn't work other than in text mode or something. People were haiving problems with it. My mobo came with an AGP slot, so I just used an old Nvidia Geforce video card, and its working perfectly. 

So as far as I know, everything except the video works. And you dont need any extra drivers for the other things. Ubuntu autodetected everything by itself.

---

### Post by daniels on 2005-01-26
Unichrome is, um, interesting.  Support in Warty is not great (indeed, rather bad), but it's a lot better in Hoary.

---

### Post by Tomy on 2005-02-07
Last month Luc posted this on the unichrome mailing list.
  > 
 Daniel Stone told me that they are shipping the unichrome driver per default with their Xorg packages. This means that they will be in "hoary", the current development branch, which is bound to be released in april.
    location of the packages:
  [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/]("http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/")
  
  Luc Verhaegen.
 
 I have "hoary" installed. Does this mean that the "via" driver **is** the "unichrome" driver?
 
 thanks
 Tomy

---

### Post by daniels on 2005-02-08
Correct.

---

### Post by BLoTt0_AI on 2005-03-07
Strangely,  using hoary I still don't get the via module in my drivers dir. Whenever I try to start X, I get " via module not found". I'm using a dfi motherboard with k8m800 S3 unichrome pro graphics. Any ideas why that module would be missing? Same thing happens in Gentoo as well.

---

