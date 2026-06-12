---
title: "Expanding Disk Space on a WUBI Installation"
date: 2008-12-02
forum: General Help
---

### Post by Roger Allott on 2008-12-02
I installed Ubuntu on my main HDD with the qmenu.exe program under Windows. I allocated 10Gb for it.

I've downloaded some of the software for it, but I seem to be no longer able to do that as I'm getting error messages that there isn't enough disk space for all my bits and bobs.

Could someone here tell me how I enlarge the amount of disk space that's allocated to Ubuntu under this type of installation?

---

### Post by vanadium on 2008-12-02
10 gigabyte should be plenty for your system files. You are probably running out of disk space because you are also storing user data (documents, spreadsheets, ..) on that partition.

I advice you to just leave the installation as is, but move the user data out. You can store the user data in your Windows "My Documents" folder and create a symbolic link to that folder in your Ubuntu home directory. This way, you will have convenient access to your data from within your home directory, however without occupying space in your Ubuntu system partition. Besides, using your Windows partition exclusively for data both from within Windows and within Ubuntu will be most efficient in disk space and having your data in a single place is most transparant.

* Move all your user data out of your Ubuntu home under the "My Documents" folder of your regular Windows installation.

* Have two nautilus windows open, side by side, one where the icon of "My Documents" is visible, and a second one opened in your Ubuntu home directory. Press Ctrl+Shift and then drag "My Documents" to your home directory. A symbolic link "Link to My documents" will be created. Rename that to "My Documents" or anything you like. Now, navigating into this link immediately takes you to your documents that you also use from within MS Windows.

The power of Linux symbolic links is that they work exactly like directories. They are a powerfull way to organise the system exactly the way *you* want.

That said, I really think this is the best advise, although I honestly have to admit that I have no idea how you could resize a wubi installation without reinstalling (if you can).

---

### Post by Roger Allott on 2008-12-02
> **vanadium said:**
> 10 gigabyte should be plenty for your system files. You are probably running out of disk space because you are also storing user data (documents, spreadsheets, ..) on that partition.

Thanks, but I haven't created any documents, spreadsheets, etc. in Ubuntu!

I might have been a bit over-enthusiastic in grabbing all the free software I thought I might one day need, but I haven't even got all of openoffice.org yet.

---

### Post by Paqman on 2008-12-02
> **Roger Allott said:**
> 
Could someone here tell me how I enlarge the amount of disk space that's allocated to Ubuntu under this type of installation?

