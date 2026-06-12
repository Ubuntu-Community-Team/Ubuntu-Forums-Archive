---
title: "ATI Mobility x300 help needed"
date: 2010-01-30
forum: Hardware
---

### Post by jman6495 on 2010-01-30
hi ,
i have a ATI radeon mobility x300 , in the Hardware Drivers section there is nothing , compiz works fine , but blur windows has never worked , it doesnt blur and it makes the PC really slow ,
i heard somewhere that the 9.11 version of the AMD catalyst driver works with blur , 


```
Some people said the blur plugin got fixed in fglrx 9.11. Anyone confirming? For me it doesn't work at all, maybe it needs some special settings to work.
```

```
Confirm. Blur works with 9.11 driver. 
```

but i cant install it!

i downloaded the .run ,

this is what happens 

```
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-17-generic; make sure that the version is being
correctly set by --iscurrentdistro
```

so that doesnt work ,
i really need to get blur working for a project ,


i am running ubuntu 9.10

---

### Post by sapg on 2010-01-31
I've been looking at this also, as far as I know the new Catalyst drivers don't support the X300 radeon mobility cards anywmore.  My girlfriend's laptop has this card and fullscreen flash video playback it terrible.  I think that the opensource drivers will support these on the newer Xorg that Karmic has eventually.  The other option I've seen is to downgrade Xorg so that you can use the older opensource drivers but I'm not keen to do that.

---

### Post by xdaedalus on 2010-02-01
I've also been having problems getting my mobility x300 to work in 9.10. As far as I know (from poking around forums) ATI dropped support for the x300 from the proprietary fgrlx driver, and the current software in 9.10 doesn't support the old fgrlx drivers that do support the x300. The open source driver works great for almost everything, but you can't get full functionality out of it (as both you and I have noticed)

For about a month I've been using Ubuntu as my main OS, and this has been pretty frustrating. Does any one know of a solution? How would you downgrade Xorg, and what would be the consequences of that? Is there another way to solve the problem?

---

### Post by Mana Whyrl on 2010-02-04
Here is a title: [http://ubuntuforums.org/showthread.php?t=1171445](http://ubuntuforums.org/showthread.php?t=1171445) - downgrade xorg on Jaunity, but not Karmic..(

ps. [http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue) and one more, but also Jaunity :(

if you find for Karmic please post here !

---

### Post by Yellow Pasque on 2010-02-04
If you tried to install the Catalyst driver, make sure you purge all of its files (the installer doesn't clean up well): [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

I would recommend you try the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=karmic)
There's also a handy utility (ppa-purge package) to make it easy to restore your original setup if you're unsatisfied with the results.

---

