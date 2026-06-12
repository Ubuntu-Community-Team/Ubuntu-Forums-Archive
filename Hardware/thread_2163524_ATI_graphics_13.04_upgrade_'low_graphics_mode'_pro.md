---
title: "ATI graphics 13.04 upgrade 'low graphics mode' problems"
date: 2013-07-18
forum: Hardware
---

### Post by hans12345 on 2013-07-18
I have many problems with my current configuration, which is

Homebuilt desktop, with AMD X3 425 CPU and integrated Radeon HD 4200 graphics.

Currently the system is dead having failed the upgrade from 12.10 to 13.04, except that it is a dual boot with Win XP which still works.

Some time ago, when I did the 12.04 to 12.10 upgrade, I had driver problems. I think it was with the 'nouveau' driver, which I replaced with an AMD ATI one.

Recently, I did a normal online upgrade to 13.04, I got the famous 'running in low graphics mode' problem.

Steps taken so far:

1. Tried various updates to fglrx, failed
2. Discovered that AMD no longer support my HD 4200. So I tried the Makson trick (http:// [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)), which I had used successfully on another PC upgrade to 13.04, which had worked.
Here it did not work.
3. I downloaded the DVD and tried  a 'repair' install. But this failed early on with Grub not installing properly. I could have set up a new version of Grub on a different partition, but was worried about the Win XP dual boot. Knowing what a pig Win XP is with dual boot, I really do not want to disturb my dual boot. Going down this path could easily require a full Win XP re-install.

So, I need some ideas.
- clean up any old traces of fglrx and then try the Makson trick again?
- clean up any old traces of fglrx and try with Nouveau drivers? They failed me in 12.10 but maybe things are different now?
- find a way around the Grub problem?

Thanks for any advice

Hans

---

### Post by QIII on 2013-07-18
Hello, hans12345!

To be perfectly honest, those hack methods break your install in ways that are unpredictable.  You now have a downgraded X Server, a legacy driver and some kernel changes.

I have been recommending against those methods since they first started appearing and you are not the first person to encounter this.

Your best bet, if you really want to use Raring, is to simply use the default open source Radeon driver, which is installed by default, and leave it alone.  The problem is, because you have done several things there is no telling at this point what state your machine is in to know how to get it clean.

I don't generally like what I call the "Blast off and nuke 'em from orbit" method -- reinstalling -- but this is one of those cases where that might be necessary.  Did you back up your important files?

If you reinstall, be sure to do a manual partitioning and preserve your /home without formatting it.

I *really,** really*** wish those hacks would be taken down.  I think those who still recommend them are irresponsible.

Best wishes.

---

### Post by hans12345 on 2013-07-18
Thanks QIII

Sound advice, but if I go for a clean install, I shall have the Grub problem, and I fear trying to start again and have to re-install Win XP.

I'll keep this as a backup solution.

Is there something else I can try first?

Hans

---

### Post by jp734 on 2013-07-18
Did the install created an xorg.conf file for you? If it did, you can edit the file and change the driver to "radeon" or perhaps "vesa". I think that will do the trick for you.

---

### Post by Yellow Pasque on 2013-07-20
1. Make sure you clean up after any fglrx stuff: [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx)
2. Use ppa-purge to get rid of any remaining makson packages (if any):
```
sudo ppa-purge ppa:makson96/fglrx
```
3. Restart, and if still in low graphics mode, post your /var/log/Xorg.0.log, and use [ code ][ /code ] tags.

---

### Post by hans12345 on 2013-07-30
Wow, 1 week without 13.04 and no forums! Actually, I have Xunbuntu on 2 older PCs, so life has gone on.

But I've tried a lot of things in the last seven days, all the suggestions that anyone has even posted! Still no luck. My current installation must be messed around.

I've ordered a new ATI graphics card that should come tomorrow. Today I did Clonezilla backups. So after the card is installed, I'll go ahead and to a new install from the LiveCD.

Thanks to everyone who offered help.

---

### Post by hans12345 on 2013-08-01
Well, the card came but I miss the DVi-D cable, so I went ahead anyway without the new card.  With the install from the LiveCD:
- reinstall failed
- clean install worked.

And the Win XP boot was not disturbed.

Story ends happily, but if the forums were not down last week, maybe I could have found out what was wrong with my old installation. But I did learn lots about Linux.

Thanks everyone

Hans

---

