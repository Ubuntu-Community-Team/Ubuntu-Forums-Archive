---
title: "Brother Printer  MFC-295CN"
date: 2014-03-05
forum: Hardware
---

### Post by gary21 on 2014-03-05
I can't get my Brother fax/printer/scanner to print.  It worked a couple of days ago but now it doesn't.  Tried to reinstall drivers and the like but now don't know what to do.   I know the printer work because I copied a paper and it printed,  but not from the computer.  Help

---

### Post by phidia on 2014-03-05
Did this printer actually print from your Ubuntu install? According to the Open Printing database & that printer's functioning in linux: > Brother MFC-295CN Black & White inkjet printer, this is a Paperweight

---

### Post by robb3 on 2014-03-05
I'm having trouble installing scanner drivers for my Brother MFC-J475DW. I went to brothers website. [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/) 
I installed printers driver but when I try and install the scanner drivers. I am at a stand still. 
I installed [**brscan 32bit**]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan-0.2.4-0.i386.deb&lang=English_sane"), scanner drivers and I installed [**scan-key-tool 32bit**]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan-skey-0.2.4-1.i386.deb&lang=English_lpr"), scan key. 
The problem is that I am having is the CPU cannot 'talk' to the scanner and the scanner 'does not see' the CPU. Its weird because the printer drivers are installed and the printer works just fine. 
In addition, I ran the command successfully with out luck, brother-udev-rule-type1-1.0.0-1.all.deb, ver.1.0.0-1 
Moreover, I attempted to run the /lib/udev/rules.d/40-libsane.rules command in the Terminal but I was unable to input 
# Brother scanners ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes" where it belonged. Please help. I am almost there. I can feel it.
Thanks

---

### Post by phidia on 2014-03-05
An alternative method of using a brother printer [at this thread]("http://ubuntuforums.org/showthread.php?t=2201868&highlight=Brother+MFC-J475DW").

---

### Post by kurt18947 on 2014-03-06
> **robb3 said:**
> I'm having trouble installing scanner drivers for my Brother MFC-J475DW. I went to brothers website. [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/) 
I installed printers driver but when I try and install the scanner drivers. I am at a stand still. 
I installed [**brscan 32bit**]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan-0.2.4-0.i386.deb&lang=English_sane"), scanner drivers and I installed [**scan-key-tool 32bit**]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan-skey-0.2.4-1.i386.deb&lang=English_lpr"), scan key. 
The problem is that I am having is the CPU cannot 'talk' to the scanner and the scanner 'does not see' the CPU. Its weird because the printer drivers are installed and the printer works just fine. 
In addition, I ran the command successfully with out luck, brother-udev-rule-type1-1.0.0-1.all.deb, ver.1.0.0-1 
Moreover, I attempted to run the /lib/udev/rules.d/40-libsane.rules command in the Terminal but I was unable to input 
# Brother scanners ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes" where it belonged. Please help. I am almost there. I can feel it.
Thanks

There are two issues I'm aware of with the scanner portion of Brother MFDs.  One is the normal user USB issue.  When you're attempting to add those lines, are you doing so as a SUDO user?  You cannot edit system files that affect all users without SUDO privileges.

The second issue is an installer glitch possibly resulting from Brother using alien (I think that's it) to convert .rpm packages to .deb packages.  Here is a link to Brother's scanner FAQ page.  The 4th item "**I'm using Ubuntu 11.10 or higher. I cannot scan from my Brother Machine.** " details the solution.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106)

---

### Post by robb3 on 2014-03-06
Thanks for the advice but I'm still having problems. I inputed my commands with sudo in beginning. I am a normal user as far as I know. I reviewed the glitched and check out my lib64 file and the only thing that I see is : /lib64/ld-linux-x86-64.so.2
(Needless to say I made the line inputs (my inital problem); and restarted my system and the scanner. I moved the USB port into a new position. Still with no success. I try to scan from the machine and it does not talk to the CPU AND the CPU cannot see the scanner.)

In my command prompt I checked the scan key tool  by inputting  dpkg -l | grep Brother  so I can see what's installed and this is what I have. 

ii  brother-udev-rule-type1                     1.0.0-1                                       Brother udev rule type 1
ii  brscan-skey:i386                            0.2.4-1                                       Brother Linux scanner S-KEY tool
ii  brscan4:i386                                0.4.2-1                                       Brother Scanner Driver
ii  mfcj475dwcupswrapper:i386                   3.0.0-1                                       Brother CUPS Inkjet Printer Definitions
ii  mfcj475dwlpr:i386                           3.0.0-1                                       Brother lpr Inkjet Printer Definitions
ii  printer-driver-ptouch                       1.3-3ubuntu0.1                                printer driver Brother P-touch label printers
ii  wesnoth-1.10-ttb                            1:1.10.2-1                                    "A Tale of Two Brothers" official campaign for Wesnoth (branch 1.10)

When I input brscan -skey l AND brscan-skey THEN I get no response. 

Plus, My gf keeps bothering me that I don't spend anytime with her. Thanks for any input.

---

### Post by gary21 on 2014-03-06
yes my printer did work,  now what did you mean with your reply???

---

### Post by kurt18947 on 2014-03-07
> **robb3 said:**
> Thanks for the advice but I'm still having problems. I inputed my commands with sudo in beginning. I am a normal user as far as I know. I reviewed the glitched and check out my lib64 file and the only thing that I see is : /lib64/ld-linux-x86-64.so.2

The MFC-296CN appears to use the same driver as my MFC-6490CW - BRScan3.  I have these in my /user/lib64 folder:
[LIST]
[*]/usr/lib64/libbrscandec3.so 
[*]/usr/lib64/libbrscandec3.so.1 
[*]/usr/lib64/libbrscandec3.so.1.0.0 
[/LIST]

Additionally, there is a sane folder containing the following files:
[LIST]
[*]/usr/lib64/sane/libsane-brother3.so 
[*]/usr/lib64/sane/libsane-brother3.so.1 
[*]/usr/lib64/sane/libsane-brother3.so.1.0.7 
[/LIST]

Without checking the file list in the FAQ section, I believe all of those need to be copied to /user/lib.  So if your /usr/lib64 contains only /lib64/ld-linux-x86-64.so.2  something seems not right.

> 
Plus, My gf keeps bothering me that I don't spend anytime with her. Thanks for any input.

Priorities man! :)

---

