---
title: "Scanner Output Not Correct"
date: 2016-09-12
forum: Hardware
---

### Post by wagb278 on 2016-09-12
My scanner is not producing white background for color documents.  Do I need a new scanner? Advice please.
My Epson V200 Photo scanner is about eight years old. The scanner functions correctly - I use Simple Scan in Ubuntu MATE 16.04 LTS (64-bit). I suspect the lamp is not working as when it was new; but I don't know much about scanners - just how to use mine.
Attached PDF is a scanner output with nothing on the scanner bed.  You can notice the expected blank white output is tinted. Scanning black & white document does not produce the tinted background that I can notice.  Scanning a photograph in color renders what appears to be correct colors on the photo; at least to my eyes. The non-photo area of the scan does show the tinted background. 
Am I seeing the results of an aging lamp thus my only option is to get a new scanner?
Thanks for any advice.

---

### Post by DuckHook on 2016-09-12
What you are seeing is Simple Scan (the app itself) auto-adjusting for both brightness and contrast in an effort to find enough contrast to differentiate text from background. This is why your text scans give you a pretty good white background whereas a blank page does not. Apps are designed to be pretty intelligent these days and they try to automatically give the highest contrast in order to render text clearly. The grey is an artifact produced when the app tries for contrast that simply isn't there.

You can reduce the grey background in colour docs (like photos) by choosing "Photo" in your menu options. It's under File&#8594;Scan&#8594;Photo. You can also monkey around with the brightness and contrast settings inside the "Preferences" menu, but this may screw up your colour balance for future scans. Try to scan colour docs as "Photos" and just don't worry about blank pages. You will truly appreciate the intelligent auto-adjust feature the first time you try scanning a page of text that has very faint lettering.

---

### Post by wagb278 on 2016-09-13
Thanks DuckHook,
You could be right, but how do I correct the scanner not producing the color white where it should?
I tried using a couple of other scanner software applications (gscan2pdf and XSane) and get similar results. 
I included a couple of test result files scanned using Simple Scan and gscan2pdf. Both result in non-white background. 
Scanning a blank (white) page gives results similar to the test of no page in the scanner (white source does not produce white scan output).
Scanning a printer test page (printed on my inkjet printer) gives reasonably accurate color where colors are produced but non-white background where it should be white. 
Using the Simple Scan Text option still produces monochrome scans with acceptable white background.
I am reasonably sure the scanner produced good white background when the scanner was new, thus I suspect the bulb has aged and is probably the cause.  Contacting Epson they say the scanner bulb is not replaceable.  
Is there a way to calibrate colors?
Is a new scanner the best option for me?

---

### Post by him610 on 2016-09-13
wagb278,,

Recommend you go to a photography shop, or online store to get a color wheel that you can scan and then use to compare with the scan results to get an idea how much, or little fidelity  the scanner produces. Then you can go forward with decision as to replace or not. Lamps tend to yellow as they age. 

BTW, I have a fifteen year old Epson Perfection 1640 that has lost nothing over the years. Of course, I always take good care of my equipment and keep it covered when not in use. It has also been stored and operated in an environment of 70-75F ambient temperature since I have owned it.

---

### Post by DuckHook on 2016-09-13
> **wagb278 said:**
> …I included a couple of test result files scanned using Simple Scan and gscan2pdf. Both result in non-white background.I see what you mean. This is not just the typical greyish background that I get when scanning a blank page.> 
Scanning a blank (white) page gives results similar to the test of no page in the scanner (white source does not produce white scan output).
Scanning a printer test page (printed on my inkjet printer) gives reasonably accurate color where colors are produced but non-white background where it should be white. 
Using the Simple Scan Text option still produces monochrome scans with acceptable white background.
I am reasonably sure the scanner produced good white background when the scanner was new, thus I suspect the bulb has aged and is probably the cause.I am beginning to agree with you. The problem may very well be the bulb in your aging scanner. I do like *him610's* suggestion, though. Getting a colour wheel to establish colour fidelity is an excellent idea (thanks him610!). Only you can judge if it's too much trouble or if it's a worthwhile test before springing for another scanner.> Is there a way to calibrate colors?I use only Simple Scan, so can only speak to that app. I know that in Simple Scan there is only "Brightness", "Contrast" and a catch-all "Quality" setting that can be adjusted. There is no colour calibration setting. There is a general "Device Colour Profiles" that is available through "System Settings", but I have never tried defining device colour profiles using this service. My colour needs are simple and the defaults have always been good enough for me. However, if you can find a device colour profile for your scanner, this might help.> Is a new scanner the best option for me?I'm always somewhat reluctant to recommend new equipment because I'm a stubborn cuss who likes to revitalize old stuff and take pride in getting it working. But sometimes, especially when quality is important, such an attitude is just not practical. I can't advise you one way or the other on this question. The answer is too dependant on your personal circumstances, importance of colour fidelity, and your tolerance for infidelity.

A few other diagnostics you can try:

[LIST=1]
[*]Do you have a Windows/Apple box? If so, how does the scanner behave with another OS?
[*]Can you take your scanner to a friend's place and try it with Windows/Apple?
[*]Is there a colour calibration setting in the Epson driver? Since I do not have such a scanner, am only going by guess and by golly, but some drivers have an associated management app and you may be able to calibrate from there. Epson's driver site for your scanner is [here]("http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?oid=88043&infoType=Downloads&platform=OSF_O_LINUX").
[/LIST]

---

### Post by wagb278 on 2016-09-15
Thanks for the suggestions,
I decided to purchase a new flatbed scanner.  I ordered one that uses LED lamps that will hopefully last longer that eight years of my occasional use.

---

### Post by DuckHook on 2016-09-15
> **wagb278 said:**
> Thanks for the suggestions,
I decided to purchase a new flatbed scanner.  I ordered one that uses LED lamps that will hopefully last longer that eight years of my occasional use.I totally get that. Just saw one advertised at Best Buy for US$50. Sometimes, it just isn't worth wasting any more time on.

Good luck and Happy Ubuntu-ing!

---

