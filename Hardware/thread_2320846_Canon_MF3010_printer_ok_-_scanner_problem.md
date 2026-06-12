---
title: "Canon MF3010 printer ok - scanner problem"
date: 2016-04-18
forum: Hardware
---

### Post by meridius2 on 2016-04-18
[SIZE=3]I have just installed Ubuntu 14.04.4 LTS 64-bit. I have a Canon MF3010 printer/scanner and got the printer part working by installing the deb drivers ([link here]("http://software.canon-europe.com/software/0044160.asp")) from the Canon website. Really this was completed by double clicking on the *cndrvcups-common_2.70-1_amd64.deb* and *cndrvcups-ufr2-uk_2.70-1_amd64.deb *packages in this order. This then went through the Ubuntu Software Centre and was installed. In fact now I have two printer setups with almost the same properties. This may be due to what I did when I tried to resolve the scanner problem through another link (see below):

Printer 1: Canon-MF3010
Device uri: usb://Canon/MF3010?serial=014B40000BF0&interface=1
Make and model: Canon MF3010 ver.2.7

 Printer 2: Canon-MF3010-2 (now set as default)
Device uri: cnusb:/dev/usb/lp0
Make and model: Canon MF3010 ver.2.7

The problem is now with the scanner. I looked online and found a few posts but followed the instructions in [this one]("http://jonathan.bergknoff.com/journal/scanning-ubuntu-canon-mf3010") which was exhausting, although I did not really understand or follow the comments below it (see my results below - personal information removed):

```

username@pcname:/usr/lib/x86_64-linux-gnu$ scanimage -V
  
scanimage (sane-backends) 1.0.26git; backend version 1.0.26
  
username@pcname:/usr/lib/x86_64-linux-gnu$ sudo scanimage -L

device `pixma:04A92759_014B40000BF0' is a CANON Canon i-SENSYS MF3010 multi-function peripheral

```

I uninstalled and installed Simple Scan. When I scan it comes up with a msg "Failed to scan: unable to connect to scanner", then comes up with a change scanner box with no options to select or deselect anything).

With XSane it comes up with a msg box "XSane 0.998 Scanning for devices" and then an error msg "Failed to open device 'pixma:04A92759: Access to resource has been denied".

I have also just uninstalled and reinstalled both Simple Scan and XSane and get exactly the same results whichever printer is set as default.

Any suggestions at this stage?[/SIZE]

---

### Post by karim-ratib on 2016-05-06
The message "Failed to open device 'pixma:04A92759: Access to resource has been denied" seems to indicate a permission issue. 

First, what happens if you run ```
sudo xsane
``` Same error?

Also, there's a permissions-related comment in that instructions link you sent: [http://jonathan.bergknoff.com/journal/scanning-ubuntu-canon-mf3010#comment-1772149607](http://jonathan.bergknoff.com/journal/scanning-ubuntu-canon-mf3010#comment-1772149607) - have you tried that?

---

### Post by meridius2 on 2016-05-07
I actually no longer have this os but moved to Xubuntu 16.04 LTS 32-bit on my spare laptop. I installed the relevant deb files from the link in my initial post: *cndrvcups-common_2.70-1_i386.deb* & *cndrvcups-ufr2-uk_2.70-1_i386.deb*.

 For some reason I just decided to check 'Simple Scan' and guess what it worked! I am really not to sure why. Perhaps some files have been updated in 16.04 or maybe as you mention there was a permissions issue in the previous install. It might just be a question of 32 vs 64-bit drivers or perhaps an incorrect procedure took place on the previous install. What is certainly the case is that the wizards don't pick up this printer/scanner automatically. I thought it should be in the CUPS database. The precise model is not even here: [http://www.openprinting.org/printers](http://www.openprinting.org/printers) However, this progress is a good step forward.

---

