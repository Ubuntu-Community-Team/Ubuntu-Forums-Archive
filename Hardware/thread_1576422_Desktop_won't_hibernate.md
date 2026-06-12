---
title: "Desktop won't hibernate"
date: 2010-09-17
forum: Hardware
---

### Post by Rob625 on 2010-09-17
I have installed 10.04(lucid) on a machine I built myself some years ago. Most things work fine, but it won't hibernate. 

If I choose Hibernate from the "on-off switch" menu at the top of the screen, it blanks the screen, but it doesn't save to disk or turn off. "Hibernate" should mean saving state to disk and powering off, I think.

The pc is an AMD Athlon 64 3000+, and the motherboard ASUS K8V-SE Deluxe. I know that hibernate ought to work with the way the BIOS is set (almost all at defaults), because I also have Windows 7, and that does hibernate when I tell it to "Sleep" - windows-speak for hibernate, at least in this case.

If you can help me to find out what it happening, I'd be very grateful. I would prefer to investigate and understand, rather than  just try a fix to see if it works.

Thanks
Rob

---

### Post by sGroggy on 2010-09-17
The default hibernate option from the "on/off-menu" didn't work for me either. It did not save my session...

You could try: ```
sudo s2disk
``` This works for me. 

To suspend you can use: ```
sudo s2ram
``` If it tells you "Device not supported" or something similiar you can try using the -f switch (force).

If this works for you, you can change the default hibernate from the on/off-menu to this one. I'm not sure how to do this but I think I've read it on this forum.

Although, you probably won't have s2disk/s2ram installed by default, you can install it by doing: ```
sudo apt-get install uswsusp
```


Greetings

---

### Post by Rob625 on 2010-09-17
Thanks, but this didn't work.
I did need to install uswsusp. After that, s2disk took me to a text screen saying "Looking for splash system... none", then after a few seconds back to the graphics screen. And sudo s2ram said "Machine is unknown" and didn't seem to do anything.

---

### Post by sGroggy on 2010-09-17
I doubt this will help, but you can edit /etc/uswsusp.conf so s2disk doesn't look for a splash system. In uswsusp.conf there's also a line "resume device = ..." Is this pointing to your swap partition?

Alternatively you could try another approach found on [http://wiki.archlinux.org/index.php/Suspend_to_Disk](http://wiki.archlinux.org/index.php/Suspend_to_Disk)


Regarding the "machine unknown" message, you can try doing ```
sudo s2ram -f
``` which will force a suspend even if the machine is unknown.

---

### Post by Jerubaal on 2010-09-17
I have the same mobo/processor as Rob625 and recently my computer has been going to sleep and not waking up even though the Power Management settings are 'Never'.

Could this be related? It never used to happen, until the past few weeks. No idea what I've changed - just usual updates.


EDIT: So I found the problem - I had enabled something in the BIOS to do with putting the pc in standby when the monitor went to sleep....

---

### Post by cemsbr on 2010-10-16
I'm having exactly the same problem than Rob625 with dell notebook vostro 1520 and Ubuntu 10.10. I'm using lvm and resume is set to /dev/mapper/vg-swap (root is /dev/mapper/vg-root). Suggestions?

---

### Post by vek on 2010-10-17
I was having this issue with my (new) desktop.  Choosing 'hibernate' would just flicker and then ... not hibernate.

And picking "sleep" would get stuck on blinking cursor.

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/522998](https://bugs.launchpad.net/ubuntu-release-notes/+bug/522998)

Turns out to be this.  Note that the module is now known as xhci_hcd (underscore hcd) in this version.  You know this is the same or similar problem if you try to hibernate, and nothing happens, and you do a 'dmesg' in a terminal and a very recent line says that it could not sleep because a usb device wouldn't sleep..

---

### Post by luispotro on 2011-10-24
I have the same problem than vek ("Choosing 'hibernate' would just flicker and then ... not hibernate."). The s2disk works as a workaround. Now, how do I set s2disk to be the default action when I issue the Hibernate command from the System menu? What do you think?

---

