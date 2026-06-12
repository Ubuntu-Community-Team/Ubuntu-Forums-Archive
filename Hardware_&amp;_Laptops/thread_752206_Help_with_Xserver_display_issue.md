---
title: "Help with Xserver display issue"
date: 2008-04-11
forum: Hardware &amp; Laptops
---

### Post by dubi0us on 2008-04-11
Hi there,

I'm brand spanking new to Linux let alone Ubuntu. There is a program that I really want to run and it only works in Linux at the moment hence the reason for me starting with it. Anyway, on to my problem and I hope this is the correct place to post this.

I have an older version of Ubuntu (v 5.10) that my dad got some time ago. I just got a new PC about 4 weeks ago with system specs as follows:

MSI K9A2 CF mobo
AMD Athlon 64 x2 4800+ at 2.5GHz
2GB DDRll 800
Sapphire ATI Radeon x1950 GT PCI-E x16 (latest Catalyst drivers for Windows)
(hopefully that is enough info)

I will be running Ubuntu in VMware as I need to be able to use my Windows OS as well. However that's not my problem.
I inserted the Live CD just to check Ubuntu out and get the feel for it before I install VMware and get it all running properly but I keep encountering an error with both the PC and 64bit 5.10.

It's something to do with the display not being configured properly and I cant see exactly what the error says because the display goes funny. I believe it is my display card though. Is this because my card is a relatively recent card (released mid 2007) and the version I have is too old? I have ordered the latest version but it's 6weeks to wait and I cant wait that long so I thought I would get started so long.

Also it's not detecting the onboard Ethernet adapter on my motherboard. Its a Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC.

So is it just because it's old or is there something else the matter and will it do this if installed instead of run off of Live CD?

Thanks

---

### Post by Crafty Kisses on 2008-04-12
For your display issue, you might want to try reconfiguring X, you can do that by doing the following:
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions as best as you can.

For your Realtek issues, you might want to see if they offer Linux drivers. [http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PNid=8&PFid=10&Level=4&Conn=3](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PNid=8&PFid=10&Level=4&Conn=3)

---

