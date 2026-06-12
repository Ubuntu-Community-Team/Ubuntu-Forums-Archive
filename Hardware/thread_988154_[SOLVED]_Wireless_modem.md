---
title: "[SOLVED] Wireless modem"
date: 2008-11-20
forum: Hardware
---

### Post by Father Shaggy on 2008-11-20
I'm a total newbie, obviously, but I got a new laptop and thought I'd give linux a try.  The laptop is second hand, and there is an ethernet card, but there was no internal wireless modem.  I picked up a D-link WUA 2340 wireless adapter, and managed to use ndiswrapper to adapt the driver for linux.  It worked well, and I was able to connect to the wireless connection at work.

However, now that I've turned off the computer and restarted it, I can't get the OS to even notice that I've got a wireless modem installed, much less find and connect to wireless connections.

Do I have to uninstall and reinstall the driver?  How would I uninstall it?  Can I use ndiswrapper again?  Is there something I'm not seeing?  is there anyone who can help?

It's been a long time since I had to work in a command line interface, but I've found I've been picking it up again quickly, so I'm not afraid of entering the system prompt.

Thanks.

---

### Post by Fire_Chief on 2008-11-20
Hi Father Shaggy and welcome to Linux! Sorry to hear it's not quite working as expected but no worries. Since you didn't specify which version of Ubuntu Linux, I'll assume it is either Hardy Heron (8.04) or Intrepid Ibex (8.10).

Have a look at this page which directly addresses setting up the Dlink WUA 2340 in Ubuntu Hardy (instructions should work the same for Intrepid).
 [http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html]("http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html")

It's very likely that while the wireless actually does work, NetworkManager is not able to use it properly. the link above addresses this and how to work around it.

Cheers!

---

### Post by prshah on 2008-11-20
> **Father Shaggy said:**
> 
Do I have to uninstall and reinstall the driver?  How would I uninstall it?  Can I use ndiswrapper again?  Is there something I'm not seeing?  


If it works once, there's no need to [un/re]install the driver.

Just load the ndiswrapper module```
sudo modprobe ndiswrapper
``` and your wireless should be active again. If it isn't see```
dmesg | tail
``` for details on why it has failed.

To automatically load ndiswrapper module on boot, add it to the end of your /etc/modules file; just the word ndiswrapper, on a line by itself, at the end. Remember to leave a blank line at the end of the file.

---

### Post by Father Shaggy on 2008-11-20
Fire_ Chief:  Thanks.  That blog post is how I got it to work in the first place.

prshah:  Thanks to you, as well.  I'll give it a shot in a bit, and let you know the results in this thread.

---

### Post by Father Shaggy on 2008-11-20
prshah:

Thanks for the help.  The driver start took care of it.  However, I can't change the "modules" file.  It says I don't have permission.  I tried just opening it through the file tree on the desktop, and it wouldn't let me save changes.  Do I need to edit it through the command line?  How can I get permission?

---

### Post by prshah on 2008-11-20
> **Father Shaggy said:**
> Do I need to edit it through the command line?  How can I get permission?

There are various ways, but the simplest is to press Alt+F2 and give this command```
gksudo gedit /etc/modules
```

Be careful when editing this file. Make your change, save and quit. If you want a closer look at the file, repeat the above command but without gksudo; then it will open as read-only and you can look through it at your hearts' content.

---

### Post by Father Shaggy on 2008-11-20
Thanks.  I appreciate the help.  I'll let you know how it turns out.

---

### Post by Father Shaggy on 2008-11-20
We're all good.  Thanks a bunch!

---

### Post by prshah on 2008-11-20
> **Father Shaggy said:**
> We're all good

Can you mark this thread "solved"? Click on "Thread Tools" near the upper right hand side of this page, and choose "Mark Thread as Solved".

---

