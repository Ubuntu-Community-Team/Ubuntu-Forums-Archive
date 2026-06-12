---
title: "Ubuntu 10.04 is not working with Brother DCP-7030 printer."
date: 2010-05-06
forum: Hardware
---

### Post by ramzzzz on 2010-05-06
The problem is that I bought a new Brother DCP-7030 printer today and connected it with my Ubuntu 10.04 computer but it does not work. 
When adding the printer to the system there is no driver for DCP-7030 in the Ubuntu's list so I downloaded the correct driver from the Brothers support driver and installed on my computer but still no sucess.
Any ideas.\
Many thanks in advance.

---

### Post by Chrille on 2010-05-12
Having the same problem!
The closest printer driver I find is DCP-2025, but that doesn't work.. :(

---

### Post by dakkar9999 on 2010-05-12
Same here.

---

### Post by dakkar9999 on 2010-05-12
Well, I tried to install the printer following these instructions from Brother.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

and this post.

[http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-9-04-64bit-and-brother-dcp-7030-cannot-install-driver-801845/](http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-9-04-64bit-and-brother-dcp-7030-cannot-install-driver-801845/)

I see the printer correctly, the printing job is said to have been sent successfully, but nothing is printed...

---

### Post by bprince on 2010-05-12
I just picked one up today.  The thing that I found weird is everything appears correct in lucid, but no printing.  So I connected to my windows computer and installed and printed a test page, but two pages came out before the windows test page that look like a linux test page.  they weren't the usual Ubuntu test page though.  They just have printer settings on them.

model# serial #

paper feed setting         print menu

user settings

14 days to return, so it will probably go back.  Oh well worth the try.

---

### Post by bprince on 2010-05-12
just followed:

[http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-9-04-64bit-and-brother-dcp-7030-cannot-install-driver-801845/](http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-9-04-64bit-and-brother-dcp-7030-cannot-install-driver-801845/)

everything works fine for printing.  now just need the scanner to work

---

### Post by dakkar9999 on 2010-05-13
Finally!  It's working.  Went over this post [http://ubuntuforums.org/showthread.php?t=1459926](http://ubuntuforums.org/showthread.php?t=1459926) and I've basically chose install new printer.  

Now it works!

Thanks!

---

### Post by Jim Danner on 2010-05-14
> **bprince said:**
> just followed:

[http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-9-04-64bit-and-brother-dcp-7030-cannot-install-driver-801845/](http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-9-04-64bit-and-brother-dcp-7030-cannot-install-driver-801845/)

everything works fine for printing.  now just need the scanner to workI happen to have installed a DCP-7010 printer/scanner today; it was not all that difficult but there are a lot of instructions to follow.

For the DCP-7030, you'll need the scanner called **brscan3 32bit** (assuming you have a 32-bit computer) labeled **deb** from the list on the [download page]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan3"). Make sure you have the right one...

The required package *sane-utils* is present by default on Ubuntu 10.04. You switch the DCP-7030 on. Then you open a terminal, *cd* to where you have saved the download, and give it
```
sudo dpkg  -i --force-all brscan3-0.2.9-1.i386.deb
```
This installs the scanner for the 'root' superuser. To allow yourself to use it normally, you need to [change another file]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10"):
```
sudo gedit /lib/udev/rules.d/40-libsane.rules
```
At the bottom of the list (but not at the very bottom; above "# The following rule will disable ...") you add
```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

```
and then save the file. Reboot the computer and you should be able to scan (e.g. with Applications... Graphics... Simple scan).

---

### Post by Chrille on 2010-05-17
Hi,
A simple alternative:
Try DCP 7010 driver instead. They seems to work fine for me!

---

### Post by damianpeterson on 2010-06-27
Thank you, Jim Danner. Those instructions worked perfectly for me with my MFC7420 (albeit I had to use the brscan2 .deb file and installation instructions from the Brother website).

---

### Post by Jim Danner on 2010-10-29
I can confirm this works on Ubuntu 10.10 too.

---

### Post by thane1 on 2011-04-23
Thanks also Jim.  First time I've gotten my DCP7030 to scan.  I used the 64 bit driver and it works great in Ubuntu 10.10.  Cheers

---

