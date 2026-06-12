---
title: "Video Card questions for dual monitor setup!!"
date: 2009-03-14
forum: Hardware
---

### Post by swoody on 2009-03-14
Well, I finally did it. I just ordered two 24" monitors. I'm going to be setting them up on my main rig, which only has one slot for a video card (currently taken up by my nVidia 8600GT) I don't do any real hardcore gaming, or graphic-intensive work, I'm mostly going to be using this computer for the internet, word processing, watching movies, running small games, etc. This is the exact card I have:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814127341R&nm_mc=OTC-RSS](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127341R&nm_mc=OTC-RSS)

My first question is, can I run the dual monitors from this card? I don't know whether it supports it or not, since it only has one VGA and one DVI hookup. So physically I can connect two monitors, but will this work? Will this card be enough to handle the load?

If I can't do it with my current card, then that leads me to my next question - What video card would you guys recommend to get? I want to try and keep this as cheap as possible, as I just laid out $450 for the monitors (and my fiancée isn't going to be very happy :D) but I want to have something that will power the monitors without me having to worry if they're going to lag if I do use a graphic-intensive program in the future.

Please let me know what you guys think! ANY and all help is greatly appreciated :)

---

### Post by swoody on 2009-03-14
Ok, well I found some hopeful advice. I spoke with someone that also has an 8600 with one VGA connection, and one DVI, and he just got his dual-monitor system setup sucsessfully. Now, how do I go about doing this? I've never tried to hook up multiple monitors before, so ANY advice would be great! :D

Also, I was hoping that someone else could also verify that they have done this before? Either one VGA monitor, and one DVI monitor, or someone who has used the same card??

---

### Post by Nevart on 2009-07-15
I really hope you have not been sitting around for 4 months waiting for a reply!  But if you haven't solved the problem yet, you just need to get a VGA/DVI converter to plug the 2nd VGA monitor into a DVI socket. They cost about $10 and any decent computer shop should have them.

---

### Post by swoody on 2009-07-15
Oh, well thanks for the reply Nevart :)
I've been waiting months to hear back about this... jk ;)

No, I've moved on since then, and am currently running dual 9800GX2's, so there's no problem in powering 2 (or even 4) monitors :)

---

### Post by gradinaruvasile on 2009-07-15
It should work. I just stopped the computer (Nvidia Quadro NVS 285 card), plugged in the second monitor, run

```
gksudo nvidia-settings
```

In a terminal, configured my second monitor for TwinView, clicked apply, Save to x configuration file. Thats all. Maybe reboot. But do not forget to click "save to x configuration file". And be sure u run as root with gksudo as i posted above.

The vga and dvi links make no difference afaik, its a dual head card if it has 2 video outs so it works with 2 monitors.

---

