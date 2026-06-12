---
title: "Toshiba laptop.. atheros card.. no wireless"
date: 2009-02-13
forum: Hardware
---

### Post by JZeFF on 2009-02-13
I got my laptop about a month ago, just yesterday i decided to put a ubuntu 8.10 partition on it.

I can not get the wireless to work.  Under System/admin/hardware drivers
The atheros drivers are enabled... i just can not figure out how to get it to search for wireless networks or anything..

Any advice...   I did some searching and couldnt find the right answer

---

### Post by Mangledbmx on 2009-02-13
im assuming you have the atheros 5006 or 5007 card, those seem to give people the most problems. you need to install and use the madwifi drivers. just do a search for your wireless card model and you should come up with some how to's

---

### Post by JZeFF on 2009-02-16
i just checked and its the Atheros AR5007EG.

Does that help much?

---

### Post by SnowRider on 2009-02-17
[http://ubuntuforums.org/showthread.php?t=865971&highlight=madwifi](http://ubuntuforums.org/showthread.php?t=865971&highlight=madwifi)   chili555 has a good how-to on this link. Hope it helps.

---

### Post by binbash on 2009-02-17
sorry wrong thread

---

### Post by JZeFF on 2009-02-17
i followed this..

[http://ubuntuforums.org/showthread.php?t=798485&highlight=madwifi+drivers+atheros](http://ubuntuforums.org/showthread.php?t=798485&highlight=madwifi+drivers+atheros)

it still doesnt work... should i have the restricted drivers activated or deactivated?

---

### Post by deadd on 2009-03-09
Hi,
I also purchased a Toshiba laptop from the blue major elelectronics chain store in January 2009.  Since it had an Atheros wireless chip, I installed madwifi per above mentioned thread.  It worked fine, only I don't really have a wireless connection, only a wired one, so I turned it off after a few days of using wireless at a friend's house.  A week ago, I went back to his house and I turned on my wireless, but it stopped working.  Other than to uninstall and reinstall madwifi, what options do I have?  Any advice is greatly appreciated.

---

### Post by stchman on 2009-03-09
> **JZeFF said:**
> I got my laptop about a month ago, just yesterday i decided to put a ubuntu 8.10 partition on it.

I can not get the wireless to work.  Under System/admin/hardware drivers
The atheros drivers are enabled... i just can not figure out how to get it to search for wireless networks or anything..

Any advice...   I did some searching and couldnt find the right answer

Post an lspci output here in this thread.

Also, I believe that the Atheros wireless card in the Aspire One is the same.

I have a tutorial for getting that to work in Ubuntu.

[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)

Comment out the portion about getting the wireless LEDs working.  These are Aspire One specific.

The script basically does is compiles the 0.10.5.6 madwifi drivers gotten from:

[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)

It then installs the driver into the kernel and adds the module to the /etc/modules file.

---

### Post by stchman on 2009-03-09
> **deadd said:**
> Hi,
I also purchased a Toshiba laptop from the blue major elelectronics chain store in January 2009.  Since it had an Atheros wireless chip, I installed madwifi per above mentioned thread.  It worked fine, only I don't really have a wireless connection, only a wired one, so I turned it off after a few days of using wireless at a friend's house.  A week ago, I went back to his house and I turned on my wireless, but it stopped working.  Other than to uninstall and reinstall madwifi, what options do I have?  Any advice is greatly appreciated.

Sounds like your kernel got updated.  If you built the drivers then you will need to remake them and reinstall them.  This is usually a simple process.

---

### Post by deadd on 2009-03-11
> **stchman said:**
> Sounds like your kernel got updated.  If you built the drivers then you will need to remake them and reinstall them.  This is usually a simple process.

Thanks.  I forgot that madwifi was a manual install for me, unlike most of my other programs are through the add/remove software interface.

---

