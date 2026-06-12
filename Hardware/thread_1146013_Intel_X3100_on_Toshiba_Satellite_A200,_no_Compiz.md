---
title: "Intel X3100 on Toshiba Satellite A200, no Compiz"
date: 2009-05-02
forum: Hardware
---

### Post by Bjorg on 2009-05-02
Hello,

Now I use 9.04, but more or less since 3 or 4 months after the launch of 8.10 and using 8.10 my laptop can't start Compiz on startup. With 9.04 that is happening again, I even did a completely fresh install.

My computer is a Toshiba Satellite A200-1DY
[http://es.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=ES&toshibaShop=false&com.broadvision.session.new=Yes&PRODUCT_ID=129159](http://es.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=ES&toshibaShop=false&com.broadvision.session.new=Yes&PRODUCT_ID=129159)

It uses an Intel X3100 graphics chip. This is strange because Intel graphics chips seem to work well with Ubuntu and Compiz.

If I do System>Preferences>Appearance>Visual Effects>Extra
the computer tries to download a driver (process that fails) and then says that effects can't be enabled. What puzzles me is that being an Intel X3100 it tries to download a driver as I it were a propietary driver, and I thought that the intel graphics cards had a good open source implementation.

Then I have to manually start Compiz Fussion Icon and Reload Window Manager, then Compiz works, but only for that session, if I reboot happens the same again, and until I manually reload the window manager again Compiz can't start.

Anybody can help?,

Thanks in advance.

Alex

---

### Post by ajgreeny on 2009-05-02
I don't have an Intel card, but I think there are problems with quite a few of them in 9.04 that did not exist in 8.10.  I seem to remember reading that it is possible to downgrade by uninstalling the jaunty Intel graphics driver and using the intrepid one instead, which you will need to download separately from here.
[http://packages.ubuntu.com/search?searchon=names&keywords=intel](http://packages.ubuntu.com/search?searchon=names&keywords=intel)
Bare in mind that I have not done this and have no way to check it out, but you may be able to find more info, and please don't blame me if it does not work.

---

### Post by DizzyTech on 2009-05-02
Consider yourself lucky.  There are many people receiving fatal freezing bugs on the Intel X3100.  Some are fixed by disabling Compiz, others are not.  As a result, the Dev Team blacklisted Compiz on X3100 cards for Jaunty.

Here's a tip:  enable the proposed repo, you'll get an update to the -intel driver and Compiz that should fix it pretty soon.

---

### Post by Just64 on 2009-05-02
> **DizzyTech said:**
> 
Here's a tip:  enable the proposed repo, you'll get an update to the -intel driver and Compiz that should fix it pretty soon.

What its that repo? U think that they are going to fix it? If yes i ll keep on 9.04, but i was thinking in back to 8.10.

---

### Post by DizzyTech on 2009-05-02
Go to System > Administration, Software Sources.  Type in your password, and go to the "Updates" tab.  Check jaunty-backports and jaunty-proposed if they're not checked already.  Hit the Close button at the bottom, and then "Refresh" when it asks you to.  The update will come via the Update Manager pretty soon, if not today or tomorrow.

---

### Post by Bjorg on 2009-05-02
> **DizzyTech said:**
> Go to System > Administration, Software Sources.  Type in your password, and go to the "Updates" tab.  Check jaunty-backports and jaunty-proposed if they're not checked already.  Hit the Close button at the bottom, and then "Refresh" when it asks you to.  The update will come via the Update Manager pretty soon, if not today or tomorrow.
First thanks to all you for trying to help.

I activated those software sources and have found that there are 5 updates proposed for Compiz and 1 for the Intel video card driver, though they mainly seem to be about the GM965 rather than about the X3100 one. 

[I]debian/patches/028_compiz_manager_blacklist: Revert change from
    1:0.8.2-0ubuntu8 to un-blacklist GM965 (8086:2a02) again. We now have a
    better workaround in the -intel driver. (LP: #359392)[/I]

Anyway I am going to try and report back in a moment, just in case something fatal happens.

**Edited later:** After the update I logged out and started session again, and did System>Preferences>Appearance>Visual Effects>Extra. Now Compiz is working smoothly!! Thanks!!

Thanks,

Alex

---

### Post by Bjorg on 2009-05-02
The problem is solved!!

After the update I logged out and started session again, and did System>Preferences>Appearance>Visual Effects>Extra and Compiz is working smoothly, great!

Thanks!

---

### Post by DizzyTech on 2009-05-02
Glad I could help.  If only I could get mine working the same.

Oh, and by the way:  for future reference, the GM965 and X3100 are more or less one in the same.  The GM965 is the motherboard chipset, the X3100 is the graphics "card".

---

### Post by Just64 on 2009-05-02
> **DizzyTech said:**
> Glad I could help.  If only I could get mine working the same.

Oh, and by the way:  for future reference, the GM965 and X3100 are more or less one in the same.  The GM965 is the motherboard chipset, the X3100 is the graphics "card".

Thanks man! U save me too!

---

