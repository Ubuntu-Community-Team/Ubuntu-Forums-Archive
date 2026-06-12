---
title: "Hp Deskjet F2280 series scanner not working"
date: 2008-08-30
forum: Hardware
---

### Post by coffeecups on 2008-08-30
Hello.... I am still fairly new to ubuntu and love it so far. Only I just purchased a HP deskjet F2280 series all in one printer scanner and copier, only a cheap piece of hardware yet works great apart from xsane can't detect the scanner. I went to the HP site and downloaded the linux drivers there yet still not able to get scanner working, it doesn't work from the console on the printer either!!? Any help would be much appreciated, Thanks:)

---

### Post by peterbrewer on 2008-09-09
Is the photo copy type function in the printer working, if not then there is a hardware problem.  Is it printing, if not have you run:
<code>sudo hp-setup</code>

Let me know how things progress.

---

### Post by pskipper on 2008-09-14
Okay, I've just bought the same printer. The version of HPLIP available through the add applications does not support the F2280.

First you need to downgrade python, all the explanations and a how to can be found on the link below..

[https://answers.launchpad.net/ubuntu/+question/41452](https://answers.launchpad.net/ubuntu/+question/41452)

You then need to install the latest version of HPLIP, again complete instructions from the link below..

[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

Follow the instructions and you'll have a fully working printer-scanner. The only thing which doesn't work is the scan button on the printer but XSane works perfectly.

Hope this helps people.

Philip

---

### Post by Visual_Noiz on 2008-10-03
Thank you it saved my life! :)

I have to add that I encountered a problem when running the script when it decided to run commands like "sudo aptitude install --assume-yes sane-utils", maybe because I have a general problem with timidity every time I do an update.

If you encounter something similar don't panic, just quit the script when asked to and copy-paste the failed command on the terminal and run it. Then run the script again. This manual workaround worked fine for me.

---

### Post by DaveinSpain on 2008-10-04
Hi.  Just bought an HP Deskjet F2280 but still can't get it to work (works fine in Windoze Vista so not hardware).  When I followed the instructions to downgrade python, the message I received was that the packages would be upgraded.  When I subsequently ran hpsetup, it could not detect the printer.  Trying to detect it manually was impossible as the input screen required a 3 digit decimal numbers and lsusb gave me 4-digit hexadecimal numbers which I could not enter.

Suggestions please?

Dave

---

### Post by Pandziura on 2008-12-19
Hello there. 
I've bought recently an All-in-One HP Deskjet F2280. I'm using Ubuntu 8.04 - Hardy Heron. I was quite stucked as I only managed to install an run perfectly the printer. Then I found with synaptic the package **hpoj**. In it's description you may read:
> **HP OfficeJet Linux driver (hpoj)**
This software provides Linux support for most "multi-function" (also known
as "all-in-one") peripherals from Hewlett-Packard, including OfficeJet,
LaserJet, Printer/Scanner/Copier ("PSC"), and PhotoSmart printer products.
...


And ***voilá***... It's running now. Just open **gimp** and Acquire a xsane Device Dialog.

[B]___________
*Pandziura*[/B]

---

### Post by MasT R&amp;R on 2009-03-24
> **Pandziura said:**
> Hello there. 
I've bought recently an All-in-One HP Deskjet F2280. I'm using Ubuntu 8.04 - Hardy Heron. I was quite stucked as I only managed to install an run perfectly the printer. Then I found with synaptic the package **hpoj**. In it's description you may read:


And ***voilá***... It's running now. Just open **gimp** and Acquire a xsane Device Dialog.

[B]___________
*Pandziura*[/B]

I've installed hpoj and tried to acquire an Xsane device Dialog, but it didn't find the scanner. Though it prints well.

---

### Post by dje on 2009-03-24
> **MasT R&R said:**
> I've installed hpoj and tried to acquire an Xsane device Dialog, but it didn't find the scanner. Though it prints well.

have you upgraded hplip? [http://hplipopensource.com/hplip-web/index.html]("http://hplipopensource.com/hplip-web/index.html")

dje

---

### Post by col48 on 2009-03-30
My problem with my F2280 was as described by pskipper (Sep 14 2008).

(Ubuntu 8.04)

The version of hplip in Synaptic was 2.8.2 and according to the hp website the printer needs 2.8.6 at least.

Downloading and installing the latest hplip (3.9.2) and adding hpoj from Synaptic (0.91-13) has cured the problem.  The installation took about 15 minutes.  I also needed to add gocr (Synaptic) for the optical character recognition to work.

I did not need to downgrade python as I did not have it installed in the first place.

Doing the scanning is via xsane in Terminal.

I too find the scan button on the printer does not work (the power button flashes for about 30 sec) but I'm happy.

Thanks to all contributors - I did not need to start a new thread!

---

### Post by Alex22 on 2009-10-19
Hi Guys!

I installed F2280 with automatic recognizing in my Ubuntu 9.04 (hplip was installed too, everything went smooth and easy, exact model- F2280 was detected.)

**And printin was great, until today i needed some scanning. It didn't go**.
So i did as Pandziura said, and installed **hpoj**. It replaced hplip and hpijs:

xxx@xxx-desktop:~$ dpkg -s hpijs|grep -i status
Status: purge ok not-installed

xxx@xxx-desktop:~$ dpkg -s hplip|grep -i status
Status: deinstall ok config-files

**And now, it's just opposite: scanning is fine, no prinitng**:

The message:
/usr/lib/cups/filter/foomatic-rip failed

Can You please help?

---

### Post by Alex22 on 2009-10-19
P.S. I read a little, and they say, normal driver for single-and multi function devices is **hplip**. **Hpijs** is just a patch to print with black cartridge instead of compositing colors for black-making (for printers, which firmware doesn't support it).

And **hpoj** is not recommended for CUPS printers. 
So what's goin on?

---

