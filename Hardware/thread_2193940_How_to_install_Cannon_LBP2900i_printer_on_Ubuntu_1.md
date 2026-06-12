---
title: "How to install Cannon LBP2900i printer on Ubuntu 13 and Xubuntu 13"
date: 2013-12-15
forum: Hardware
---

### Post by stevecook on 2013-12-15
I have just changed my OS to Xubuntu 13 from Ubuntu 12.04 LTS and have experienced a problem with the Cannon LBP2900i printer not working. It was pretty tricky to get it working on 12.04 LTS, but was possible. Hower some of the CUPS environment must have changed in Ubuntu 13 so that now the old method I used does not work anymore.

I have since discovered a method of getting the printer working again in Xubuntu 13 and Ubuntu 13.

You'll need to download the following file and and  install it via the softare centre then go back and follow my original  instructions on another earlier thread of mine for installing the Cannon LBP2900i printer in Ubuntu 12.04 LTS ([http://ubuntuforums.org/showthread.php?t=2013437](http://ubuntuforums.org/showthread.php?t=2013437)). I've absolutely no idea why this extra file makes the printer work again, but there it is. I'm sure there are some Ubuntu boffins here who can come on this thread and explain precisely why this works.You  are more than welcome to try it for yourself.  The fille is called:

**[B][SIZE=2]gs-esp_8.71.dfsg.1-0ubuntu5.5_all.deb[/SIZE]**[/B]

I think it is something called a "transitional package"

You can download it from:

[http://packages.ubuntu.com/uk/lucid/all/gs-esp/download](http://packages.ubuntu.com/uk/lucid/all/gs-esp/download)

If you double-click the downloaded file, it should open in Software-Centre and then you can install from there.

I should say, I completely purged CUPS and reinstalled it (to get rid of all the mess I had previously made trying to get the printer to work) prior to  installing the above transitional package and then installing the printer driver in the way  previously shown in the other thread of mine I have linked to.

Hope this works for others.

Steve Cook.

---

