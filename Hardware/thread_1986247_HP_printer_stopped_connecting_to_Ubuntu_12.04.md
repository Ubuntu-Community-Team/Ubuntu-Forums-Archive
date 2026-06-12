---
title: "HP printer stopped connecting to Ubuntu 12.04"
date: 2012-05-24
forum: Hardware
---

### Post by Roz Omid on 2012-05-24
Hello and Thank you for this forum;

I had a basic problem with the printer set up before.  I updated to Ubuntu 12 and now that it has been two or three weeks later I can't print.  

In the system setup/printer I deleted all printers and added a new one.  Everything went well and I even printed a test print with all the circles and colors but no more after that.  I can't print a basic document.  

The little printer icon no longer shows up on the top right corner next to volume and battery gage icons so I can delete the job that is not wanting to print.

I called HP since it is a HP Deskjet 1000 but they said they don't have the drivers for Ubuntu (whatever drivers are.)

Can anyone tell me how to fix this please?

---

### Post by fantab on 2012-05-24
Install HPLIP.

 ```
$ sudo apt-get install hplip 
$ sudo apt-get install hplip-gui

```
Configure your printer using hplip. More often than not your printer should work.

---

### Post by Linux_junkie on 2012-05-24
Without knowing exactly what you've done its difficult to help you.  However, after you had deleted your previous printer setup and installed a new printer you need to check that the new set up is set to default.  Also you can check the print settings in your apps to make sure that they are "pointing" to the new printer.

---

### Post by Roz Omid on 2012-05-25
Thank you for your replies.  This morning I was able to print two pages; one an hour ago and one just now. 
Yesterday I restarted the computer twice.
It must have done the set up as default by itself this morning or a miracle happned after I updated the new things that Ubuntu asked me if I wanted to update.
Ubuntu is the best.

---

### Post by mapes12 on 2012-05-25
I had a problem with a HP all in one printer last week. The standard HPLIP package in the repos didn't seem to work. So I hopped over the the HP website to get the latest version:-

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

If the run file downloads to your Download folder drag it onto your Desktop then follow the HP script instructions word for word. My printer now works perfectly.

---

### Post by Guilden_NL on 2012-05-25
Mapes12, the latest version of HPLIP does correct a nice selection of known bugs. If you choose the "download and install firmware" option if offered, it will also take care of known bugs in the various printers that are identified to require new firmware.

Since I am caught up in the 30,000 HP employees being retired early or laid off, I almost made a snarky comment about HP, :-k but will leave it with confirmation that Mapes12's answer is spot on. 

A lot of good Linux people at HP are caught up in the layoffs, so when you need to replace those HP printers, here are two good sources to see who else supports Linux: 
[http://www.linux-drivers.org/printer_scanner.html]("http://www.linux-drivers.org/printer_scanner.html")
[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters")

---

### Post by Rex Bouwense on 2012-05-25
Sorry to hear about your layoff.  I just added my HP printer to my Lubuntu 12.04 install.  I downloaded HPLIP and installed it and now my printer works like it did in 11.10 and 11.04 and 10.04 etc.   HP printers almost always work.

---

### Post by Guilden_NL on 2012-05-25
Rex,
You said "download" so I interpret that as off of the HP Open Source site which is the best place to get it from.  

In the case of HPLIP, it makes sense not to use the Ubuntu repositories as they lag quite a bit and there has been constant work on fixing known bugs.

Thanks for your thoughts. I started a consulting company and three of us are already booked through the end of 2012. No sense of sitting around whining about my situation. 
"Ain't no rest for the wicked!" :p


PS, ping me if you are RV'ing through the Phoenix area anytime. I'll buy you a Dark Roasted Ubuntu coffee at the local (not Dutch) coffeehouse. :)

---

