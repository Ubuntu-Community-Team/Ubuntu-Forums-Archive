---
title: "Scanner Canon MP258 noy detected"
date: 2010-06-27
forum: Hardware
---

### Post by kozhi on 2010-06-27
I recently purchased a Canon MP258 all-in-one. While its printing after I installed a driver from the Canon site, Ubuntu 10.04 is not detecting the scanner. Xsane says "No devices available". 

I ran the command sane-find-scanner

Resulting in:
"found USB scanner (vendor=0x04a9, product=0x173a) at libusb:001:007
found USB scanner (vendor=0x050d, product=0x705c) at libusb:001:002"

On running scanimage -L

"No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages)."


Any suggestions? Thanks.

---

### Post by Harikrishnan.T on 2010-06-29
Hey can anyone help me to configure my canon mp258 scanner to my ubuntu 10.04lts. I have already configured my printer but failed to configure the scanner. please help!!!!!

---

### Post by desertdog on 2010-06-29
Your scanner has the same usb id as the MP250, which is supported in the latest version of sane. 

You could try to update to the latest sane using this advanced method. [http://mp610.blogspot.com/2008_04_01_archive.html](http://mp610.blogspot.com/2008_04_01_archive.html)

You could also try an easier method described here [https://help.ubuntu.com/community/UpdateSaneWithPpa](https://help.ubuntu.com/community/UpdateSaneWithPpa)

---

### Post by kozhi on 2010-06-30
Thanks a lot desertdog. I was about to post a solution that worked for me when I saw Desertdog's post. The solution I stumbled upon is here:
 [http://harbhag.wordpress.com/?s=canon+scanner](http://harbhag.wordpress.com/?s=canon+scanner)

It worked for me. So, either way, the scanner should work. Cheers:p

However, I do miss the software that comes with these gadgets. For example, I use an HP scanner at office and its windows based software has one of the best OCRs I have seen. This doesn't work in Wine. I suppose the Canon software might also have some functionalities that might be quite useful. And this too doesn't work under Wine. :confused:

I would look forward to some suggestions on whether there might be some way to use these software under Ubuntu. Thanks once again.

---

