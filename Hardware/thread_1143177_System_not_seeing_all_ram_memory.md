---
title: "System not seeing all ram memory"
date: 2009-04-29
forum: Hardware
---

### Post by marcelofontenele on 2009-04-29
Hi everybody, 

I'am a Jaunty user. My mobo it's gigabyte and i have  two memo modules, one of 1 Gb and other o 2 Gb. When i hit the command [COLOR="Red"]**free**[/COLOR] i had the following result:
```

             total       used       free     shared    buffers     cached
Mem:       **[COLOR="Red"]2578320[/COLOR]**     485732    2092588          0      17336     209936
-/+ buffers/cache:     258460    2319860
Swap:       995988          0     995988
```

Below system monitor print:

[IMG]https://sites.google.com/site/joaomarcelofn/Home/system.png[/IMG]

So, during the boot, the memory count shows over 3gb, but ubuntu only give me 2.57 Gb. Anyone knows how to fix this.

Thanks

Marcelo

---

### Post by HankB on 2009-04-29
Hi Marcelo,
Are you running a 32 bit kernel? With 32 bits, the most memory that the processor can address is 4GB. However video memory and other I/O also needs to use some of that space. That is could be the reason you don't see all 3 GB of your RAM.

You can get around this by installing a server kernel which can use additional processor facilities to access more RAM. If your processor supports 64 bit execution, you can install the 64bit architecture.

HTH,
hank

---

### Post by marcelofontenele on 2009-05-01
Hi Hank,

Thanks for the tip. Today i made the installation of 64 bit version of ubuntu 9.04 and now i have 3gb of ram memory available. First time using 64 bit system and i think it is, for the moment, better than 32 bit. Firefox it's  working real great as i never seen using sites with flash content (processor use issues).

See ya,

Marcelo

---

