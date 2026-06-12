---
title: "Dual Default Printer Setup. Is it possible???"
date: 2020-09-17
forum: Hardware
---

### Post by suomalainen on 2020-09-17
Hello Everyone!!!!

I have the need for a dual printer setup in order to meet a business workflow requirement.

_**WORKFLOW**_

We receive incoming customer orders through our cloud service. When we process an order an address label is immediately printed on a 4X6 inch label and placed on the package. The printer is connected directly to the PC via USB.

Next, an instruction sheet containing specific information relating to the purchase is also printed. This is printed on 8.5X11 inch paper. This printer is a network printer connected via WiFi.

Both documents are printed from a PDF file that opens in the web browser (Firefox/Chrome)


When I move from printing a 4X6 label to printing the 8.5X11 instruction sheet I must always change the printer in print settings. It shall be obvious to the user that this burns time, labor and resources unnecessarily.

_**QUESTION**_

Is it possible to print 4X6 PDF documents automatically from the label printer and 8.5X11 documents from the network printer? If so, how is this achieved?


_**What I have tried already**_

One work around I did try, and was hoping very much would work, was the e-service offered by HP. As many will be aware HP offers a service whereby an e-print enabled HP printer can be assigned an email address. Whenever a PDF document is e-mailed to this printer it will print automatically.

The problem we faced was that the documents were held at the mercy of the Internet and slowed down the workflow process. The other problem is that there appears to be no job queue that can be accessed online and jobs deleted as needed. Nonetheless, it was cool having a button on the admin dashboard. Simply clicking it would sent the print request to HP to automatically print on our network printer.

I look forward to your replies and learning other methods I can try to lick this once and for all.

Thank you,

Suomalainen

---

### Post by oldfred on 2020-09-17
Found this:
[https://stackoverflow.com/questions/42781944/preview-a-pdf-file-and-choose-printer-before-actually-printing-the-document](https://stackoverflow.com/questions/42781944/preview-a-pdf-file-and-choose-printer-before-actually-printing-the-document)

I use python3 and a browser (pyqtwebengine) in it. I then script change of web sites and add some local info to screen. But it requires a bit of python programming, using a code editor ( I use geany) and I use Qt5 to create screens.  You then could choose printer & make other changes.

Do you even have to open pdf with browser?

[https://apple.stackexchange.com/questions/276248/how-to-choose-printer-from-command-line-or-from-a-python-application](https://apple.stackexchange.com/questions/276248/how-to-choose-printer-from-command-line-or-from-a-python-application)
[https://gist.github.com/mutaku/1928574](https://gist.github.com/mutaku/1928574)

---

### Post by suomalainen on 2020-09-17
As I mentioned, I process customer orders via the cloud. As such pdf's open in the browser. I just don't want to have to keep changing the printer all the time. It would be better that labels print from dedicated label printer and instructions from dedicated network printer.

No I have saved a bunch of time and money! :) Yea!!!!!!

---

### Post by TheFu on 2020-09-23
If it was me, I'd save bth types of files to the downloads directory, then run a script - 1 printing to each printer.  his is trivial using **lp** and a different target. 
How to determine which file is for which printer?  Perhaps the sizes or you could just control the filenames used.
```
lp -d laser-prn  file1.pdf
lp -d label-prn  file2.pdf
```

Simple once the printers are defined in CUPS.
I once had to setup 6K printers across about 30 servers. Our paid admins claimed it would require years of effort.  I wrote a script in 2 hrs that accomplished it that day. 

> Use the script, Luke.

---

