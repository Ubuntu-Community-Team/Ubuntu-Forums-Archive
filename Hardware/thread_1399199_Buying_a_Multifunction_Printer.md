---
title: "Buying a Multifunction Printer"
date: 2010-02-05
forum: Hardware
---

### Post by t1m on 2010-02-05
I need a multifunction printer. I've seen several Lexmarks and Brothers that seem to be supported in the [Open Printing Database]("http://www.linuxfoundation.org/collaborate/workgroups/openprinting").

The Database rated the Brother 7440N we just bought "perfect", but I did hassle a bit to set it up (hopefully solved now), and the Brother scanner driver didn't seem to work. Maybe I should persevere, but how hard must it be?

I tried searching the list of supported scanners ([HardwareSupportComponentsScanners]("https://wiki.ubuntu.com/HardwareSupportComponentsScanners")), but this seems incomplete and out of date.

Does anyone use a multifunction printer with Ubuntu? 
Is there a way to see the list of standard drivers that you see when you add a new printer in Ubuntu? (Those all seem to work flawlessly.) Any thoughts or ideas?

Thank you.

---

### Post by linux4life88 on 2010-02-05
HP does a good job with the Linux community:

[http://hplipopensource.com/hplip-web/index.html]("http://hplipopensource.com/hplip-web/index.html") (Home Page)
[http://hplipopensource.com/hplip-web/supported_devices/index.html]("http://hplipopensource.com/hplip-web/supported_devices/index.html") (Supported Printers)

I've had good luck with my multifunction HP C4180 under Linux, although this printer is very very outdated.

---

### Post by blur xc on 2010-02-05
> **t1m said:**
> I need a multifunction printer. I've seen several Lexmarks and Brothers that seem to be supported in the [Open Printing Database]("http://www.linuxfoundation.org/collaborate/workgroups/openprinting").

The Database rated the Brother 7440N we just bought "perfect", but I did hassle a bit to set it up (hopefully solved now), and the Brother scanner driver didn't seem to work. Maybe I should persevere, but how hard must it be?

I tried searching the list of supported scanners ([HardwareSupportComponentsScanners]("https://wiki.ubuntu.com/HardwareSupportComponentsScanners")), but this seems incomplete and out of date.

Does anyone use a multifunction printer with Ubuntu? 
Is there a way to see the list of standard drivers that you see when you add a new printer in Ubuntu? (Those all seem to work flawlessly.) Any thoughts or ideas?

Thank you.

I just purchased an HP OfficeJet 6500 Wireless and could not be any more satisfied with my purchase.

Getting on our home wireless network took under a minute- and that kind of depends how fast you can type in your encryption key in the network setup wizard.  Then I went to Ubuntu, selected add new printer in the printers dialog deal, select the printer from the list, hit next a couple of times and BAM.  Test page spit out, no problem.

Now, scanning was different.  On my desktop running 9.04, the wireless scanning didn't work right away, but it did on the laptops running 9.10.  Faxing from either computer did not work out of the box either...

So- I went the the [hplip website]("http://hplipopensource.com/hplip-web/index.html") and installed the latest version of hp-lip (I recommend you do this before adding the new printer, since you have to do it all over again anyway).  Installation takes a few minutes, but when done everything the printer can do can be accessed from the pc.  Faxing, scanning, ink levels, etc...  Everything works perfectly.

The printer works great is is fantastic w/ Ubuntu.

BM

---

### Post by t1m on 2010-02-07
Thanks for the ideas etc.

I did find out that HP supports Linux quite well. (Yay for them!) We ended up getting an HP LaserJet M1522nf. It's quite a nice printer (quick, quiet) and it works perfectly with Ubuntu, for us. (I have not tried faxing. The hp-setup program [see link below] said I couldn't do faxing from this computer or something.) I followed [these Ubuntu instructions]("https://help.ubuntu.com/community/HpAllInOne"). (I did have to change the printer's "location" in the Ubuntu printer settings because it's a netowork printer.)

Yay! :popcorn:

---

