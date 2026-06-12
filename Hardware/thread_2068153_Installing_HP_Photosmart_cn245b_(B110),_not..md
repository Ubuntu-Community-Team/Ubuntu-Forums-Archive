---
title: "Installing HP Photosmart cn245b (B110), not."
date: 2012-10-08
forum: Hardware
---

### Post by grey1beard on 2012-10-08
Toshiba Satellite, hp photosmart B110, HPLIP 3.12.10

Following an earlier thread, I've installed the latest version of hplip, and am having problems getting through the last stages of adding the printer.
The HP Device Manager-Setup (page 1 of 3)shows USB, Network, or Wireless(with temp usb cable)
Choosing the last, clicking on Next opens another window - Device Manager - Wifi Configuration (page 2 of 5), where my printer is listed as the only one.

In the background, the Terminal window clocks these choices, but stalls with line "ValueError: need more than 1 value to unpack"

Selecting my new printer and clicking on the Next button (on page 2 of 5) has no effect. 
I've tried deleting all printers and re-tracing my steps, but the end result is the same, and therefore I am stuck.

Can anyone throw me a line ?
John

---

### Post by grey1beard on 2012-10-09
OK, so no help appearing yet, so I've started again, with the printer on.
Unplugged usb cable, deleted printer and re-booted.
Went to System/Admin/Printing, and clicked on Add/Printer.
When it showed the Add Device window, I clicked on Other, and after a few seconds, up popped the wireless printer.
Selected that, and hit the Forward button, and a few seconds later a new window for naming it, and printing a test page, and it worked !!!!!!!!!!!!!!!

I hope the above may help anyone with similar difficulties.
Allow time for the different stages to occur, and remember to highlight(select) the name of the printer at each new window, even if it's the only name there, before moving forward.

John

---

### Post by grey1beard on 2012-10-09
Bouyed up by earlier success, I have just upgraded the SWMBO's laptop to 11.04, and installed the printer onto hers.

Slight hiccup at the final hurdle though, and I'm not sure if I cleared it, or hplip did.
Although it's a wireless network, the last stage required that I should use a temp usb cable connection. This didn't work, just like my first problem, so I unplugged it, rebooted, and went once again via the #2, and this detected the printer OK.
Test page printed OK, so I can now go out into the garden and relax for a while(taking steaming cup of Arabica with me).

---

