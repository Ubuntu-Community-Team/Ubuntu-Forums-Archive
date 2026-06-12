---
title: "Ubuntu GPU underclocking"
date: 2008-08-04
forum: Hardware
---

### Post by another_sam on 2008-08-04
CPU underclocking will be very easy in Intrepid [http://brainstorm.ubuntu.com/idea/7392/](http://brainstorm.ubuntu.com/idea/7392/) , so now I think it is time to put the focus on GPU underclocking.

Here I will explain quickly how to do it for ATI and NVIDIA cards.

Caution: extreme underclocking may cause your system stop to respond, and extreme overclocking may cause your system blow up.



**For ATI cards**, I found [http://wiki.cchtml.com/index.php/Configuring](http://wiki.cchtml.com/index.php/Configuring) where it is explained you can run the next command to set the power state to the lowest.
```
aticonfig --set-powerstate=1
```

And run the next command to print information about power states.
```
aticonfig --lsp
```

I have an ATI Mobility Radeon X1400 and runs perfectly.



**For NVIDIA cards**, exists nvclock. I have not tested it, but according to the instructions in its man page, you should be able to get enough information on which working frequencies you want from this two commands:
```
nvclock -i
```
```
nvclock -s
```

And then set the desired frequencies with:
```
nvclock -n 300 -m 100
```
For example, if you want 300 MHz for core and 100 for memory.

---

