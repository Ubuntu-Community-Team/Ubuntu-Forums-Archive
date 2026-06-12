---
title: "Canon P-215 Scanner"
date: 2014-09-18
forum: Hardware
---

### Post by Gavin_Blackford on 2014-09-18
Hi,

I am trying to get a Canon P-215 Scanner to work with Ubuntu, I know this printer will work in Linux as I have tried it with other distributuions with success.

In Ubuntu when I connect the Scanner I can see it listed as a USB Device

```

lsusb | grep -i canon
BUS 001 Device 003: ID 1083:1646 Canon Electronics, Inc.

```

But when I run Simple Scan (or any other Scanning Software) I get a message telling me that no scanners have been found

I have looked on SANE Website ([http://www.sane-project.org/man/sane-canon_dr.5.html](http://www.sane-project.org/man/sane-canon_dr.5.html)) and it lists my Scanner as working with Sane 1.0.24, but when I look on my machine (running Ubuntu 14.04) the version of Sane appears to be Sane 1.0.14-9, I am thinking that this might be my issue, but not sure how I can update this to the latest version when the Repo's only appear to have Sane 1.0.14-9 (it's been a while since I last used Linux).

I might be looking in compeltely the wrong place for this, but this is my first guess to my problem, can anyone help?



Also can anyone reconmend any scanning software, I have tried a few apps, but so far I haven't found any that can give me the fucntionality I am looking for which is to scan multiple documents through my scanner and OCR them (it needs to be able to support my scanners duplex), as it is a document scanner I am not interested in selecting part of a page etc, just hitting scan and having a document at the end.

The closest I have found to date I beleive is gscan2pdf which seems to be able to OCR the documents, but the when I searched the OCR'd PDF the search seems to hightlight the wrong word (e.g. I searched for "and", but it went to the word "the" or something) 



Thanks,


Gavin,

---

### Post by pdc on 2014-09-19
The SANE website has a page on the backend that is said to support your scanner [http://www.sane-project.org/man/sane-canon_dr.5.html](http://www.sane-project.org/man/sane-canon_dr.5.html)

in that, the author who has done the work has a contact address; would it be worthwhile talking directly to him, as he would seem to have the most knowledge to help you? Authors of the backends are frequently very grateful for the contact, as they can evaluate the backend against differing pieces of hardware; that they don't have access to without your help

---

### Post by Gavin_Blackford on 2014-09-19
Thanks for the reply, after a bit more googling I have found that I must have read the version number incorrectly (does anyone know how I find the version number of an installed package?) and I actually have 1.0.23 (or that is what launchpad is reporting is available for Ubuntu 14.04), but the good news is that 1.0.24 is avaialble for 14.10.

I did have a go to see if I could get the packages from 14.10 to install on 14.04 (on a Test VirtualBox machine), but no success and as it is getting close to the release date for 14.10 I am going to wait until it is released to see if that sorts my problems out (or we get a closer to release version I can test on VB as beta 1 wont boot on my VirtualBox)

---

