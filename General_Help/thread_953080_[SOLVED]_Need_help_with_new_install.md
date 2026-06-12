---
title: "[SOLVED] Need help with new install"
date: 2008-10-19
forum: General Help
---

### Post by Ironhorse_somo on 2008-10-19
Background info:
I am trying to dual boot WinXP Pro(SP2) and Ubuntu 8.04.1 LTS Desktop edition (the disc was received from Ubuntu via snail mail - not burned on my computer.) My computer was built for me by a local shop and is not any name brand. After playing with Ubuntu a little on the disc, I did an "Install in windows" and put it on it's own hard drive.

The problem:
Now, When I highlight the Ubuntu option when choosing between OS'es, it goes into the Ubuntu start up screen, then kicks me to a "DOS looking screen" with the following message:

Busybox v1.13 (Debian 1:1.1.3-5ubuntu12)Built-in shell (ash) Enter 'help' for a list of built-in commands.
(Initframs)

And I am unable to proceed any further. Yes, I am a complete newbie to Ubuntu. Help?

---

### Post by alzie on 2008-10-19
What it looks like you were doing is a Wubi install.  Unfortunately it's beyond me to help other than to give you the links to the wubi forum and the the wubi guide.  Hopefully you can find an answer or post a question there and get the appropriate help.

WUBI forum  [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

Wubi Guide [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

I hope this helps you.

---

### Post by Bucky Ball on 2008-10-19
Couple of ideas. Was Windoze shutdown correctly? Maybe open Windoze and shutdown from there then try again.

You could try installing using the alternate cd. This has been known to eliminate the problem although I think this is because it is not a Wubi install.

Wubi installs sometimes produce this error and fixes tend to vary. You may want to have a dig in here:

[http://au.altavista.com/web/results?itag=ody&q=Busybox+boot+ubuntu&kgs=0&kls=0](http://au.altavista.com/web/results?itag=ody&q=Busybox+boot+ubuntu&kgs=0&kls=0)

This looks promising, even though for Gutsy, there is a fix. Could well work in Hardy also but I would go for the open and close Windoze first up. 

[https://answers.launchpad.net/ubuntu/+question/5429](https://answers.launchpad.net/ubuntu/+question/5429)

The upshot is to enter this on a command line:
```

update-initramfs -k 2.6.17-11-i386c -c
```

You may need to put 'sudo' at the beginning of this command. Hope this gets you somewhere. :)

---

### Post by Ironhorse_somo on 2008-10-19
update-initramfs -k 2.6.17-11-i386c -c

Tried that command line (?) No dice.

---

