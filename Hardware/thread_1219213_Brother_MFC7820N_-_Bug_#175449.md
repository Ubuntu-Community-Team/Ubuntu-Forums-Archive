---
title: "Brother MFC7820N - Bug #175449"
date: 2009-07-21
forum: Hardware
---

### Post by moonguide on 2009-07-21
I have a Brother MFC7820N installed on Ubuntu 8.04. It's a network printer and is also installed on my XP laptop. Printing on XP takes a "normal" amount of time: click Print, within a second or two printing begins with no noticeable pause between pages. Do the same thing from my Ubuntu desktop machine and printing doesn't begin for many seconds, and there is a many second pause between pages.

GOOGLE-ing turned up:

[https://wiki.edubuntu.org/HardwareSupportComponentsPrintersBrother](https://wiki.edubuntu.org/HardwareSupportComponentsPrintersBrother)

which led to:

[https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother/MFC-7820N?highlight=(Bug)|(\%23175449](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother/MFC-7820N?highlight=(Bug)|(\%23175449))

Those tell me that this was a known problem on 2007-12-15, and that I should see Bug #175449.

I have not had occasion to pursue bugs in the past. My brief attempt to track down what's going on with it led me to:

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/175449](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/175449)

That was all very interesting, and possibly related to my issue, but I don't see anything that indicates the real status of the bug. I see a Status column with three lines, each with a different status, new, invalid, triaged. Following links doesn't lead to any useful information.

Is there some way to determine if someone is actually working on the problem, and how they're doing?

---

