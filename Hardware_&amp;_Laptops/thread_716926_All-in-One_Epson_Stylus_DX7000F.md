---
title: "All-in-One Epson Stylus DX7000F"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by Dmitrijs on 2008-03-06
Dear Sirs,

I'm using now Xubuntu, I like it a lot, but have some problems.
I can't find drivers for this device in the internet, I also was trying to install package from Xubuntu in Add/Remove menu. No result, still can't scan...
Please, help.

---

### Post by markjensen on 2008-03-06
That unit falls under the "paperweight" category at LinuxPrinting.org :(
[http://www.linuxprinting.org/printer_list.cgi?make=Epson](http://www.linuxprinting.org/printer_list.cgi?make=Epson)

Sorry to bear the bad news.

---

### Post by Dmitrijs on 2008-03-06
Thank you,
as I understood - i can't scan and print..... :(

---

### Post by Dmitrijs on 2008-03-06
But I have fount drivers on Epson support pages -> printer driver for this device:
Suse
Mandrake
Red Hat

.....
But I don't know which oper.system should I choose - there is no Ubuntu....
And there is no scan driver.....
Please help/

---

### Post by markjensen on 2008-03-06
Can you post a link directly to the page you found?   I tried finding it on their drill-down menus but could not find it.

---

### Post by Dmitrijs on 2008-03-06
Here the link: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

Dear friends, I would like to thank you for such an operation system like Linux!
I don't to have pay for that - it's brilliant!
Thanks for helping me also!

---

### Post by markjensen on 2008-03-06
Well, their [list of supported OSes](http://avasys.jp/english/linux_e/all-in-ones_OSList.pdf) seems to primarily show 2.4 series kernel releases.  A few 2.6 series show up, looking under your 7000 series.

I would select your printer,  "Stylus CX6900F/DX7000F"
then pick "Fedora Core" for the distro
and "5" for the release (since the chart did NOT show 6 as supported)

This will get you an .RPM file, which is not native to Debian-based distros.  However, there is a tool called **alien** that is supposed to allow RPM files to install in Debian (and, presumably Ubuntu, but I am an old RedHatter recently converted to Ubuntu).

This might work.  It might not.

Best of luck!

---

### Post by Dmitrijs on 2008-03-06
Hmm....... I don't know, will try!
But who makes all these drivers? 
I not even always can install because of Windows using all the time .... :)

---

### Post by markjensen on 2008-03-06
Those appear to be closed-source drivers from (or at least sponsored by) Epson.

Most drivers (for things that work) in Linux are written by the Open Source community.  That makes things easier to get because they can be included in the kernel, or at least easily installed automatically by your package manager.

Notable exceptions to the Open Source drivers are the popular closed-source nVidia and ATI video drivers (because of the sweet, delicious 3-D goodness).

---

