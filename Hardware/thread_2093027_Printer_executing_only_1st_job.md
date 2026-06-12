---
title: "Printer executing only 1st job"
date: 2012-12-09
forum: Hardware
---

### Post by sapog on 2012-12-09
Hello, I've got a problem: my printer executes only first job after it was seen by system. For example if I turn computer on it will print one document (>= 2 pages), but next it won't. Print test page is also behaving so. After rebooting computer or printer (unplug & plug back) it can execute only 1 job again. But system says job is done, on the Kubuntu side everything looks like ok, but no pages are printed.

Count on I'm newbie to linux systems (installed less than a week ago), so maybe I did something wrong... because a couple of days before (as I remember) it worked normally. Printer: Samsung SCX-4220.

---

### Post by prconnor@gmail.com on 2012-12-09
I'm having similar issues printing on USB with Samsung ML-285ND from lubuntu.  After installing a driver the first print job works correctly.  Subsequent print jobs are all nonsense characters, page after page of double sided nonsense filling printable extent of the page.  Replacing the driver allows me print one job again.

This behavior is new since installing lubuntu.  I had previously printed without issue from Ubuntu from the same computer by USB with no issues.

---

### Post by prconnor@gmail.com on 2012-12-10
Seems like I found a solution in installing a driver from the Samsung website:

[http://www.samsung.com/us/support/owners/product/ML-2851ND/XAA?tabContent=content2#](http://www.samsung.com/us/support/owners/product/ML-2851ND/XAA?tabContent=content2#)

All tests so far seem to work correctly although I have only printed a few times.  Likely there is a printer driver for your model on the Samsung website also.  Executing the "autorun" file in the archive installed a cups driver without issue on my box.

---

