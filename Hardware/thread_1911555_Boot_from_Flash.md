---
title: "Boot from Flash"
date: 2012-01-19
forum: Hardware
---

### Post by forrestcarter on 2012-01-19
I just found a CompactFlash>IDE chip today in a server I am not using.  I'm assuming that this will allow me to use a CF card as a hard drive.  Would I get any sort of speed increase while booting if I used this in my desktop?  And if so, what all would I have to install on the drive, just my Boot directory, or /usr/ as well?  Please forgive me for not knowing this already, I've been a desktop linux user for about 10 years but never really got into the internals of linux before just recently.

---

### Post by jerrrys on 2012-01-20
Why don't you just stick it in and see what happens next.  Maybe ubuntu will automatically recognize it.  If not recognize; open a terminal and enter:

lspci

It should show up there.  This is a PCI card right?  If this is a USB plugin, the command would be:  lsusb

That I think would be the first step, but i don't own one so this is just my guess.  Good luck

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=CF+card+as+a+hard+drive&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=CF+card+as+a+hard+drive&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=CF+card&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=CF+card&sa=Search&cof=FORID:9)

---

### Post by C.S.Cameron on 2012-01-21
Try the USB Startup Disk Creator to make a Live CF card.
Your bios may recognize it as a hard disk.

---

