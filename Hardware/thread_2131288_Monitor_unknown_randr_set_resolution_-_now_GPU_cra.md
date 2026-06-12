---
title: "Monitor unknown: randr set resolution - now GPU crash reports"
date: 2013-04-01
forum: Hardware
---

### Post by chessnut007 on 2013-04-01
Hi,

I have the following tv which I am using as a monitor - connected via vga cable:-
DGM 22 inch screen

[http://www.digimate.com/en/productDetail.asp?prod=520](http://www.digimate.com/en/productDetail.asp?prod=520)

The monitor is unknown according to ubuntu 12.10

I therefore manually set the resolution to get higher than 1024*768 (4:3) to get 1368*768 

Contained in a script:-

[I]xrandr --newmode "1366x768_60.00"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1366x768_60.00 
xrandr --output VGA1 --mode 1366x768_60.00

This works - however now the system regularly crashes and reports GPU crash. 



[/I]I have a samsung rv520 laptop with intel built in vga graphics card.

Please can someone offer me some advice?

Thanks

---

