---
title: "Ubuntu on a Gateway NV4405H"
date: 2009-10-20
forum: Hardware
---

### Post by charding on 2009-10-20
Has anyone installed ubuntu on this laptop? 

[http://www.futureshop.ca/catalog/proddetail.asp?sku_id=0665000FS10129068&catid=25313&logon=&langid=EN](http://www.futureshop.ca/catalog/proddetail.asp?sku_id=0665000FS10129068&catid=25313&logon=&langid=EN)

I'm considering buying it, but I don't want to get it if there is going to be a lot of problems.

---

### Post by Dark_Stang on 2009-10-21
My only concern would be the wireless card. Other than that it looks fine. Gateway's website offers no information on it and futureshop doesn't post exactly what kind of card it is. Can you get into a shop and check device manager to see what it is? If it's intel you're golden.

---

### Post by charding on 2009-10-30
I checked this laptop and the wireless card is a:

Atheros AR5B91

It seems from a post I found that this card is covered as a kernel driver..

---

### Post by nosoupforyou on 2009-11-13
I'm looking at this laptop too, has anyone tried enabling compiz or effects with kwin on it yet?

I also saw this acer unit which seems just as good but with AMD/ATI chips instead of intel but I'm not sure how well they would work with ubuntu. [http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10131714&catid=#](http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10131714&catid=#)

---

### Post by doundounba on 2009-12-18
> **charding said:**
> Has anyone installed ubuntu on this laptop? 

[http://www.futureshop.ca/catalog/proddetail.asp?sku_id=0665000FS10129068&catid=25313&logon=&langid=EN](http://www.futureshop.ca/catalog/proddetail.asp?sku_id=0665000FS10129068&catid=25313&logon=&langid=EN)

I'm considering buying it, but I don't want to get it if there is going to be a lot of problems.

My current experience using Kubuntu 9.10, 64bit:

- No wireless *or* wired connectivity.
- No screen brightness adjustments.

There seems to be some known problems ([link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/426130")) between the 9.10-included kernel and the Atheros-AR928X driver (ath9k), but I would have expected to be able to use the wired connectivity (Broadcom bcm5784m) to update.  No dice.  I may try to hunt down the wired connectivity problem, but for now I am a bit miffed.  Maybe I'll post with more details if I can't get wired connectivity to work.  Other than that though, everything (UI, card reader, suspend/wake, didn't try the videocam, but it's identified in dmesg output) seemed to work very well.  The machine itself is very nice for the price (especially since some online retailers are selling refurbished ones).

---

