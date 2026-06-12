---
title: "HP C6180 Printer invokes but not the fax"
date: 2009-11-27
forum: Hardware
---

### Post by FredVanH on 2009-11-27
Hi.  On my newly installed Ubuntu 9.10 via Live CD, I just installed my HP Photosmart C6180 all-in-one.  It seemed to go forward without a hitch.  When I go to print a document out of Writer, in the Print dialog the C6180 printer shows up as the default and only device choice upon which to print.

In my previous installation of this device using Windows Vista, C6180 FAX was also a(n installed) choice.  Anyone know how to get that (fax) part installed?

The computer is connected to the router via an ethernet cable.  The C6180 is connected to the router via wireless.

Thanks,
Fred

---

### Post by Ralph L on 2009-12-06
I am having a similar problem.  I can't find anyway to specify Fax during printer setup.  I have both my computer and printer on a wifi network.  Under Jaunty I just powered up my all in one clicked the New button and it discovered the c6180 and brought up a window where I could select printer or fax.  

On Karmic it searched for a long time and finally brought up a different window that gave me a choice of LPT #1, Serial Port #1, Other, and Network Printer.  I selected Network Printer and found my C6180 listed.  I selected it and configured the printer, which worked fine. However, I tried the New button again and this time it couldn't even find the c6180.

Any help would be appreciated!!!

Ralph

---

### Post by Ralph L on 2009-12-08
I found the answer.  Searched the web and found there was a bug in the Karmic distributed hplip [https://bugs.launchpad.net/hplip/+bug/407079](https://bugs.launchpad.net/hplip/+bug/407079) .  Downloaded and installed hplip-3.9.10 from [http://hplipopensource.com/](http://hplipopensource.com/).  Followed the directions on that web site.  At the end of the installation it brought up a wizard.  Under Device Discovery I selected Network/Ethernet/Wireless (direct connection or JetDirect).  Clicked Next.  It found my C6180.  Clicked Next.  Window came up to configure both a printer and a fax.  Entered names and clicked Add Printer.  

Ralph

---

### Post by FredVanH on 2010-02-12
Thanks, Ralph L, for finding the answer!  I downloaded and installed hplip-3.9.12 and it installed both printer & fax just as you said.  However, when I went to "print" a Writer document to HP C6180 FAX, after I hit "Print", I got a quick dialog saying it was printing to the fax;  but nothing happened.  In fact, it had not even asked me for the phone number I wanted to fax to.  Any ideas?
Thanks,
Fred

---

### Post by FredVanH on 2010-02-12
I'm embarassed to say that I rebooted and now it works fine - I get both devices available and working on any print dialog.  Thanks again, Ralph.  The reason it took me 2 months to get back to the forum to see your solution was that this thread was my first post and I just assumed (erroneously) that the forum automatically sent emails upon new posts.  I just discovered that that's not the case and am currently working on finding out how to request that option.  Thanks, Fred

---

