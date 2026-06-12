---
title: "GPS -- using program in wine, what com port?"
date: 2009-07-10
forum: Hardware
---

### Post by xluke on 2009-07-10
Hello,
I am using a GPS program in wine called SeaClear.  I have a USB GPS-360.  How do I know what com port to set the gps?  Com 1-6 say "can not open com x port"  -- is there a way I can verify ubuntu is recognizing my GPS?  How do I know what port to set it on?

Thanks!

-- I should add, I just downloaded GPSDrive and it is not detecting my GPS.  What should I do?  It works fine in windows.

---

### Post by tjapko on 2010-11-08
You have to make a soft link with:

ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1

and then your GPS will be recognized.

---

