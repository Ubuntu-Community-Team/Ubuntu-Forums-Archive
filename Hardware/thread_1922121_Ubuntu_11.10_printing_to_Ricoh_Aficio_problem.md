---
title: "Ubuntu 11.10 printing to Ricoh Aficio problem"
date: 2012-02-08
forum: Hardware
---

### Post by evan54 on 2012-02-08
Hi,

I'm trying to print to a Ricoh Aficio printer, my OS is Ubuntu 11.10 on a Sony laptop.

When I connect it it all seems ok, in the sense the printer appears on the printer list and is recognised as the correct model.

However when I send a test page the folllowing occurs.

Instead of printing a test page it prints the following text:

"CUPS PrintTestPage"

not sure why this is happening... Any help would be much appreciated.

best

---

### Post by NeoDarin on 2012-04-18
I'm having similar issues with a Ricoh Aficio MP C3500 printer.
My sys: 2.2Ghz, 3.7GB Memory, 64-bit Ubuntu 11.10

I installed the driver from [http://www.openprinting.org/printer/Ricoh/Ricoh-Aficio_MP_C3500](http://www.openprinting.org/printer/Ricoh/Ricoh-Aficio_MP_C3500)

The printer prints the following:

%!PS-Adobe-3.0
%% %%
mark
() () (201204181028) {setuserinfo} stopped
cleartomark
%%%!

Then prints an infinite loop of blank pages until I cancel the job.

At least you are getting a test page printed, how did you get that far?

---

### Post by NeoDarin on 2012-04-18
Sry the printed output somehow got a smiley face in it.

Correct output should be:

%!PS-Adobe-3.0
%%  %%
mark
()  ()  (201204181028) {setuserinfo} stopped
cleartomark

---

### Post by marche9320 on 2012-05-12
I have the same problem as well, similar output from Ubuntu 11.04.  looks like no one has made any headway here

---

### Post by suokunlong on 2012-05-20
I had the same problem but I solved this by doing the flowing:

when setting up the printer, DO NOT select the recommended driver ( Ricoh 3045 PS), select the driver named **Ricoh 3045 PXL** instead.

I have tried and it works fine with the PXL driver.

---

