---
title: "Hardware compatibility: compact page and document scanners"
date: 2009-07-11
forum: Hardware
---

### Post by RonCam on 2009-07-11
I want to both move to Ubuntu and retain the ability to use a compact page or document scanner.  For example, I now use a Logitech Pagescan USB scanner more frequently than my flat bed scanner.  I never needed a driver as the scanner has native support from my present operating system (Windows 2000 Professional).  But, support terminates in a year, and I'm looking forward moving on ... (tux smilie here*)

As far as I can determine, Linux support for the Pagescan was attempted some years ago, but the project was never brought to completion.

If this is true, I'm willing to buy a new, reasonably-priced similar scanner and found the following counterparts of the Pagescan:
> Pentax DSmobile 600
IRIScan Express 2
RoadWarrior Sheet-fed Mobile Scanner
Xerox Travel Scanner 100
Plustex OpticSlim M12Plus
Genius Color Page SF600
With the exception of the Plustek ('miminal' SANE support -- not really I was hoping to find) could it possibly be true that none of the others will function with any Linux distro, including Ubuntu?  Have I failed to find some other brands or models with Linux drivers?

:confused: I must be missing something ... any advice (other than the obvious dual-boot) would be appreciated.

__________
* :shock: I can't believe -- a GNU/Linux site without a Tux smilie !!

---

### Post by RonCam on 2009-07-15
**[color="red"]*** bump ***[/color]**

Should I assume, then, from the lack of response, that :frown: there is ***no*** support in Ubuntu, either natively or through SANE, for this general type of single-pass, sheet-fed scanner (see image below and list above):
[IMG]http://i.i.com.com/cnwk.1d/sc/32176942-2-200-0.gif[/IMG]
Anyone have information to the contrary?  Is there another forum, more appropriate to this question?

If there's *really *no support for these scanners, I will have to so inform the folks at SANE and see what may be done.

---

### Post by desertdog on 2009-08-23
I have a page where I keep track of the small usb document scanners. [http://sites.google.com/site/roadwarriorscanner/](http://sites.google.com/site/roadwarriorscanner/). Also see [http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)

Your best bet is the Syscan Travelscan 464, which is usually branded by Ambir in the US. This scanner is no longer manufactured, but they come up used on ebay every couple of weeks. It (and its little brother the Travelscan 662) are completely supported, including calibration.

The Visioneer XP 200 also has complete support, including calibration. This was recently added, so you have to download the latest source code and compile from source. Also this scanner is a little larger than the others and is not usb powered.

The Pentax DS Mobile (not the DS Mobile 600) has a closed source linux driver that you can request from Pentax customer service.

There are closed source drivers for the docketport line of scanners. [http://www.docucap.com/](http://www.docucap.com/), but they are for resellers of these scanners. If you bug them enough, they will give them to you. 

Open source support for the Docketports is very basic (no calibration). 
Good luck.

---

### Post by RonCam on 2009-08-24
Thanks very much.  I was beginning to think a dual boot was the only solution.  Good to have this information on the forum, as I searched before posting and saw nothing.

If Linux users know about this, then we can make our buying decisions based on which manufacturers are willing to support our operating system  ...

After posting but before seeing your reply, I went ahead and bought the *Genius Color Page 600,* in the hope I could get it working.  They are available at extremely attractive prices ($80-90), and I expect are being sold in great numbers. 

I see the Genius products aren't on your site's list.  Anyone know if they have cross-compatibility with something that is?

The folks at SANE don't seem to have an interest in this category of scanner.  There's "minimal support" for one, the Plustek.  I was about to find out how to contact them and ask if the omission of this category is intentional, or unintentional.

---

### Post by RonCam on 2009-08-24
My Googling is improving.  

I found a reference to the Genius SF600 (image of same, in July 15 post) [in this document]("http://src.opensolaris.org/source/xref/sfw/usr/src/lib/sane-backends/sane-backends-1.0.19/backend/gt68xx_devices.c") on a SANE backend source for gt68xx_devices.  The document is dated 2007.

I assume this means I may have SANE support, but I now have to wonder if this has been dropped from the current version of SANE, since their website makes no mention of compatibility with Genius scanners.

---

### Post by desertdog on 2009-08-25
RonCam:
The Genius Colorpage 600 looks like it might be a clone of the Plustek Opticslim M12. Can you run $sane-find-scanner at the command line and report back the vendor id and the product id?

If it is the M12, there is partial support. [http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/) explains how to extract the firmware binary and where to put it on your linux box.

Edit:
Upon further investigation, this scanner is partially supported by the gt68xx sane backend. See above link on how to extract firmware file cism216.fw from windows driver and where to put it in your linux filesystem.

---

### Post by putt1ck on 2012-03-11
For anyone else coming across this thread looking for a manufacturer supported solution, Canon are claiming support (even in product descriptions!) for their new imageFORMULA P-150. Just purchased one, happy to provide feedback if requested - but official support should mean it works as advertised with a minimum of fuss (via SANE).

---

### Post by moallam on 2012-03-23
I just purchased a PlusTek Mobileoffice S400 (which, per PlusTek's website, replaces the OpticSlim M12 model) on the hopes that since it replaces a "basic" SANE-supported model, it would work out of the box. Unfortunately it didn't. 

Ironically the sane-find-scanner tool identifies the scanner. Here's the output

```
found USB scanner (vendor=0x07b3, product=0x0465, chip=GT-6816?) at libusb:006:005
```But it still, when trying to scanimage -L it returns

```

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```
Any help or clues on what can be done to get that model working on Ubuntu would be greatly appreciated.

Thanks a million

P.s. I'm not trying to hi-jack this thread. I thought keeping another related question here would help people in my and the OP's situation. Just saying!

---

