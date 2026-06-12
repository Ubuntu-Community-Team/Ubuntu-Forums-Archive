---
title: "Brother MFC-7340 printer giving streaky lines/blank pages"
date: 2009-11-30
forum: Hardware
---

### Post by zmall88 on 2009-11-30
I correctly installed a brother MFC-7340 all-in-one laser printer according to the brother linux drivers website. The scanner is working fine and also the printer except that the page starts streaking usually on the 2nd/3rd page and every page after that comes out blank. I don't see this issue with the copier at all (I copied up to 10 pages with no problems), although after the printer starts streaking and gives blank pages, it messes up the toner so that when I try to copy, it gives blank pages. When this happens, I take out the toner and give it a good shake to have it work again.

Everything seems fine and dandy. The computer is connected, all the drivers are installed and the only problem is with this 2nd/3rd page fail. 

I am running 9.10 (karmic), 64-bit and the printer is connected via USB. I installed the cupswrapper and lpr drivers. I also followed the special instructions for 64-bit versions of ubuntu mentioned on the brother website.

Some details:
```
dpkg  -l  |  grep  Brother
ii  brmfc7340lpr                          2.0.2-1                                    Brother MFC-7340 LPR driver
ii  brscan-skey                           0.2.1-3                                    Brother Linux scanner S-KEY tool
ii  brscan3                               0.2.7-1                                    Brother Scanner Driver
ii  cupswrappermfc7340                    2.0.2-1                                    Brother MFC7340 CUPS wrapper driver

```Any help would be greatly appreciated as frustration is hitting the roof (and the junked paper pile is too).

---

### Post by zmall88 on 2009-11-30
bump

---

### Post by chaddcw on 2010-03-25
Did you ever get a solution to this? I'm having the same problem except the streaks start half way down the first page and often the top quarter of the first page is printed twice.

---

### Post by tom_d on 2010-04-08
I bought this printer with assurances that it works with ubuntu. So far I can't get it to work. does anyone have it working? is so, please post the steps to make it work.  thanks tom_d

---

### Post by chaddcw on 2010-04-30
I do have this working on an OpenSUSE machine.  The instructions provided by the Brother website worked fine.  As far as I can tell, the problem I was seeing with the blank pages/streaks was caused by a failed update of CUPS.  Only part of the CUPS system successfully updated during a system update (via YaST on OpenSUSE) because of network issues.  After fully updating CUPS and rebooting the OpenSUSE box the printer works fine.

---

### Post by Geriborg on 2010-06-16
I've had the same problem (sigh)! It seems to be linked to graphics (PDF graphics, web graphics, photos, etc.) as if the information was garbled to the printer, and it started printing out garbage. Printing straight text seems not to be a problem, sans graphics. Help would be appreciated.

---

### Post by shaw.sam on 2010-08-05
Any solutions to this problem yet? My dad just bought one of these and hooking it up to his Ubuntu PC (basically only ever uses internet & email) results in the issues being experienced here - streaky lines and blank pages.

Tried many different drivers and PPD files, same result.

---

### Post by jandriel on 2010-11-02
Same problem: either prints entirely blank pages, or prints a garbled first page and a continuing number of completely blank pages.

Sadly, this printer worked very well until I disconnected it to bring the system to another location for a week, then returned home.

---

