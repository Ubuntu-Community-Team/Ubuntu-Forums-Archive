---
title: "Trouble with MFC-J475DW Brother scanner"
date: 2014-03-10
forum: Hardware
---

### Post by robb3 on 2014-03-10
Good evening. 

I am having trouble installing the scanner drivers for my MFC-J475DW Brother scanner. I press the scan button on the scanner/printer and the device cannot see my computer. I try scanning on linux software and the software cannot see the device. I installed the printer drivers because my printer works. I have utilized Brother's website, [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1.html) I feel exhausted and I could use some assistance. 

1. In my command prompt I checked the scan key tool  by inputting  dpkg -l |  grep Brother  so I can see what's installed and this is what I have. 

ii  brother-udev-rule-type1                     1.0.0-1                                       Brother udev rule type 1
ii  brscan-skey:i386                            0.2.4-1                                       Brother Linux scanner S-KEY tool
ii  brscan4:i386                                0.4.2-1                                       Brother Scanner Driver
ii  mfcj475dwcupswrapper:i386                   3.0.0-1                                        Brother CUPS Inkjet Printer Definitions
ii  mfcj475dwlpr:i386                           3.0.0-1                                        Brother lpr Inkjet Printer Definitions
ii  printer-driver-ptouch                       1.3-3ubuntu0.1                                 printer driver Brother P-touch label printers
ii  wesnoth-1.10-ttb                            1:1.10.2-1                                     "A Tale of Two Brothers" official campaign for  Wesnoth (branch 1.10)

2. When I input the commands: brscan -skey l AND brscan-skey THEN I get no response in the command prompt

3. I  used gksu gedit /lib/udev/rules.d/40-libsane.rules and I added the two lines that's annotated on Brother's website. 

4. I checked out my lib64 file and the only thing  that I see is : /lib64/ld-linux-x86-64.so.2
(Needless to say I made added the line inputs; and  restarted my system and the scanner. I moved the USB port into a new  position. Still with no success. I try to scan from the machine and it  does not talk to the CPU AND the CPU cannot see the scanner.)

5. On a side note, my gf tells me its 'fine' to do what I want to do. Then, she aggros me for not spending enough time with her. 

I am new to Linux and I'd be very appreciate for any guidance. Thank you

---

