---
title: "Ubuntu won't boot on Lenovo ideapad 110s-11IBR"
date: 2017-04-15
forum: Hardware
---

### Post by adamrclemons on 2017-04-15
Hello!

I recently purchased a ideapad 110s-11IBR.  After trouble shooting it, I was able to install Ubuntu just fine.  However, now, when I boot the only options I get are the hard drive #1 "eMCC Disk: Hynix 32gb" and #2 "Windows Boot Manager."

There are no other options and selecting both does not boot into Ubuntu.  I tried installing fedora, just to see if it made any difference and that did the same thing.  So, I tried ubuntu again and still.. the same problem.

I'm now stuck.  Any thoughts what I should do next?

---

### Post by oldfred on 2017-04-15
LENOVO Ideapad 100S Laptop  32 bit UEFI bootia32.efi
[URL="https://ubuntuforums.org/showthread.php?t=2350606"]https://ubuntuforums.org/showthread.php?t=2350606
[/URL]
 Lenovo 110s  My Experience Installing and Using Linux on my Lenovo 110s UEFI settings better support than 100
[https://ubuntuforums.org/showthread.php?t=2350394](https://ubuntuforums.org/showthread.php?t=2350394) 

Many  Lenovo's have to have a work around to boot Ubuntu.
      
 Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186) 
    [       ]("https://ubuntuforums.org/showthread.php?t=2350606")
 Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114) 
    [URL="https://ubuntuforums.org/showthread.php?t=2350606"]
[/URL]

---

### Post by dayvkaos on 2017-08-12
Im using linux on Lenovo Ideapad 110s currently.

Was it ever working?

---

