---
title: "Acer suspend"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by scubasteve657 on 2008-02-15
I have an Acer Aspire AM1100-E1302B destop pc.  It will not suspend with ubuntu.  Anybody have any success with this model or things to try?

I found a small command line program a while ago that let me try different standby modes.  I thought it was called s2ram or something similar but I've never been able to find it again; does anyone know what I'm talking about?

---

### Post by Namain on 2008-02-15
The program you are thinking of is called "uswsusp".  You can find it in the Ubuntu repos, but it is a bit of a crippled build.

I would suggest installing the Debian build of uswsusp.  It is found here: [http://packages.debian.org/sid/uswsusp](http://packages.debian.org/sid/uswsusp).  If it says that your computer is not supported you may have to use a work around to make it work properly.  I would suggest trying s2ram very cautiously.

For more information on uswsusp check out:
[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)
and the uswsusp homepage:
[http://suspend.sourceforge.net/](http://suspend.sourceforge.net/)

---

### Post by scubasteve657 on 2008-02-20
Thank you for the tip, but it is still not working.  I tried every option with s2ram and the best I could get is a frozen display of "inu ATI Radeon Xpress 1250", and even capslock wouldn't work.  So my guess is it's a radeon problem.  Disabling the restricted kernel module did not help.

Any furthure suggestions?

---

### Post by scubasteve657 on 2008-02-22
Okay, so I can get suspend working with s2ram now.  Turns out I was just waking the computer too soon after it went to sleep.

But it won't work when the fglrx module is loaded.  I like my compiz eye-candy, so I will continue using this module.

Here is the process for getting supsend to work:
# /etc/init.d/gdm stop
# rmmod fglrx
# s2ram -f -a 1

So,  my question now is, can I write a scrip that will accomplish this?  And if so, can I also script it to re-insert fglrx & reload gdm? Admitedly this is not ideal behavior, but it would be better than leaving the machine on 24-hours a day or turning it off at nights.

Also, if I get this working, I"d like to be able to wake the machine by lan when I access a samba file share.  Windows is able to accomplish this quite well, can it be done with linux?

---

