---
title: "Cannon MP600"
date: 2011-04-01
forum: Hardware
---

### Post by Jonny87 on 2011-04-01
My dad is running Ubuntu 10:10 and has a Cannon MP600 that he's trying to get working. We couldn't find the driver in the list, the closest that we could find was for the MP610 so we tried installing it. It printed the test page but he said it was like it was printing out of line and out of proportion etc.  Does anyone know a way round this? Is there perhaps a printer equivalent to ndiswrapper to use a Windows driver?

---

### Post by IcarusR on 2011-04-02
Drivers for printer & scanner are available in rpm format on canon asia site here, you will need to use alien to convert to deb format.
[http://support-in.canon-asia.com/P/search?model=PIXMA+MP600&menu=download&filter=0&tagname=g_os&g_os=Linux]("http://support-in.canon-asia.com/P/search?model=PIXMA+MP600&menu=download&filter=0&tagname=g_os&g_os=Linux")

Failing that people say that MP500 driver works well.

If you google or search forum you will find info on this printer.

Scanner is supported by sane & should work.

---

### Post by Jonny87 on 2011-04-02
> **IcarusR said:**
> Drivers for printer & scanner are available in rpm format on canon asia site here, you will need to use alien to convert to deb format.
[http://support-in.canon-asia.com/P/search?model=PIXMA+MP600&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-in.canon-asia.com/P/search?model=PIXMA+MP600&menu=download&filter=0&tagname=g_os&g_os=Linux)

Failing that people say that MP500 driver works well.

If you google or search forum you will find info on this printer.

Scanner is supported by sane & should work.

Thanks for the tip, last time we tried the rpm from the Cannon site and converting it to deb, my Dad said that the printer stopped working all together. I'll get him to try the MP500 driver and see how that goes. If that doesn't work I'll try the rpm - deb thing again. 

Just out of curiosity (this might be why it didn't work last time) but when you use alien to convert from rpm to deb, does it have to be on the computer that your doing it for or does it not matter?

---

### Post by IcarusR on 2011-04-03
> Just out of curiosity (this might be why it didn't work last time) but when you use alien to convert from rpm to deb, does it have to be on the computer that your doing it for or does it not matter? 

No it doesn't have to be on the box you are running alien from, could be on a local server, but it would be best on same box.
Either ways you will have to give alien the exact location of it ie

```
alien /home/fred/Desktop/file_to_convert.rpm
```

Alien defaults to converting to .deb see man page

```
man alien
```

---

### Post by kkruecke on 2011-10-24
I found [URL="http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html"] helpful.

I Removed the printer I had installed as mp600. Then did

>     sudo add-apt-repository ppa:michael-gruz/canon
    sudo apt-get update
    sudo apt-get install cnijfilter-mp600series

It seems to be working fine.

---

### Post by daveman67 on 2011-10-29
> **kkruecke said:**
> I found [URL="http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html"] helpful.

I Removed the printer I had installed as mp600. Then did



It seems to be working fine.


Thanks very much. After the 11.10 upgrade, I had similar out-of-line printing problems with my canon MP600. Using these drivers fixed it.

Dave

---