You can use [LVPM](http://lubi.sourceforge.net/lvpm.html) to resize your virtual partition. It can also transfer a Wubi install onto it's own partition.

---

### Post by bapoumba on 2008-12-02
Moved to Wubi.

---

### Post by Jammanuser on 2008-12-02
> **Paqman said:**
> You can use [LVPM](http://lubi.sourceforge.net/lvpm.html) to resize your virtual partition. It can also transfer a Wubi install onto it's own partition.

hey, Paqman...is it possible to also use that program from the Ubuntu Desktop CD, since i can't boot into my wubi install? or could i maybe use it from Windows?

Looking forward to ur reply... :guitar:

---

### Post by Paqman on 2008-12-03
> **Jammanuser said:**
> hey, Paqman...is it possible to also use that program from the Ubuntu Desktop CD, since i can't boot into my wubi install? or could i maybe use it from Windows?

Looking forward to ur reply... :guitar:

It's not available for Windows, and i'm not at all sure it would work running off the LiveCD. It couldn't hurt to try though. 

Are you able to boot into a recovery session of your Wubi? You might be able to uninstall some software from there?

---

### Post by ago on 2008-12-03
> **Roger Allott said:**
> I installed Ubuntu on my main HDD with the qmenu.exe program under Windows. I allocated 10Gb for it.

Is this qemu we are talking about, or umenu? There is no such thing as qmenu.exe

Anyway have a look at the wubi guide. [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

---

### Post by Jammanuser on 2008-12-03
> **Paqman said:**
> It's not available for Windows, and i'm not at all sure it would work running off the LiveCD. It couldn't hurt to try though. 

Are you able to boot into a recovery session of your Wubi? You might be able to uninstall some software from there?

hmm...ok! and no, i can't boot into a recovery session either...i get the same crc error either way! :guitar:

its too bad the program's not available for Windows!:sad:

Thanks for replying though!

Cheers! :D

---

### Post by Roger Allott on 2008-12-03
> **Paqman said:**
> You can use [LVPM](http://lubi.sourceforge.net/lvpm.html) to resize your virtual partition. It can also transfer a Wubi install onto it's own partition.

Thanks for this, but I seem to be in a bit of a catch-22 situation.

I've downloaded LVPM deb file to a Windows drive, but when I try to get Ubuntu to install it, I get an error message telling me I can't because I haven't got enough disk space!

So, I go to add/remove programs on the Applications menu and select a program to uninstall, but invariably it tells me that doing that involves removing some dependencies and I must use Synaptic to do that.

So I launch Synaptic, it gives me an error message telling me to run 'dkfg (or something like that) --configure -a' to adjust the configuration, I click OK to get rid of the error message, Synaptic closes, I run the command suggested in a terminal window, and I'm told I can't because of insufficient drive space!!!!

So, what I seem to need to know urgently is which folders or files that reside in the root directory could I delete, without Ubuntu going tits up, that would provide me with sufficient room to install LVPM?

Anyone got any ideas on that?

---

### Post by magmon on 2008-12-03
Jamman, you can create a new partition using whatever program you like, and install ubuntu via CD directly into the new partition.

---

### Post by Jammanuser on 2008-12-03
> **magmon said:**
> Jamman, you can create a new partition using whatever program you like, and install ubuntu via CD directly into the new partition.

thanks...but that's not what i needed to know! :D i needed to know how to transfer an ALREADY installed ubuntu (the wubi install) to a new partition...**without** booting into ubuntu first...that's why i was wondering if the program that Pacqman mentioned could be used from either Windows or a Ubuntu Desktop CD, which according to him, it can't! ;)

Thanks anyway, though! :)

Cheers!

-jammanuser

:D

---

### Post by wahoobob on 2008-12-05
You might do a directed install to a small partition (8 gb?) to get a version of ubuntu on the machine.  run the program there to  move WUBI to another partition and then delete the partition with the small install.  OR... install virtualbox to run Ubuntu in a virtual machine under window$ ... then move the WUBI there.  I think I would try the second option first as it won't mess up as much GRUB info, etc.

---

### Post by Jammanuser on 2008-12-05
> **wahoobob said:**
> You might do a directed install to a small partition (8 gb?) to get a version of ubuntu on the machine.  run the program there to  move WUBI to another partition and then delete the partition with the small install.  OR... install virtualbox to run Ubuntu in a virtual machine under window$ ... then move the WUBI there.  I think I would try the second option first as it won't mess up as much GRUB info, etc.

Hey! that's a VERY good idea! :D i wonder why i didn't think of it before myself...? I'm probably going to try that...i'll let u know how if it works or not! Thanks! :)

Cheers! ;)

-jammanuser

:D

---

### Post by magmon on 2008-12-06
Ok, back to the original question lol. I would recommend finding a program that makes partitions that works on windows, and then do whatever it was you where trying to do on ubuntu xD

---

### Post by Jammanuser on 2008-12-06
> **magmon said:**
> Ok, back to the original question lol. I would recommend finding a program that makes partitions that works on windows, and then do whatever it was you where trying to do on ubuntu xD

BootIt NG is probably the **best** program for making partitions... ;)

Cheers! :)

-jammanuser

:D

---

### Post by theozzlives on 2008-12-08
Partition Magic, but it's commercial and pricey.

---

### Post by Jammanuser on 2008-12-08
> **theozzlives said:**
> Partition Magic, but it's commercial and pricey.

yeah...i downloaded the program too...in fact, **before** i download BootIt NG! However, i never installed it, because I wasn't sure that it would work on Vista, and also because i read a few things on the Net that said Partition Magic screwed up a couple people's computers...and so i wanted none of that! and that's why i went to BootIt NG!

Anyway, i finally solved my "crc error", so now I can get into my Wubi install again, and download LVPM into that, and then use it to upgrade my Wubi install to a dedicated partition...

Cheers everyone! :guitar:

-jammanuser

):P

---

