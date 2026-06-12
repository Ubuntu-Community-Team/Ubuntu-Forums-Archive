---
title: "Scanner doesn't work in Ubuntu 18.04."
date: 2018-10-02
forum: Hardware
---

### Post by vitalyam13 on 2018-10-02
Hello, I need help. Recently I bought new multifunction printer Samsung Xpress SL-M2070, installed drivers from HP site called ULD(scanner+printer driver for Linux systems), but Scanner doesn't work(Printer works find). Why? I tried to contact with HP support team, but they said that Linux system isn't supported and they can't help me;(

---

### Post by davidbowie2nl on 2018-10-14
Hello,

yesterday I had the same problem with a [FONT=arial][SIZE=2]Samsung Xpress SL-C460W Color Laser Multifunction Printer and the ULD_V1.00.39_01.17
version after upgrading to Ubuntu 18.04. Reinstalling after the upgrade did work for the printer but not for the scanner.

I was able to fix it for my situation in the following way:

The reason it didn't work for me is that the install-scanner.sh script does the configuration properly for sane, but
then copies the .so files into a folder that Ubuntu 18.04 does not expect, while this used to work in Ubuntu 16.04 (32 bits).  
In my case it was: /usr/lib/sane, while all the other scanner drivers were located in  /usr/lib/i386-linux-gnu/sane.

copying the libsane-smfp.* files to [FONT=arial][SIZE=2]/usr/lib/i386-linux-gnu/sane and then starting xsane from the console did the trick for me.

I don't know if this is an Ubuntu bug or an outdated Samsung installation script thing (the version of the script was released in 2017).

If anyone knows if I should report this to HP as a bug (as the ULD is still listed on their site) and more importantly how,
please let me know.

Hope this solves it for you as well.

 [/SIZE][/FONT]
[/SIZE][/FONT]

---

