---
title: "Scanner on AO1 problems"
date: 2009-05-27
forum: Hardware
---

### Post by taffydan on 2009-05-27
Running Ubuntu 9.04 with Xsane installed and apparently working.  Trying to scan from an HP J5780 AO1.  When trying to scan from the laptop, get message "Error during CMS conversion.  Could not open scanner ICM profile."  When trying to scan from the AO1 get message "No Scan Options.  Refer to device documentation to troubleshoot."  (Documentation, if any, on CDs for MS and Apple)  Any help appreciated.

---

### Post by ubigT on 2009-05-30
I get the same "Error during CMS conversion. Could not open scanner ICM profile." using Xsane and an HP psc 950.  Anyone have any ideas?


EDIT:
I have an idea!  Uncheck the color management: Preferences / Enable Color Management.

Worked for me.

---

### Post by MakisM1 on 2009-06-22
I have a netbook and loaded Jaunty (9.04) yesterday. I operate it through a home LAN which includes a network printer (HP OfficeJet L7780).

I loaded the HPLIP, found my printer, printed fine, but trying to scan I got the infamous (as I read here) ICM error.

I used the go-around "turn off the Color Management" and it worked.

In the process, trying to set up the XSANE I figured out that the problem was that the ICM profiles were missing!

If you launch XSANE and go

Preferences>Setup>Color Management

You will find that it expects you to specify 5 ICM profiles

A quick search found one (1) available in the whole file system!

It is in

/usr/share/ImageMagick-6.4.5/config/sRGB.icm

sRGB.icm being the filename.

I input, for the time being, this file for all 5 ICM profiles and enabled Color Management in the Preferences. It works fine.

My question to the more knowledgeable:

Where can I find ICM profiles for my printer? I would like the scanned image to be slightly more vivid.

Best regards

MakisM1

---

