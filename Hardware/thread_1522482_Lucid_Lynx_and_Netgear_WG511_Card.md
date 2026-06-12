---
title: "Lucid Lynx and Netgear WG511 Card"
date: 2010-07-02
forum: Hardware
---

### Post by thomas_roche@comcast.net on 2010-07-02
I recently upgraded to Ubuntu 10.04 (Lucid Lynx) but when the system rebooted, the Netgear WG511 wireless card no longer works (no lights, connection). This card worked fine on the previous install. Can anyone provide any info as to how to correct this and/or get it to work again? Thanks...

---

### Post by ajgreeny on 2010-07-02
Which WG511?   There are three versions, and one of them will only work with WEP encryption, not WPA.

I have version 2, with the marvel chipset, which is the one which only works with WEP, but as you say you had it working previously, I presume this is not your situation, unless you have changed your router settings.

---

### Post by thomas_roche@comcast.net on 2010-08-02
The card I have is the WG511 v2.0. Any ideas how to get this working again with Lucid Lynx?

---

### Post by jmkelly on 2010-11-01
Don't know if you've fixed it yourself yet, but I fixed this problem with ndiswrapper.

Get the driver from Netgear [URL="http://kbserver.netgear.com/products/wg511.asp"]http://kbserver.netgear.com/products/wg511.asp[/URL.] That's the hard part, you have to use a Windows box because the only way they ship it (AFAIK) is in a Windows executable. Note that there's more than one version of this card; make sure you pick the right one. Unzip the file you get from Netgear on a Windows box, extracting its files to a removable drive (floppy or USB or whatever). The one you need is netgw511.inf, it'll be in the Drivers folder.

Plug the removable drive into your Ubuntu box. Use the Synaptic Package Manager to install ndisgtk if you don't have it already. It'll automatically ask if you want to install other ndis* stuff, say yes.

Open a terminal window and type sudo ndisgtk. Give your sudo password. In the ndisgtk window, click on "Install New Driver", browse to the removable drive and select the driver. Your card should start working in a minute or less.

If you can't get hold of a Windows box to extract the zip file from Netgear, let me know and I'll email you the driver itself.

---

### Post by wookster on 2011-05-01
great tip - worked a treat. thanks.

---

### Post by calzakk on 2011-05-03
I'm confused - the download from the Netgear website is an installation executable.  You can unzip it, but it doesn't contain any .inf files.

---

