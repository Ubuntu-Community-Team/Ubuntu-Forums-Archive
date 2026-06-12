---
title: "memory&amp;cpu leak after upgrade to Karmic?"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by tombrus on 2009-10-31
After upgrading to Karmic I noticed my CPU to be busy all the time.
After some investigation I noticed that ***at-spi-registryd*** and ***dbus-daemon*** are both nibbling away around 20%-30% of my CPU power.
Furthermore I noticed that ***indicator-messages*** and ***at-spi-registryd*** are using serious amounts of memory and are continuously asking for more. I would say they are leaking memory.

Here are two ***top*** snippets a few minutes appart:
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                         
 2390 tom       20   0  [COLOR="DarkOrange"]947m[/COLOR] 816m 4644 R   [COLOR="DarkRed"]27[/COLOR] [COLOR="DarkRed"]20.6[/COLOR] 180:22.92 at-spi-registry                                 
 1870 tom       20   0 66856  40m  640 R   [COLOR="DarkRed"]22[/COLOR]  1.0 334:54.50 dbus-daemon                                     
 2806 tom       20   0  [COLOR="DarkOrange"]541m[/COLOR] 481m 2756 S    5 [COLOR="DarkRed"]12.2[/COLOR]  78:26.65 indicator-messa                                 

```
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                         
 2390 tom       20   0  [COLOR="DarkOrange"]963m[/COLOR] 832m 4640 S   28 21.0 185:30.41 at-spi-registry                                 
 1870 tom       20   0 66856  40m  640 S   25  1.0 339:10.95 dbus-daemon                                     
 2806 tom       20   0  [COLOR="DarkOrange"]545m[/COLOR] 486m 2756 S    6 12.3  79:21.98 indicator-messa                                 

```

[LIST]
[*]Is this the general experience?
[*]Is there a bug for this already?
[*]Does anybody know a workaround?
[/LIST]

I can work with my machine alright, but if I leave it running for too long (and I tend to leave it running indefinitely) it will probably eat itself through all the available memory :(. So I am forced to restart every so many days (like you have (had?) to do with windose ;))

-Tom

---

### Post by macogw on 2009-10-31
at-spi-registry is the Accessibility stuff. If you don't need a screen-reader or anything like that, disable it in umm...(I use Kubuntu so I'm trying to remember where it is in Ubuntu)...System ->Prefrences ->Accessibility Tools

---

### Post by tombrus on 2009-10-31
Great, thanks, that solves some of the burden (maybe all, I'll post an update here when my machine ran for several days...). 

BTW: it is in **System|Preferences|Startup Applications**: unselect the ***AT SPI Registry Wrapper***. Or is there a more advanced way to do this?

But this still is a problem for them that need accessibility things, right?

Why is this on by default? I assume most people do not need it...

-Tom

---

### Post by cyberkost on 2010-02-22
Yeah, but indicator-messages keeps leaking memory (and eating CPU).  9.15% of 4GB on my Karmic Koala @ uptime of 3d3h :(

---

