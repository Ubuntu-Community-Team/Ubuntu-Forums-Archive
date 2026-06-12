---
title: "Dell C840 backlight won't shut off"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by chip616 on 2007-04-02
I have a Dell C840 laptop that has worked well on previous versions of Xandros Linux -- another Debian derivative.  The backlight shut off just fine with the timeout on the screen saver set.  I recently upgraded to Xandros 4 (2.6.18 kernel) and I cannot get the backlight to shut of for any reason.


Anyone have experience with this hardware on Ubuntu?  I'll switch distros if it works with Ubuntu.

The only reference I found to this item in the forum is here, and it is not exactly the same problem:

>http://www.ubuntuforums.org/showthread.php?t=17436&highlight=Dell+C840+backlight<

Thanks.

---

### Post by thewizard5001 on 2007-04-02
My backlight shuts off just fine with Ubuntu 6.10 and Ubuntu 7.04 Feisty Fawn (which is in beta, I'm using it now, it's very stable, and, it allows me to close the laptop lid and not have the GUI crash, excellent!)

---

### Post by chip616 on 2007-04-02
TheWizard5001:

Can you confirm a that you also have a Dell C840?  While I assume that is the case, you don't specifically state it.  Hardware is very finnicky, and what works on one Dell machine may not work on another.  Has to be the SAME model.  :)

Thanks.

---

### Post by chip616 on 2007-04-06
OK, here is the solution:

It is necessary to add a line to the /etc/X11/xorg.conf file.

Open /etc/X11/xorg.conf with root privileges.

In the "Monitor" section, add the following line:

     Option  "DPMS" "true"

Save the file back to disk.

The quotation marks are necessary.

This may or may not be an issue with Ubuntu.  If you do have this problem, then here is a solution.  Ubuntu may already include that option in its xorg.conf file.  I can't check at the moment, as I have the Ubuntu 6.06 disk out of my machine.

My thanks to the kind folks in the [CompuServe Linux forum]("http://community.compuserve.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=127892") who assisted in finding this fix.

By the way, that forum is free.  You need to sign up for an AOL screen name, but  that is a free service.

I hope no one minds my posting this link here.  I have been a member of that forum for going on 5 years.  It is a small community, but knowledgeable.  Responses are quick, and don't get 'lost' in the sheer volume of messages that get posted in larger forums like this one.


Frank.

---

