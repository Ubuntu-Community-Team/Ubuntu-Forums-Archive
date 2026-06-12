---
title: "Portable Hard Drive Mounting/Unmounting Errors!"
date: 2008-01-31
forum: Hardware &amp; Laptops
---

### Post by myke on 2008-01-31
A quick bit of help is needed here.  I've become comfortable with KDE over Gnome lately and want to stick with it.  I have everything working but one.  I have a portable hard drive by Wester Digital; a Passport.  I have it formatted in NTFS.   It mounts perfectly fine but every so often I need to "safely remove" it and later remount it without restarting the laptop.  I can right click on the icon in the media folder and unmount it fine but when I try to remount it, it gives an error every time saying I don't haver permission or that kio-mount helper can not mount at this time.   I have found a work around in that I can go into system settings: hard drives and re-enable it after signing in as administrator.    It's just that this is a pain in the back side.

Also, if my Passport isn't already plugged in when I start my laptop and I later plug it in, I can only get it to mount by going into system settings.

Surely there is some way to allow my id to mount and unmount with a click of a mouse.  I have root set to be allowed to login under the gui on it's own and simply double clicking on the icon will mount it after it's been unmounted or plugged in after the laptop is started.   I want this same ability in my regular id login.

I'm sorely tempted at this point to just customize everything under root login as there never is a problem when logging directly thru the gui as root.  I know you can mess things up easier this way also but there also is alot less conflicts having full admin authority without doing everything thru sudo.

However, if anyone can help me fix this mount / unmount problem, this is the only thing I haven't figured out how to fix on my own id thus far.

Please help if you can.

This is occuring ... BTW ... under KDE.   I've sought help from the Kubuntu forums to no avail. There's just not as many people over there.   These little annoyances are actually causing me to consider moving over to Gnome as I could still keep my favorite KDE packages.  So here's a question for you Gnome folks:   Can you set up the desktop where the icons for portable drives and such don't automatically appear on the desktop when mounted.  I have been using the Ubuntu Gutsy live cd to try it out and the mount/unmount problem is not there that is with KDE.  The only odd thing is, 2 iconss always appear on the desktop for my portable drive.  If I unmount it, one always stays and I can't get rid of it without logging out and back in again.   I'd rather not have them on the desktop anyway but on a panel.  Can it be set up like this in Gnome?

---

### Post by myke on 2008-02-03
Any ideas?

---

### Post by Yellow Pasque on 2008-02-03
Post your /etc/fstab file. The line probably just needs to have the 'user' option added to it.

---

