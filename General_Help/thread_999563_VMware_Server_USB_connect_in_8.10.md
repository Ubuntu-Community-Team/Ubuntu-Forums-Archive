---
title: "VMware Server USB connect in 8.10"
date: 2008-12-02
forum: General Help
---

### Post by nowhere@cox.net on 2008-12-02
Hey all. I updated via fresh install from 8.04 to 8.10. In 8.04, I was running VMWare server 2 and everything worked fine, including USB connect allowing me to run iTunes in VMware and sync my iPhone. On the bottom right of the VMWare console, there was a USB button that after I connected my iPhone and ubuntu squawked about it, I could click the icon and say connect and it would be available in the VMWare. See attached picture to see the icons I'm talking about.

Now, with the same vmx files and same version of VMWare, installed on 8.10, this icon is missing. It's the only thing different. Now I have to open firefox, load up the vmware web client, log in, wait, wait, wait some more, then the iphone will show up on the USB menu and I can tell it to connect there. Then I wait some more and many Ubuntu dialogs pop up again but it is available in the VMWare console. Anyone know how to get this simple icon back in the status bar?

Thanks,
Eric

---

### Post by nowhere@cox.net on 2008-12-10
Bump.

Anyone?

Thanks!

---

### Post by z662 on 2008-12-13
i am having the same problem...

---

### Post by reduser on 2008-12-17
Me to!

---

### Post by tverbisc on 2009-01-19
I had the same problem using Ubuntu 8.10 and VMWare Server 1.08.  The following link was the answer for me:

[http://kenyangeekboy.blogspot.com/2009/01/getting-vmware-server-to-see-usb.html](http://kenyangeekboy.blogspot.com/2009/01/getting-vmware-server-to-see-usb.html)

---

### Post by nowhere@cox.net on 2009-01-22
Thanks! I'll try it out. I wonder if it's going to goof up the gnome auto mounting of USB devices...

---

### Post by nowhere@cox.net on 2009-01-25
That was a great step in the right direction. My USB drives and iPhone now show up on the remote console status bar and in the Devices menu. However, when I use them I get an error.
```
Remote USB device error: Remote device disconnected: an error occured while sending data.
```

If I use the web based interface it works fine. I'm thinking the remote console is not unmounting or something before trying to attach the USB device.

Any ideas here?

Thanks!

---

### Post by dcstar on 2009-01-25
There are fixes for VMWare issues in the Virtualization forum (where this thread should be), and detailed instructions on fixing USB issues.

---

### Post by nowhere@cox.net on 2009-01-25
Hi David,

Do you have any specific links in mind?

Thanks.

Edit: FYI
Here is the same problem unresolved...
[http://ubuntuforums.org/showthread.php?t=1020429&highlight=vmware+USB](http://ubuntuforums.org/showthread.php?t=1020429&highlight=vmware+USB)
Here is a solution for pre-Intrepid (doesn't work for 8.10)
[http://ubuntuforums.org/showthread.php?t=731001&highlight=vmware+USB&page=2](http://ubuntuforums.org/showthread.php?t=731001&highlight=vmware+USB&page=2)
This is what I did to get the USB to show on the devices menu of the remote console but this leaves me back at link 1
[http://ubuntuforums.org/showthread.php?t=626118&page=3](http://ubuntuforums.org/showthread.php?t=626118&page=3)
This search yields no results:
vmware server "2.0" USB

---

### Post by nowhere@cox.net on 2009-01-26
Gave up. Switched to Virtualbox. USB works fine with a simple addition to the fstab. I like it way way WAY better than what vmware did to Server when they went to 2.0 and that web interface. 

Looks like Virtualbox has come a long way and for what I need it for it seems to work great!

Now I have to migrate my iTunes stuff grrrrrr....

---

