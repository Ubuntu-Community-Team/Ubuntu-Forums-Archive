---
title: "Ubuntu and windows 7"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by bahawks2 on 2009-08-28
Hello every one i was wondering. If I Install ubuntu into a duel boot with windows vista will i still be able to upgrade windows vista to windows 7 with the upgrade disc? also if the trial version of ubuntu is running laggy then does that mean my laptop will perform the same way if i perform a duel boot installation?

Here are my laptop specs:
[http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10127831&catid=](http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10127831&catid=)

---

### Post by oboedad55 on 2009-08-28
> **bahawks2 said:**
> Hello every one i was wondering. If I Install ubuntu into a duel boot with windows vista will i still be able to upgrade windows vista to windows 7 with the upgrade disc? also if the trial version of ubuntu is running laggy then does that mean my laptop will perform the same way if i perform a duel boot installation?

Here are my laptop specs:
[http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10127831&catid=](http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10127831&catid=)

Running from the CD, which is what I assume you're doing, is slow compared to an installed version. If you install Windows first then Ubuntu, then you will be able to dual boot. If you install Windows second then it will overwrite your MBR and only allow you to boot Windows. So if you do a Windows upgrade that's what will probably happen. If it does, come back here and search for reinstalling grub, and that will get you fixed up again.

--Jon

---

### Post by Mark Phelps on 2009-08-28
> **bahawks2 said:**
> ... If I Install ubuntu into a duel boot with windows vista will i still be able to upgrade windows vista to windows 7 with the upgrade disc? ...
Yes, you will be able to do an in-place upgrade -- but only to the same version or higher, in other words, if you're running Home Premium, you can only do an in-place upgrade to Home Premium or "higher". Saying this because lots of folks bought Ultimate for Vista and with Seven, given the lack of discount prices, many of those folks are probable going to go Home Premium or Professional instead.  

However, doing such an upgrade is strongly discouraged.  It's better to do a clean install between major MS Windows versions.

And, as has been mentioned, installing Seven will overwrite the MBR, so you will need to use an Ubuntu LiveCD to restore GRUB.

---

### Post by bahawks2 on 2009-08-28
Alright so from what I have gathered I should probably wait till after I get the windows upgrade disc and see if there’s a way to do a clean install with the upgrade disc. Then once windows 7 is installed, install Ubuntu with windows 7 using GRUB to duel boot; then everything should run smoothly in Ubuntu (unlike the speed of the demo). By the way I was using a USB version of ubuntu demo so that might have been why it was slow I will test the CD I have some where in my house.
:guitar:

---

### Post by presence1960 on 2009-08-28
> **bahawks2 said:**
> Alright so from what I have gathered I should probably wait till after I get the windows upgrade disc and see if there’s a way to do a clean install with the upgrade disc. Then once windows 7 is installed, install Ubuntu with windows 7 using GRUB to duel boot; then everything should run smoothly in Ubuntu (unlike the speed of the demo). By the way I was using a USB version of ubuntu demo so that might have been why it was slow I will test the CD I have some where in my house.
:guitar:

Not exactly. You can install Ubuntu now. if you do a clean install of Windows 7 later all that will happen is windows will overwrite the MBR and you will need the Ubuntu Live Cd to perform a 30 second operation to restore GRUB to MBR. Go ahead and install Ubuntu now!

---

### Post by stlsaint on 2009-08-28
hehehe...i never knew ubuntu had a trial version!!! but yea you mean wubi...and from usb you are running a small version of it as well im assuming so yes a full install will run much faster!

---

### Post by bahawks2 on 2009-08-28
> **presence1960 said:**
> Not exactly. You can install Ubuntu now. if you do a clean install of Windows 7 later all that will happen is windows will overwrite the MBR and you will need the Ubuntu Live Cd to perform a 30 second operation to restore GRUB to MBR. Go ahead and install Ubuntu now!

Ok sweet once I gat home I will run the installation :). Since my laptop only has one hard drive I will have to make it so it has two partitions right? And when I make the partition do I have to make them equal sizes I thought I read some were that they needed to be the same size.

Thanks for all the help so far every one :)

---

### Post by bahawks2 on 2009-08-29
unfortunatly when i installed there was no improvement in the speed what so ever :( so i sadly uninstalled ubuntu maybe its something to do with my hardware maybe the next version of Ubuntu will work out for me.

---