### Post by AlphaZeta on 2010-12-03
I installed MFC-7340 as a network printer using CUPS a couple of weeks ago and I believe that changing the printing resolution to the highest solves the problem, at least for me it did. ([http://www.kerrywong.com/2010/11/23/brother-mfc-7340-setup-under-linux/](http://www.kerrywong.com/2010/11/23/brother-mfc-7340-setup-under-linux/))

---

### Post by kocur on 2011-01-23
I have actually very similar problem but with Brother DCP-7030 printer - [http://ubuntuforums.org/showthread.php?t=1673624#post10387522](http://ubuntuforums.org/showthread.php?t=1673624#post10387522) ...have you found the solution???

Highest resolutions doesn't solve the problem. 

Ps. It is interesting that my printer was working originally and then stopped however when connected to other Ubuntu it is working just fine ...

Thanks!

---

### Post by fbicknel on 2011-02-19
I printed using my MFS-7340 for about two months without any issues.  Today mine started doing this intermittently.  Most of the time, you get blank pages (until you press job cancel on the printer).  Even the self-test page from CUPS would usually print one whole test page, then another split with another half page, then blank pages "forever".

Sometimes you get the half page followed by the vertical streaks, followed by blank pages ad-tray-emptium.

The only thing that had happened recently was that I switched off the printer and moved it about 4 feet away for a time to deal with a new UPS.  When I replaced it, this started happening.

So after much googling with no positive result, and after re-installing the Brother lpr and cups drivers, I finally turned my attention to the printer itself.

Switch off the printer, open the front, remove the toner cartridge, replace it, shut all the doors and lids... and then it worked.  For one page.

When it happened again, I repeated the "fix".  Then in printed 2-1/2 pages, streaked the last half of that page and started printing blanks again.

I'm thinking bad printer??

Ok - one more time.  This time I decided to also clean the corona wire (see [Brother link]("http://solutions.brother.com/Library/pdf/all/alldcp_tn_us.pdf")).

That worked.  I printed several multi-page jobs after that with no issues.

Go figure.

Edit: Several weeks later and a lot of trying different things.  Still have the problem.

Brother support suggested trying from a different computer.  So I put my laptop next to it (10.10 - exactly the same drivers throughout) and I can print without issues from there.  I even set it up as a cups print server and printed from the original machine without issues.

Switch back to first machine and streaks and blank pages - usually first page, now.  

I tried a different USB port.

I tried sticking a USB hub in between the computer and the printer.

Nothing seems to work except a different computer.

---

### Post by andrefrisco on 2011-03-18
Hey everyone!

I had the problem with my MFC-7320: Blank pages and/or stripes that look like bar code when printing documents containing images. 

Seems I found the reason: I terminated the scan key tool. "brscan-skey -t" and printing works fine. Unfortunately I cannot use the scan key service anymore. Seems there is communication problem that makes the printer crash with scan key tool.. Bad :-(

Regards

andre

---

### Post by fbicknel on 2011-03-21
Excellent lead!  Thanks.

This explains why connecting a different host to the printer works - brscan-skey wasn't running on the other host.

Just went through an exercise this weekend of re-installing Ubuntu on a different drive.  Of course the printer works fine.  I started brscan-skey later on - guess I had better check whether it's working now or not.

Saved the other drive; I will boot it and turn of brscan-skey and observe.  It was misbehaving with regularity before I got desperate.

I'll pass this along to Brother, too.  I have a case open with them.

---

### Post by andrefrisco on 2011-03-21
Hope Brother will fix this. Let us know when you get a reply on this! Thanks.

---

### Post by fbicknel on 2011-03-22
Verified: brscan-skey on = garbled print.  brscan-skey off = perfect working order.

So that's the workaround and I'll report it to Brother.  If they come up with a fix, I'll be sure to post it here.

Thanks, andrefrisco for pinpointing the problem!

---

### Post by fbicknel on 2011-03-30
I'm afraid I have to report failure.  The upshot (and final message from Brother just today):

> 
Dear Brother Customer,  We have reviewed your request and although we can not offer you the  assistance you need, we suggest the following: try reinstalling the OS.  We apologize for any inconvenience you may have experienced.  Sincerely,    Customer Service Brother International Corporation 
They were not able to reproduce the problem and therefore assumed it is my problem, not theirs.  This despite many messages telling them I had already re-installed the OS (They kept harping on that.)

I'm a bit fed up with them, as you can imagine.

I guess I'll have to look into scanbuttond and hope that works.

Anyone have any further information on the topic?  

One bit of unfinished business I intend to try: I had modified the script that their brscan-skey utility calls to put multiple ADF-scanned images into a single pdf.  I'm going to try putting that back where it was and see if brscan-skey still gets in the way.

I will say it is nice to have the printer back - even without the scanner button working.  So thanks again for effectively providing a workaround, **andrefrisco**.

---

### Post by freechelmi on 2011-09-16
Same problem Here with a 7320. called brother France this morning, they answered : You should call a linux expert.

I told them they have a driver problem but as usual they just support linux not the same way they support other OSes....

but as it's installed on a server 10.04 we might use PhpSane to start the scan, but the Brkey was really a better solution.

---

### Post by heath_r on 2012-02-16
Similar problem with HL-2270DW...
printer worked every day for about a year...
then starts randomly printing garbage and/or blank pages.
Business situation, so I bought replacement printer, which does the same thing.

This using Ubuntu 10.10 64 bit, updates regularly.

---

### Post by plizzba on 2012-02-16
heath_r, you should try uninstalling brothers "scan-key-tool" package if it is installed. This fixed my problems. But because your problems appeared spontaneously, maybe there is a different source of the problem.

---

