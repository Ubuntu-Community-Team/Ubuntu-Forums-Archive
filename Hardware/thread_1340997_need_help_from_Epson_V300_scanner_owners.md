---
title: "need help from Epson V300 scanner owners"
date: 2009-11-29
forum: Hardware
---

### Post by bob12564 on 2009-11-29
I just bought the Perfection V300 Photo scanner based on its support for Linux and for slides and transparencies.  The Avasys drivers installed easily and I was up and running in less than 5 minutes.

Now that I've had time to play with it, I've noticed the limitations of the Image Scan software.  Windows users get automatic dust removal and color restoration but I don't see it in the Linux version.  Does it exist?

Also, I am disappointed with the XSANE compatibility.  From what I've read, it seems that SANE is supported by the Epkowa back end and it is very limited.  For example, it doesn't support the transparency unit.  Also when I use the XSANE plugin to the GIMP, all I get is a blank preview window.  The mouse is functional in the window but there's no image.  Regular scanning with XSANE also seems hit or miss and it's hard to get OCR to work decently unless the scan resolution is greater than 600 dpi.  Image Scan seems to work much better in all cases.

I'm feeling disappointed.  I expected all the Windows features and better SANE support.  Many V300 owners seem to have done well with it and I'm hoping that I'm just using it incorrectly.  Can anyone help?

Many thanks.

---

### Post by bailout on 2009-12-06
Hi Bob, Can't help with your problem. I have just installed my v300 and it is scanning prints fine in iscan and skanlite but won't scan transparancies at all. I wasn't sure from from your message whether you have got it to do so in iscan? I know you say it doesn't work in xsane.

---

### Post by bob12564 on 2009-12-06
It scans transparencies fine in iscan.  After days of reading I found at least one other person stating that the transparency unit does not work in SANE.  Are you having a software issue or hardware?  Remember that you have to remove the white panel on the door to expose the transparency lighting array.

Since we're not getting much help from the community here, I'll tell you what I've been able to conclude on my own.  Most manufacturers that support Linux work within SANE.  Epson, for some reason, prefers to remain proprietary and it provides a 2-prong approach.  Full support is available through their Image Scan software.  However, there is also limited support through the Epkowa backend of SANE.  SANE gives more features but they're not fully supported for the V300.  No support for the transparency unit is one example.  SANE has advantages over Image Scan.  SANE can also produce postcript files and Image Scan cannot.  That's important if you're trying to use the scanner with fax software like Efag-gtk which requires postscript.  And XSANE can invoke OCR.

I've discovered that XSANE and Image Scan can also interfere with each other.  You'll notice that when Image Scan is running or was running during the current session, XSANE may not give you a preview window.  It seems to work if you start XSANE first and let it be the one to initialize the scanner.  Once Image Scan is started, XSANE gets flaky.  

Otherwise, all I did was to download the two deb packages on Avasys for Ubuntu and double click them.  The installation worked perfectly and I was up and running in no time.  

I hope this helps.

---

### Post by bailout on 2009-12-06
> **bob12564 said:**
>  Remember that you have to remove the white panel on the door to expose the transparency lighting array.


#-o:oops: You were right. I actually found this out when I booted into windows to test it and the windows epson app helpfully gives an error message saying to check that. In my defence I haven't used the scanner for a while and only ever did about one slide scan to test it.

Having removed the panel it scans slides in iscan and also skanlite and xsane. I only ran one app at a time and didn't try running it as a plugin but other than that didn't do anything special. However, I didn't like the results from xsane scanning a slide. It was too bright even with the auto adjustment turned off.

I bought the scanner to digitise a mixed collection of both prints and slides and have been very impressed with its scans of prints but less so with slides/negs.

---

