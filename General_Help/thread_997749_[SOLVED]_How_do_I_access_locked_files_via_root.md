---
title: "[SOLVED] How do I access locked files via root?"
date: 2008-11-30
forum: General Help
---

### Post by headflux on 2008-11-30
Hi,

Having a bit of trouble. Accident did something which means my system can't recognise my laptop monitor and now only boots in low graphics mode.

Think I might have to reinstall.
However, I'd like to recover some files onto a USB HDD first.  But I can't access the files/folders because of the permission.

I think I can get round this my going via root, but I can't remember the terminal command.

Can anyone help?

Thanks

---

### Post by Elfy on 2008-11-30
```
gksudo nautilus
```

---

### Post by lametike on 2008-11-30
another thing related to this,is there a root account?i heard before that it is disabled by default in ubuntu,so how does i reactivate the account??

---

### Post by headflux on 2008-11-30
Thank You Forest Pixie.  That's the second time you've saved my bacon.

Much Appreciated.

Simon

---

### Post by Elfy on 2008-11-30
@lametike -  If you need to ask how to do so then you shouldn't perhaps be doing it - the forum policy on helping people to do so is clear - [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

Don't ask people how to enable the root account you don't need it and other's won't need the infractions they could get by helping.

---

### Post by stella2657 on 2008-11-30
> **headflux said:**
> Hi,

Having a bit of trouble. Accident did something which means my system can't recognise my laptop monitor and now only boots in low graphics mode.

Think I might have to reinstall.
However, I'd like to recover some files onto a USB HDD first.  But I can't access the files/folders because of the permission.

I think I can get round this my going via root, but I can't remember the terminal command.

Can anyone help?

Thanks
hi, done the same thing myself, just have to fiddle and see how it works, there is a recover option somewhere on the boot menu, cant remember how to, but it did come up with a recover last good video setting, and reset the video settings file.

---

### Post by stella2657 on 2008-11-30
> **stella2657 said:**
> hi, done the same thing myself, just have to fiddle and see how it works, there is a recover option somewhere on the boot menu, cant remember how to, but it did come up with a recover last good video setting, and reset the video settings file.
a quick note on the permission problem, make sure u have permission on your home folder and mount the usb drive on your home folder, not of the root like in windows, this should overcome most of your problems, or else install krusader or gnome commander, they both have a sudo command to move the odd locked pics/word files ect.

---

