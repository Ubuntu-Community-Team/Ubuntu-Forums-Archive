---
title: "Dell A920 - some success printing"
date: 2011-03-01
forum: Hardware
---

### Post by NJames99 on 2011-03-01
I am very new Linux, and have been searching for a way to get my Dell A920 to print. I have succeeded in getting the printer to print at least in black and white. The printer always was unreliable for color so I won't comment on color printing. Copying and scanning are not working at all.

I just installed Ubuntu 10.04 on a new system yesterday.

I downloaded lidstdc++5 from [http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb](http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb)

Then I downloaded lexmark.z600-0.4.deb from [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=view&target=lexmark.z600-0.4.deb](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=view&target=lexmark.z600-0.4.deb)

Then System > Adiministration > Printing > select Add printer, the A920 was plugged in and recognized. I selected it and clicked forward.

I had to wait for several minutes while Ubuntu searched for drivers. I closed the hardware driver window that eventually opened. Then a new printer window opened. Under "Makes" I selected Lexmark, then forward, under Models I selected Z600.

And that did it. Test page showed I was low on ink...:D Maybe this will be helpful to someone else.

---

