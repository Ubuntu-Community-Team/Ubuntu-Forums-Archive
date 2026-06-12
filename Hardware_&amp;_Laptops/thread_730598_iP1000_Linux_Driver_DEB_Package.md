---
title: "iP1000 Linux Driver DEB Package"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by tdm on 2008-03-21
**I am currently working on a DEB package for this printer but for now use my easy tar.bz2 package for Ubuntu and other distros.**
 
[Get It Here]("http://www.esnips.com/doc/a88b484e-fbd3-443d-9634-744ef5aa22e4/Canon-PIXMA-iP1000-Linux-Driver.tar")


:) :)

---

### Post by tdm on 2008-04-12
[CENTER][COLOR=Black]:grin:  \\:D/
[/COLOR][/CENTER]
[COLOR=Black]**I have created the DEB package for Debian/Ubuntu based systems.**
[**Get It Here**]("http://www.esnips.com/doc/8478e2e8-23d8-4863-bca9-4b65469d5d00/ip1000-driver-for-debian-based-systems")

You may need to restart the CUPS server, do this by rebooting or running the following commands:
sudo -s
[/COLOR][SIZE=1][COLOR=Black]*(password)*[/COLOR][/SIZE][COLOR=Black]
killall cupsd
cupsd
exit

NOTE: For systems that are not Debian/Ubuntu based use my easy tar.bz2 package above.[/COLOR]

---

### Post by ja-ve on 2008-05-01
I'm an Ubuntu 8.04 *newbie* sporting a iP1000. Just want to thank you because this is the only procedure out there that **really works! **=D>

---

### Post by guhpraset on 2008-05-08
It didnt work for my hardy heron

--- update ---

success after i followed few steps mentioned [here]("http://ubuntuforums.org/showpost.php?p=1994891&postcount=1").

Thank You!

---

### Post by Macario Muñoz on 2008-05-21
Thanks a lot tdm! Great job!

Hoary.- I never knew how to make my Pixma ip1000 printer works.
Breezy.- I could install it converting the rpm drivers to deb,
Dapper:- The same
Edgy.- Install it was very easy using the takushi debs.
Faisty.- The same
Gutsy.- Takushi repository was and is dead. I couldn't do it works by any other method.
Hardy.- I tried a lot but I couldn't. Just now with your fabulous deb.

Thank you again. Sorry for my bad English.
Greetings from Veracruz, Mexico.

---

### Post by surja on 2008-07-08
Sorry the .deb file did not work. But it worked after I followed "guhpraset' instructions. Thanks.:)

---

### Post by tdm on 2008-07-08
I don't know why it doesn't work on your box. :(

It works fine on my Hardy box and my Fathers one. Even on a fresh re-install.

Just install the .deb package
Plug in the printer (iP1000 ONLY!!!)
Turn on the printer
Wait until it says from the notification area this:
Driver Installed "Canon Print filter v2.50"
(or something like that)

I have had no problems with it at all.
:)

---

