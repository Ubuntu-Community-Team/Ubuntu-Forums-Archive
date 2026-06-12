---
title: "Wubi has no install inside windows option.."
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by avalonofthewind on 2009-04-28
Hey everyone.  I've downloaded 9.04 and run the live cd just fine on my MSI Wind machine.  However, when I try and run Wubi (which won't autostart) it runs BUT won't show the "install inside windows" option at all.

The same cd/usb shows the option just fine on my desktop.  I did have a wubi partition with 8.10 before which I uninstalled and deleted. 

My C: partition is Windows, and my second partition is OSX.  On he c: I have over 15 gigs left.

I'm completely baffled as to why this option won't show up! Any help would be appreciated.  

Thanks!!

---

### Post by Mark Phelps on 2009-04-28
Wubi probably wants a big chunk of contiguous space, and your free space may be spread across the Windows partition.  Try doing a defrag in Windows to see if that helps.

---

### Post by avalonofthewind on 2009-05-18
Thanks for the suggestion...I will try that.

---

### Post by avalonofthewind on 2009-05-22
No such luck. It's still missing the same option.  I put in my old 8.10 stick and Wubi worked perfectly.

I ended up having to install 8.10 clean and then upgrade to 9.04 through the update manager.

I'm baffled by why wubi (9.04) would not have that option whild 8.10 does.

---

### Post by jatinps on 2010-05-03
i have this problem too on a brand new win7 machine with 75gb free in primary partition. this is with wubi 10.04. i think wubi sees recovery partition or something and hence does not give 'install inside windows' option. very strange!

Edit - i tried on 2 more laptops and it works on one but does not work on another. This is really strange and irritating !! - would be nice if someone can hint on some argument which would force it to show the install 'inside windows option'

Edit 2 - i tried with wubi-182 from here [http://people.canonical.com/~evand/wubi/lucid/]("http://people.canonical.com/%7Eevand/wubi/lucid/") - thats the newest one which works. However it does not recognize the latest ISO, I have. So it attempts to download and once download it can't recognize the download iso and so downloads again in an endless loop!
Point to the iso with --skipmd5check does not help.
I have this problem on 2 of 3 laptops (win7 and winxp)

edit 3 - ok it was a lame thing - the reason why I was not getting the option to install inside windows was because wubi saw the livecd/usb inserted so it assumed I don't want to do regular wubi and just asked me to boot from livecd - taking out the usb worked and wubi loaded properly, but the UI should be fixed!!

---

### Post by n.arrow001 on 2011-08-19
Thanks dude this thing worked out for me..

---

