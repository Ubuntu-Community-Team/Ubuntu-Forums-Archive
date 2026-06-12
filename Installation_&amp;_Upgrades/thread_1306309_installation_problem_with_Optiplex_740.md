---
title: "installation problem with Optiplex 740"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by intelliboy on 2009-10-30
Hi,
I am having problems installing kubuntu/ubuntu on my optiplex 740 desktop. I burned thru 5 cd's of kubuntu, ubuntu and kubuntu-alternate and with every cd, once i boot, i reach the main selection screen where you get to select between "install kubuntu, try kubuntu without installing etc". I have tried every option there and each time, all i get is a blank screen with a blinking cursor on the top left corner and the system then just sits there. After a while even the cd stops spinning. 

I searched around and seems like other optiplex 740 users also have the issue. Has anyone else faced this or have a suggestion?

---

### Post by phillw on 2009-10-30
> **intelliboy said:**
> Hi,
I am having problems installing kubuntu/ubuntu on my optiplex 740 desktop. I burned thru 5 cd's of kubuntu, ubuntu and kubuntu-alternate and with every cd, once i boot, i reach the main selection screen where you get to select between "install kubuntu, try kubuntu without installing etc". I have tried every option there and each time, all i get is a blank screen with a blinking cursor on the top left corner and the system then just sits there. After a while even the cd stops spinning. 

I searched around and seems like other optiplex 740 users also have the issue. Has anyone else faced this or have a suggestion?

1.  md5 checksum the ISO ...... [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
2.  Burn at 4X speed, MAXIMUM
3.  md5 checksum the CD.

In your case, I'd also suggest that you clean your CDR drive with a cd-cleaner & make sure you're using a 'decent' brand of CD 

Apologies if you have done all the above.  It just rules out a massive %ge of the 'funnies' that happen.

Regards,

Phill.

---

### Post by intelliboy on 2009-11-03
Thanks for the info. Following your advice, i burned a cd at 2x. Also i was using a verbatim cd and i used a memorex this time. I am still having the same issue with the Optiplex 740's. All of the cd's work fine on my lenovo thinkpad and on another machine that has an ASUS mobo with an AMD processor. 

On the Optiplex 740's, no matter which cd i use or what i select, i simply get a blinking cursor and a blank screen after the initial (k)ubuntu menu selection screen. 

> **phillw said:**
> 1.  md5 checksum the ISO ...... [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
2.  Burn at 4X speed, MAXIMUM
3.  md5 checksum the CD.

In your case, I'd also suggest that you clean your CDR drive with a cd-cleaner & make sure you're using a 'decent' brand of CD 

Apologies if you have done all the above.  It just rules out a massive %ge of the 'funnies' that happen.

Regards,

Phill.

---

### Post by phillw on 2009-11-03
> **intelliboy said:**
> Thanks for the info. Following your advice, i burned a cd at 2x. Also i was using a verbatim cd and i used a memorex this time. I am still having the same issue with the Optiplex 740's. All of the cd's work fine on my lenovo thinkpad and on another machine that has an ASUS mobo with an AMD processor. 

On the Optiplex 740's, no matter which cd i use or what i select, i simply get a blinking cursor and a blank screen after the initial (k)ubuntu menu selection screen.


Hmm, sorry you're still having problems - oh, and btw, I've never had problems with Verbatim discs.

Do you have / can you get a windows install disc - and try and see if your computer recognises that as a boot disc. I'd like to try and rule out a cd-drive error.

Another option would be to download & burn off, say, Gparted and try that.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

(SourceForge is a trusted site)

In the meantime, I'll have a dig around and see if there are any reported issues with your system & kubuntu.

Also try the dell area of this forum at ....   [http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

Phill.

---

### Post by Roasted on 2011-02-23
I know this is an old thread, but I wanted to bump it as I'm having the same issue.

I have Ubuntu 10.10 installed on this system, but for testing purposes I wanted to format it and install Kubuntu 10.10. It locks up after I select Start Kubuntu.

I've tested the CD and checked all of the MD5 sums of everything. I burned the CD in slowest speed and I also tried Kubuntu from a flash drive. All fails at the same point.

I'm clueless on what else can be done. The same media on an HP dc5850 here on my desk works flawlessly.

To be fair, the Optiplex 740's have given me a lot of headaches. For example, for PXE boot to work properly for mass imaging, I had to flash each BIOS to 1.1.8, which is an old BIOS version. Every BIOS version after that on up to 2.1.9 and beyond has yet to correct the PXE issue. Damn these 740's.

---

