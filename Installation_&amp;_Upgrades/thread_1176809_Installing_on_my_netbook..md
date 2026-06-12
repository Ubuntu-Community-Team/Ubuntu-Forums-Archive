---
title: "Installing on my netbook."
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by 2598matt on 2009-06-02
i burnt ubuntu to a disc and cant find a slot to put it in on my netbook. how would i go about puting linux on my netbook.
any help?

---

### Post by raymondh on 2009-06-02
> **2598matt said:**
> i burnt ubuntu to a disc and cant find a slot to put it in on my netbook. how would i go about puting linux on my netbook.
any help?


Hello Sir,

Most (if not all) netbooks do not come with a built-in CD drive.  That being the case, you'll need to make a liveUSB which you can plug into a USB port in your netbook, boot into it, and install ubuntu.

Download unetbootin.  If you are using windows right now, download the link for windows.  Here's the link

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

and install the program.  Once installed, open it and source the ubuntu iso you said  you downloaded.  Then plug in a blank USB thumb drive and point unetbootin to it.  Copy.  Quit after a successful copy.

To install, you need set your boot options to access the thumbdrive first (otherwise, windows will always load up).  Of course, you'll also need to have the live thumbdrive attached to the computer.... and install from there.

May I suggest a few readings and research about installing ubuntu.

[http://www.ubuntu.com/getubuntu/releasenotes](http://www.ubuntu.com/getubuntu/releasenotes)
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Let us know if you need further assistance.

Regards,

---

### Post by ktstowell on 2009-06-25
great guide, thanks for the help, im having some trouble atm the moment installing ubuntu from my flash drive. The error is:

NTLDR is missing
Press Ctrl+Alt+Del to restart

Shouldn't the ubuntu bootloader replace the need for a boot.ini?

Any enlightenment would be greatly appreciated, in the mean time ill be doing some more research.

Thanks

---

### Post by Divider on 2009-06-25
NTLDR is apart of the windows operating system, therfor your not correctly booting from the flash drive. 

Make sure you set your boot priority, if need be get a usb cdrw/dvdrw drive.

make sure your attempting to run jaunty, (9.04) and not an earlier version, netbooks don't like the older distro's of ubuntu.

also for a better response post a new topic.

---

### Post by ktstowell on 2009-06-25
Thanks for the reply, turns out i just kept the lastest distro in iso form and mounted it, installed it via the install in windows option to a previsouly designated partition and it works all dandy now. I'm tri-booting xp, vista and ubuntu, with xp and ubuntu successfully installed. Vista is now giving me the NTLDR error, but thats a post for another forum.

---

