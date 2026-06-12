---
title: "Brother DCP-385C - Can't get the scanner to work (64bit)"
date: 2012-04-14
forum: Hardware
---

### Post by Keypen on 2012-04-14
The printer works fine. No problem at all. The problem is the scanner.

Simple Scan just says it can't find the scanner. Xsane 0.998 says it cant open the unit "brother3:bus8;dev1".

I have tested the guide at: [http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)
The guide is five years old. I get stuck at editing the file /etc/udev/rules.d/45-libsane.rules because it does not exist. I tested to edit like it looks in the guide but no it's not working.

I have tested Brothers solution at: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)
cp says that the files are the same. Linked or what it is called?


I have downloaded and installed brscan3 64bit and scan-key-tool 64bit.
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)


I have tested to run brscan Scan-key-tool but it do not find my scanner. If I type "brscan-skey  -l" in the terminal I get an empty anwser.
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn3.html)


What is it that I'm missing?

---

### Post by Keypen on 2012-04-15
I was researching and I found a "solution", run the scanning software as root. But this isn't my type of solution for a problem.
[https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/578620](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/578620)

On the same page a comment by Alastair Callum (alastair-callum) fixed the problem for me. edit /lib/udev/rules.d/40-libsane.rules with this information:
```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
```

More information regarding this at Brothers own site: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

Now Simple Scan and XSane finds my scanner and can scan without any problem.


The problem before was also that the earlier guide wanted to edit the  file /etc/udev/rules.d/45-libsane.rules but it have changes name and now  is  /lib/udev/rules.d/40-libsane.rules.

---

