---
title: "Ubuntu 64bit"
date: 2008-07-08
forum: Hardware
---

### Post by EmyrB on 2008-07-08
Hi All,

I thought I'd throw this out to the community and see what responses I will get. I am retiring my trusty Athlon 64 3000+ which has 1.5GB of RAM and a 256MB nVidia GeForce 6200 AGP GFX card for a Athlon 64 X2 4800, 2GB of DDR2 800 RAM and a nVidia Geforce 8400GS PCI-E.

My first question is will Ubuntu 8.04.1 support this hardware? I have done a quick search and it seems the 8400GS has given some people headaches.

My second question is should I run pure 64bit or a hybrid 32/64bit like Mac OS, or should I stick with 32bit?

The programs I use on a regular basis are : -

Thunderbird
Firefox
Amarok
Scribus
Gimp
Inkscape
VLC
Azuerus
Aria Download Manager
FSpot
Last FM
Brasero
Virtual Box
Wine
Compiz
AWN

I also have Doom3 installed and I have to put my hand up and say that I use Wine for both WoW and Guild Wars.

Any feedback would be greatly appreciated (even if its to say go forth and multiply ;) )

Cheers

EmyrB

---

### Post by pofigster on 2008-07-08
64-bit doesn't have the greatest driver support or Flash-support.  Unless you're planning on installing 4+ gigs of RAM, I'd stick with 32 bit since the only real advantage of 64 bit is better memory addressing, which at 2gigs isn't an issue.

---

### Post by stchman on 2008-07-08
> **pofigster said:**
> 64-bit doesn't have the greatest driver support or Flash-support.  Unless you're planning on installing 4+ gigs of RAM, I'd stick with 32 bit since the only real advantage of 64 bit is better memory addressing, which at 2gigs isn't an issue.

64 bit the drivers work just the same.  For 64 bit Ubuntu the drivers are in the kernel just like 32 bit.  If your hardware works OOB with 32 bit then it will with 64 bit.

As far as Flash, Flash 9 works just the same in 64 bit.  I have 3 machines running 64 bit and Flash works well on all of them.

Java is another matter.  The SUN Java browser plugin does not have a 364 bit counterpart.  You can use OpenJDK or Icedtea.

```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin

```

Everything else functions well.  32 bit apps will run on 64 bit OS.  Nearly all the debs in the repos have a 64 bit couterpart.  The gDesklets package does not function but Screenlets work.

If you have a 64 bit processor use 64 bit Hardy.

---

### Post by stchman on 2008-07-08
> **EmyrB said:**
> Hi All,

I thought I'd throw this out to the community and see what responses I will get. I am retiring my trusty Athlon 64 3000+ which has 1.5GB of RAM and a 256MB nVidia GeForce 6200 AGP GFX card for a Athlon 64 X2 4800, 2GB of DDR2 800 RAM and a nVidia Geforce 8400GS PCI-E.

My first question is will Ubuntu 8.04.1 support this hardware? I have done a quick search and it seems the 8400GS has given some people headaches.

My second question is should I run pure 64bit or a hybrid 32/64bit like Mac OS, or should I stick with 32bit?

The programs I use on a regular basis are : -

Thunderbird
Firefox
Amarok
Scribus
Gimp
Inkscape
VLC
Azuerus
Aria Download Manager
FSpot
Last FM
Brasero
Virtual Box
Wine
Compiz
AWN

I also have Doom3 installed and I have to put my hand up and say that I use Wine for both WoW and Guild Wars.

Any feedback would be greatly appreciated (even if its to say go forth and multiply ;) )

Cheers

EmyrB

As long as that software is in the repos it will work with 64 bit.

What mobo, chipset, ethernet will the new system have?  The 8400 will work with restricted driver install.

Don't count on WINE playing all your Windows games.  People often look to Linux as a free Windows which is not true.  If WINE runs the game great, if not then that is how it is.  My recommendation is to dual boot for your games.

Too often people judge Linux solely on how well it runs Windows programs.  That is complete BS.  How many Linux programs does Windows run?  If you have a huge need for Windows software then run Windows.

---

### Post by EmyrB on 2008-07-09
Thanks guys for the feedback so I am safe to run 64 bit Ubuntu. :)

As for the motherboard it will either be an MSI K9VGM-V or ASUS M2N-MX SE Plus.

The Windows Games is not an issue, as I don't mind dual booting into Windows if I need a gaming fix. I was just at a loose end and decided to see what would work and what would not.

As I have been 100% Linux now for about 2 years I have got used to the Linux Apps for my day to day computer use. I don't really care about Windows Apps compatibility. If only there was a Linux version of Quicken I would dump WINE.

Cheers

EmyrB

---

### Post by EmyrB on 2008-07-14
Just so you all know I updated my hardware and installed Hardy 8.04.1 64 bit and I am now enjoying life on the 64 bit side. Just as a side note, Wine also installed the 32 bit libs, and I happily reinstalled Quicken which works like a charm :)

Thanks for all you support

---

