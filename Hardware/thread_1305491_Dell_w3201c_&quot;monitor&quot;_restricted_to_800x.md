---
title: "Dell w3201c &quot;monitor&quot; restricted to 800x600 :-("
date: 2009-10-29
forum: Hardware
---

### Post by mobrien118 on 2009-10-29
Hi,

I just upgraded from Jaunty (where it worked) to Karmic and now my "monitor", which is a 37 inch "Dell w3201c" 1366x768 TV, is not properly detected.

In the past it has been VERY hit or miss, and at some point in time I tried random modelines and got it working with (I think) Hardy.

I neither remember how I did it, nor do I have the time to trial/error hundreds of modelines. Can anyone tell me how I may get this working again?

I made a backup of Jaunty, but I think I destroyed the backup during the upgrade, accidentally, so I am stuck here in 800x600.

Anyone have any ideas? Where to start?

Thanks!!!

--mobrien118

---

### Post by mobrien118 on 2009-10-30
OK, so I *sort of* have something going.

I'm very confused about how Ubuntu does graphics. Always have been.

So, I put these 2 lines into my "Monitor" section of my xorg.conf:

```
        Modeline "1360x768@75" 111.93 1360 1392 1816 1848 768 782 792 807
        Modeline "1360x768_75.00"  109.00  1360 1448 1584 1808  768 771 781 805 -hsync +vsync
```

Somehow, that makes the "option" for 1360x768 show up in my "Display" settings in Ubuntu. I have no idea which modeline it is using.

HOWEVER, (and this is how I was working in Jaunty) the TV thinks it is 1024x768. But when I tell it to fill the screen, I get a halfway decent picture at 1360x768. Some tweaking of the monitor settings (pixel clock, h and v scaling) and I get an OK picture, but in another distro I was actually able to get the monitor to know that it was getting 1360x768, and Auto Adjust worked then too. Is there any way to achieve that? What am I missing in my modeline?

Thanks to anyone who actually understands this stuff and can help!!!

--mobrien118

---

### Post by mobrien118 on 2009-10-30
Oh, also, there is a considerable amount of "flicker" that wasn't there before.

:-(

---

