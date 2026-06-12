---
title: "Brother MFC-465CN won't print via network"
date: 2009-07-22
forum: Hardware
---

### Post by oryan_dunn on 2009-07-22
I've got a Brother MFC-465CN connected via a LAN connection.  It prints fine from several Windows machines, so I know the printer and network are fine.  I have looked at all the info available from Brother on the printer, but nothing they suggest seems to work.  The machines that have problems have Ubuntu 8.04 amd64 and a dell mini with the lpia 8.04 installed.  In both cases, I've installed the brother-* drivers for the printer, the printers dialog finds the printer just fine and the driver shows up just like it should.  When I print a test page, everything within Ubuntu indicates that the test page went though successful.  The LCD screen on the printer lights up like it is about to do something, but then nothing happens.  Does anyone have any ideas?

Things that I will try tomorrow is to use a 32-bit 8.04 live cd to see if it will work from that.  Also, I will try 8.10, and 9.04 if the 8.04 doesn't work.  I will also try to connect it directly via USB.  Ultimately, I will need to get it to work in 8.04 via the network, but perhaps these other methods will narrow down the source of the error.

I must mention that this is not at my house.  The person a while back had Ubuntu 8.10 amd64and I seem to remember that he was able to print from that.  I'll try the things I mentioned above, but I wanted to see if anyone here has some insight into the issue.

Thanks,
Ryan

---

### Post by oryan_dunn on 2009-07-23
Ok, so chalk one up to human incompetence.  I had installed the bh7 instead of the extra package.  This page here [https://wiki.edubuntu.org/BrotherDriverPackaging](https://wiki.edubuntu.org/BrotherDriverPackaging) is a bit misleading as it says that the 465CN driver is in bh7 package.  So, that is what I was using, which ubuntu detects the recommended driver as the 460cn.  After I installed the -extra packages, it detected as the recommended driver the 465cn, and it worked properly after that, with no special settings.  I'll see if I can update/contact the maintainer of that page, so that other may not be as confused as I was.

---

