---
title: "Brother MFC-J470DW"
date: 2014-11-15
forum: Hardware
---

### Post by Erskien_Lenier on 2014-11-15
Is there a video somewhere that will walk someone who has little to no experience with installing a Brother MFC-J470DW via a Terminal window. I can get the terminal open but it keeps asking me for my wifes password of which the only password I set up this laptop with is the logon password. Tried that an it tells me that's incorrect. I've extracted the install file to desktop that can install the 2-3 different software pieces necessary but thats as far as I've gotten. I'm willing to pay for someone to walk me through this if open to it... . Ubuntu version 14.4 LTS installed. My email is Next Level Mentor at G Mail dot com (no spaces)

---

### Post by kurt18947 on 2014-11-16
Something like this?

[http://support.brother.com/g/b/downloadend.aspx?c=gb&lang=en&prod=dcp115c_eu_as&os=127&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=gb&lang=en&prod=dcp115c_eu_as&os=127&dlid=dlf006893_000&flang=4&type3=625)

You will need to work from an account with SUDO/administrative privileges. The above page indicates this installer is for the DCP-115C.  That shouldn't matter, I don't believe the download is model specific.  Is your printer connected via USB or network? Once you specify your model, you'll be asked to agree to a couple licenses, the installer will start and you'll be asked if you want to specify a URI.  You'll be offered a possibly confusing list of a dozen or more. One will be USB, the others will be network protocols.  Brother printers seem to emulate HP printer protocols.  I have had good luck assigning a static I.P. to networked printers via the machine's keypad and using appsocket/JetDirect. After setting up the printer, you may be asked to agree to a second set of license agreements. This will be for the scanner install. If you don't wish to install the scanner, simply decline the license.

Brother offers a linux help page and FAQs.  Some of the information is fairly outdated.  For instance, I don't find it necessary to do any of the pre-required steps mentioned there.  There have been a couple glitches installing the scanner function but I believe ubuntu 14.04 may have fixed those.  Good luck, I think Brother has one of the easier linux installers.

---

