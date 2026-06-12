---
title: "Canon Pixma Prints part of page then stops"
date: 2012-02-26
forum: Hardware
---

### Post by Paul A C on 2012-02-26
Set up Canon Pixma ip3600 Printer on Lubuntu 11:10 (using ip4600 driver which is the same except ip3600 does not support duplex).

On attempting to print test page, 27% of job is sent to printer (while printer cleans its head and generally wastes ink), Then the printer starts printing and another 2% of the page is sent.  Then no more of the page is sent.  The printer just hangs (green power light flashing).  All that is printed is the 'ubuntu' header.

I had the same printer set up on Lubuntu 10:4, and it worked fine.

My suspicion is that it is a problem with USB support rather than the printer driver/sub-system itself.  Anyone have any idea how to test this?

One thing I have considered is to try to get the Printer files from Canon and use these, but I don't want to waste ages trying this if this is not likely to be the issue.

---

### Post by aikishugyo on 2012-02-26
> **Paul A C said:**
> Set up Canon Pixma ip3600 Printer on Lubuntu 11:10 (using ip4600 driver which is the same except ip3600 does not support duplex).

On attempting to print test page, 27% of job is sent to printer (while printer cleans its head and generally wastes ink), Then the printer starts printing and another 2% of the page is sent.  Then no more of the page is sent.  The printer just hangs (green power light flashing).  All that is printed is the 'ubuntu' header.

I had the same printer set up on Lubuntu 10:4, and it worked fine.

My suspicion is that it is a problem with USB support rather than the printer driver/sub-system itself.  Anyone have any idea how to test this?

What about the gutenprint drivers? The iP3600 is nothing like the iP4600, so it is no wonder IMO that the printer cannot understand the printjob intended for an iP4600.

---

### Post by Paul A C on 2012-02-27
> **aikishugyo said:**
> What about the gutenprint drivers? The iP3600 is nothing like the iP4600, so it is no wonder IMO that the printer cannot understand the printjob intended for an iP4600.

Thanks for your comments:-

1.) What do you mean by the gutenprint drivers?  The driver I installed is the canon ip4600 CUPS+Guttenprintv5.2.7 driver from the standard Linux install.  Is there another one?  If so, where do I find it, how do I install/use it?

2.) The IP3600 & IP4600 are virtually identical printers (see [http://www.photographyblog.com/news/canon_pixma_ip4600_and_ip3600/](http://www.photographyblog.com/news/canon_pixma_ip4600_and_ip3600/) for example).  The linux suggested driver is the one for the ip3000 which **is not** of the same type (it uses a different print head).  I confirm that the ip4600 driver can work for the ip3600 printer because that is what I am using on my Lubuntu 10.4 PC.  My question is, why does the driver not work on the Lubuntu 11.10 install?

In the mean time, I'll keep digging, but anyone who has any ideas that will save me time, please shout.

---

### Post by Paul A C on 2012-02-28
2 more attempts, and 2 more failures:-

1.) Copied the PPD file from working PC, (Ver5.25) and installed printer using this PPD file.  Test print, nothing printed at all.  Knew I was pushing my luck this way, so the 'proper' way:-

2.) Downloaded ip3600 driver pack from Canon UK, and unpacked the .tar.

2 files resulted:-
i) cnijfilter-common-3.00-1_i386.deb Double clicked to run package installer, but failed due to broken dependencies.  Tried the -f option to fix, but only able to remove package completely.
How can I get this to install with the necessary dependencies?
ii)cnijfilter-ip3600series-3.00-1_i386.deb  Not much point doing anything here till I get the 'common' installed.

---

### Post by Rodney9 on 2012-03-01
Try this -

[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Paul A C on 2012-03-01
Thanks Rodney,

This simple set of instructions certainly did the trick, and the driver here gives more options than the old one I had using the ip4600 driver.

Still waiting to see if I can persuade the printer to use the photo black ink when printing photos, that is something I have never managed with Canon printers on Linux 'yet'.

---

### Post by Paul A C on 2012-03-06
Spoke too soon, installed driver using the method Rodney suggested > sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update

sudo apt-get install cnijfilter-ip3600series
2 problems noted so far.

i) Unable to select paper source, well not quite true, I can select rear feed, but paper is selected from the cassette irrespective, makes it pretty well impossible to print envelopes

ii) Sometimes the job is printed 2 or 3 times, even though copies is definitely set to 1.  Is this a ploy of Canon to use up their (expensive) ink?

So for now using the ip4600 driver installed on Lubuntu 10.4.  

Anyone got any ideas how to find a driver that will work properly for 11:10?  Or to fix the issues I am having with the one I tried here.

Will have a bit of time at the weekend to try out a few options.  But won't be able to run 10.4 for ever so need a solution eventually.  Help appreciated.  (Should I **buy** Turoprint...anyone used that?)

---

### Post by aikishugyo on 2012-03-09
> **Paul A C said:**
> ... won't be able to run 10.4 for ever so need a solution eventually.  Help appreciated.  (Should I **buy** Turoprint...anyone used that?)

You could definitely try gutenprint. If the versions of gutenprint between 10.04 and 11.10 differ, that would explain why your use of the iP4600 driver does not work any longer.

In older versions of gutenprint there was only one mode, and it happened to be the same mode for each printer, which meant that if the printer supported that mode, you could use a variety of drivers for one model.
However, adding support for more commands used in the Canon ESC/P2-type protocol means the printers gradually became more different. Also, addition of other modes is printer-specific.

You should try the 5.2.8pre1 release of gutenprint and see what the iP3600 driver does for you. And report back on the gutenprint mailing list or sourceforge site for bugs or support requests.

---

### Post by Paul A C on 2012-03-09
Aikishugyo what do you mean use Guttenprint?  The drive I have says it is  'canon ip4600 CUPS+Guttenprintv5.2.7', so to me that looks like a Guttenprint driver.

Today things seem to have gone from bad to worse, since my 10.4 installation does not seem to have started the CUPS print server either.

Seems Printing is still a bit of an achillies heel in Linux.  Would hate to have to resort to Windows just to be able to print!

---

### Post by aikishugyo on 2012-05-04
> **Paul A C said:**
> Aikishugyo what do you mean use Guttenprint?  The drive I have says it is  'canon ip4600 CUPS+Guttenprintv5.2.7', so to me that looks like a Guttenprint driver.

Today things seem to have gone from bad to worse, since my 10.4 installation does not seem to have started the CUPS print server either.

Seems Printing is still a bit of an achillies heel in Linux.  Would hate to have to resort to Windows just to be able to print!

The gutenprint driver for the iP4600 in 5.2.7 is not correct (number of inks is incorrect) so it does not work either for the iP4600 it is intended for. However, the incorrect driver is in fact (inkwise) correct for the iP3600. This explains why you can possibly print with the 5.2.7 driver (in 5.2.7 there is no driver for the iP3600).
However, in the development code (released as 5.2.8-pre1 in December 2011) the iP4600 driver is corrected---so no longer works for the iP3600 even by accident---while aniP3600 driver was added.

Regards,
Gernot

---

### Post by Paul A C on 2012-05-04
Thanks for clearing that up.

I have found on the CUPS forum that the problem with not being able to select trays is a general CUPS issue.  If anyone is interested I'll try to locate it and link it here.

Still no updated CUPS that resolves the issue so far though

---

