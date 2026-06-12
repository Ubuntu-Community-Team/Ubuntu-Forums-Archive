---
title: "Can't install command-line from Alternate CD"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by RatTub on 2008-12-03
Today I tried installing a command-line only version of (k)unbuntu from the alternate CD.

The first this I saw when booting from the CD was a black screen with the word "Boot: ". No options or anything.
I typed "help" to see what options I had and I was shown options from F1 to F12 describing different installation parameters.
Some of the options described were "install", "expert", "cli" and "cli-expert".
When I typed "cli", it didn't work. So I typed "install cli" and the installation started.

I was taken through the usual steps to configure my paritions, keyboard layout, time zone, etc.  But when the installation finished, I was taken to KDE.

Am I missing something or is there something wrong with my computer?  This is an older computer (Compag Deskpro Pentium 3 500mhz)

Any help would be appreciated.
Thanks!

---

### Post by icanfly0307 on 2008-12-03
What speed did you burn the CD at? If it's at the max speed, then the burn will have errors. Try burning the CD again at the slowest speed possible.

---

### Post by RatTub on 2008-12-03
The installation worked fine on another computer tho... the problem only comes up with this old one.

---

### Post by oldos2er on 2008-12-03
You could remove all the KDE packages if you don't want them installed. Am I right in thinking you want vanilla Ubuntu with no graphical interface?

---

### Post by RatTub on 2008-12-03
Yes, I tried uninstalling KDE using this:
[http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)
without the "sudo apt-get install ubuntu-desktop" command at the end. 
But now when the computer boots, all I get is a blank screen. No cursor, prompt or anything.
I can still use ssh, but I'd still like to fix this...

---

### Post by oldos2er on 2008-12-04
> **RatTub said:**
> Yes, I tried uninstalling KDE using this:
[http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)
without the "sudo apt-get install ubuntu-desktop" command at the end. 
But now when the computer boots, all I get is a blank screen. No cursor, prompt or anything.
I can still use ssh, but I'd still like to fix this...

 I don't know if this will fix your problem, but it couldn't hurt to try. Reboot, and when the grub menu comes up, hit "e". You want to edit the "root" line, removing vga=xxx, where "xxx" is a number, usually 795. Only remove that part, nothing else. Then hit "b" to boot. Let me know what happens.

---

