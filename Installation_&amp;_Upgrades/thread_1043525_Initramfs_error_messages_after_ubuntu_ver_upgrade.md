---
title: "Initramfs error messages after ubuntu ver upgrade"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by BertP on 2009-01-18
I used the update manager to  upgrade from Ubuntu 7.10 to 8.04.  After reboot I get stuck with what I think are initramfs messages displayed using Busyboy 

most of the messages are a repeated pattern that seemingly never end; only the numbers in column one increase with the rest of the fields repeating. A new set of 3 messages are spit out after an interval of maybe 20 to 30 seconds.

-----------------

[ 320.45198 ] ata2:00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

[ 320.45198 ] ata2:00: cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in

[ 320.45198 ] ata2:00: status: { DRDY }

--------------------

Anyone have any idea what this pattern of 3 lines mean?

(note: I can get around this sometimes during the boot process by  hitting F12 to choose the  bootmenu, and then exiting to allow the  computer to boot from the harddrive .    When eventually I am able to get the harddrive to boot, 8.04 seems to work perfectly]

[note2:  I never had a problem with 7.10 for almost a year on this computer and Dell's extended hardware test shows no hard drive errors or any other errors]

[note3:  I am assuming that the "ata" in the error message is regarding something with the drives.  This computer has only 1 SATA hard drive, one R+W DVD and no floppy disk drive]

Thanks in Advance!

---

### Post by squee on 2009-01-18
Not sure what the lines mean, but if I were you,

1) Back up all important data, not forgetting bookmarks and passwords on FF.

2) install most recent version (8.10 at the moment)

3) enjoy!

shouldnt take more than an hour, a lot quicker than waiting the hour you have for a reply that doesnt even fully answer your question.

---

### Post by BertP on 2009-01-19
actually I tried that... not 8.10 but with Dell's special build of 8.04
first I reverted back to 7.10 then downloaded Dell's  8.04 iso and burned a DVD....   When running the DVD,  I got to the point of choosing which video card I have installed and I get the same damn messages before it even began copying files!

 I have tried installing 8.04  3 times... I particularly wanted that version because it will get long term support

Thanks for the help!

---

### Post by Partyboi2 on 2009-01-19
Try adding irqpoll as a boot option.
[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

---

