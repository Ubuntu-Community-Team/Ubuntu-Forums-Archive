---
title: "Problem after upgrading 8.04 to 8.10"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by k956411 on 2008-12-16
Since upgrading my system to 8.10 i have had a few issues.
i no longer have sound which i never had a problem with.
My wireless which always worked excellent nows drops out all the time with an error saying "ipw2200 firmware error detected restarting"
and i use a laptop hooked up to another monitor. before i could set it to 1280x1024. now it wont allow any bigger than 1024x768.

Has anyone got any ideas to fix these problems? or else does anyone know how to revert back to 8.04?

Cheers

---

### Post by albinootje on 2008-12-16
> **k956411 said:**
>  or else does anyone know how to revert back to 8.04?

Backup your data, and do a fresh installation of 8.04.

---

### Post by Master Chief on 2008-12-16
I also ran into a few annoying problems, but I won't revert back to 8.04 and I won't advise you to do this, but instead I like to see this kind of issues fixed/resolved. Don't you?

Please note that my problems are different, but also appeared right after the update.  Which is unfortunate for me, and very annoying, but reverting to a previous version is not a solution.

I would advise you to add more information, missing information, like the brand and type info of the installed video adapter and the used monitor.

---

### Post by gbc on 2008-12-17
I had similar problems after upgrading.  To fix the sound I had to reinstall the linux- sound-base, alsa-base, & alsa-utils.  There is a guide that helps debug sound problems called "Comprehensive Sound Problem Solutions Guide.  [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Seba Veron on 2008-12-22
I have also had sound problems after upgrading from 8.04 to 8.10 on my Lenovo 3000 Y410.  My soundcard worked before but since I upgraded it doesn't work.  I have referred to the guide below, the Comprehensive Sound Problems Solutions Guide v0.5e

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

My soundcard is listed when I type "lspci" into a terminal and I have been able to open the graphical mixer ALSA so I know that is not muted.  I have also been able to identify my soundcard (HDA Intel) from the Alsa project website.  If anyone can point me in the direction I need to go from here, I would be grateful.  I don't understand much of the lingo bandied about here, so clear newbie instructions would be greatly appreciated.

---

### Post by k956411 on 2008-12-23
thanks guys but i have tried the comprehensive sound stuff to no avail.
for some reason my system recognises my audio no problem "Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller" but alsamixer will only show me pulse audio. so i'm not sure whats happening here.

my video card is "Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)" as recognised by the system which is an onboard chip for my thin and light laptop.

and finally my wireless is an intel ipw2200bg.

Master Chief. i too would like to see these bugs fixed without having to revert to a previous install and if it was just a case of having a lower resolution for the extra monitor plugged into my laptop i wouldn't care. but if a i have no sound and cannot get on the Internet for more than 5 minutes then my system is unusable to me.

one of the main reasons i use ubuntu on the laptop is that for some reason (still unknown why) even with the latest drivers under windows i cannot get speeds above about 200kbs  when downloading anything. while under ubuntu on the same system i never get less than 800kbs.
if the wireless now does not work properly its a waste of my time.
you have said that reverting to an older install is not a solution but have not given an alternative. 

its not very helpful and reminds me of a post i recently put on a mac forum (crazy OVER enthusiastic people on there let me tell you)
i specifically asked for help with a linux script i was trying to create on a macbook pro (triple boot system) i specifically stated why i HAD to use linux, why my script HAD to do what i stated but yet i got nothing but a bunch of replies stating i should be able to do anything i wanted under mac and didn't need linux and another bunch of replies asking why i would want to do what i asked.

in total i got 43 replies and not a single one tried to actually answer my question, just asked irrelevant questions or gave irrelevant suggestions. and as far as i'm concerned, posted for the sake of increasing their post count.

I enjoy using linux and think ubuntu is one of the best but if something i need doesn't work i don't have time to wait for a fix before i do anything. i'm happy to send in any information the developers think may help to fix it in the future but i need it working now. hence my question.

---

### Post by albinootje on 2008-12-23
> **k956411 said:**
>  I enjoy using linux and think ubuntu is one of the best but if something i need doesn't work i don't have time to wait for a fix before i do anything. i'm happy to send in any information the developers think may help to fix it in the future but i need it working now. hence my question.

I think it's no big deal to go back to 8.04 esp. because you had everything working well.

Today i showed a co-worker the BBC-plugin in Ubuntu 8.10 inside VirtualBox (a totem version which is, as i read, apparently too difficult to backport to 8.04), he asked me about upgrading the desktop to 8.10, but i prefer to stick to 8.04 on certain machines. Long term support till 2011 is pretty cool to have.

---

