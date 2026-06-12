---
title: "After installation updates can't work well"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by smart ali on 2009-07-25
Good afternoon,

I have installed Ubuntu 9.4 in my PC. for the first time it's working very well.
After installing all updates I rebooted the system and now I can't connect it to the internet, I can't open firefox...etc

I don't know what to do.:o

I'm new user for Ubuntu, just escaped from Fedora11


waiting the help from you guys :)

---

### Post by quixote on 2009-07-26
Well, let's hope it's something simple, like a file that didn't download during the update. :)

When you say "no internet" are both wired and wireless down?  Or will it connect when wired?

It might be worth trying to put in a wired connection, and then boot into recovery mode.  Choose the option to start a "root console with network support".  (Be careful at this point, because commands you enter can affect all parts of your computer.)  Then at the command prompt enter "ping www.google.com"  It should return a repeating series of messages saying how long the ping took to reach google.  If not, there's no connection that way either.  

If it does reach the great wide world that way, you can try: ```
dpkg --configure -a
``` (Be careful not to make any typos.) This should fix broken packages, if it finds any.

To get out of the recovery mode type at the command prompt "reboot" or "halt now" (the latter for shutdown).

---

