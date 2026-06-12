---
title: "Having troubles installing Ubuntu on custom rig"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by sirvyper4580 on 2008-12-23
Alright, I'd like to warn you that I am completely new to Linux, so I apologize if the solution to this problem is painfully obvious. I also warn that this post might be painfully long.

This is what I'm using atm: AMD Athlon(tm) 64 X2 Dual Core Processor, NVidia motherboard (can't remember exact model right now, it's about 2 years old), Radeon x1950 Diamond Video Card, G15 Keyboard, Logitech MX Revolution Mouse, 4 gigs of ram, 1 250gb hdd (SATA) and 1 1TB (SATA) hdd. Windows Vista Ultimate 64bit SP1 installed on the 250gb hd, the 1TB is used to install all my music, games, etc etc. 

I downloaded an ISO for Ubuntu 64bit, version 8.10 through the Ubuntu website. I originally tried to install a Virtual PC of it to check it out first. I would get the main screen with how to install Ubuntu and such, but wouldn't go further then that. So I figured I'd be bold and try to install it outside of VPC. I put the disc in and Wubi popped on. I set it up to install on D: (1TB HD) and use 30gb space. It kept saying there was an error reading the contents on the CD, I looked up on this forum actually how to fix the problem and none of the solutions worked for me. So I rebooted and boot to the CD. It gave me the option to check out Ubuntu before installing, awesome option btw, so I did so. I loved the interface and everything seemed so smooth. However, after a few actions here and there, it locks up completely.

I thought maybe the problem was the fact that I was using 64bit Ubuntu, so I DLed the 32bit version of Ubuntu. Wubi installed it without a hitch, it was rather quick actually. So I reboot, select Ubuntu in the Windows Boot Screen and after some seconds of booting, I go into DOS, unable to access my harddrives. I use DIR to check out the contents and I see Grub, Command.com, softmod, autoexec, but that's pretty much it. I tried getting into c: and d: with no luck. So I rebooted again, went to Vista this time and it booted up fine, my harddrives were intact and everything.

I tried the same thing with Xubuntu and it did the EXACT same thing, it would install using Wubi no problem, but would kick me into DOS with no harddrives.

So I'm lost, without completely reformatting C:, I'm not sure what else to do.

Update: I did try installing Ubuntu onto C: with Wubi and got the same results. Boots into DOS 6.22 with no access to my harddrives.

---

### Post by logos34 on 2008-12-23
well, if you've tried VPC and Wubi unsuccessfully, the next logical step would be to try installing on a dedicated partition.  Carve out space on the 1 TB drive--you can shrink it with Vista disk utilities or use Gparted on the live cd. Or let the ubiquity installer do it with either 'Guided--use largest continuous free space' option or 'manual' (If it freezes up on you again, try using the text-based [Alternate Install CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").)

---

### Post by sirvyper4580 on 2008-12-23
Thank you for your assistance!

I got Ubuntu to install with the Alternate disc no problem. Took about 100gb from the 1TB harddrive and used it to install Ubuntu. Everything went by smoothly.

However, now with Ubuntu, it constantly restarts after a few minutes of use. Sometimes it'll freeze or restart before I can even log in. I did a mem test to see if I had bad memory, but it passed.

---

### Post by logos34 on 2008-12-24
You might search for clues over at launchpad bug reports:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

You could also try 8.04 Hardy--it's better supported (LTS release) and maybe you'll be lucky and not have any issues. (it's what I plan to run for the forseable future--almost everything 'just works')

good luck

---

### Post by logos34 on 2008-12-24
[delete--duplicate post]

---

### Post by sirvyper4580 on 2008-12-29
Thank you for all your advice... Here's my situation now as it stands.

I got Ubuntu 8.04 (x86 version) installed. I ended up completely reformatting my C: drive and used the Guided partition to create the swap partition and such. I still had to use the Alternate disc to install Ubuntu sadly, but what can one do?

After that, Ubuntu ran pretty stable for a while, the best it has ever ran on my PC. I was able to activate my Video Card (Radeon X1950 Diamond) and was able to use some of the enhanced Desktop features. Played a couple of games before getting too involved just to make sure it wouldn't crash and it worked fine. Then a message popped up that I needed to install 214 updates, normal for a clean OS install (atleast normal for a typical Windows user like myself).

I went ahead and tried to install the updates. It downloaded them all just fine, however when it came to installing them, my system froze half-way in (It looked like it froze on a Kernel update perhaps?). I had to hard-reset the comp. Ubuntu froze before it could start up. I used the Recovery Mode, repaired broken packages (which ended up installing the packages I downloaded it seemed) and went to boot as normal. It allowed me to sign in no problem, then I went to use Firefox and it crashed on the second page I loaded up (Google to be precise). I hard-reset again and avoided using Firefox. I used Add/Remove to install a couple of other games to check out and it froze on install again. I also on occasion deal with a random reboot, though I think that might have something to do with my BIOS, not sure to be honest.

So if I had to guess, it seems that my problem is somewhere along the lines of installs/updates. I just don't know what would cause the issue, nor how to fix it.

---

