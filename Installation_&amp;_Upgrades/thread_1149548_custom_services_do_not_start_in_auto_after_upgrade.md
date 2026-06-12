---
title: "custom services do not start in auto after upgrade to 9.04"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by pico on 2009-05-05
Hi!

I have 2 PC with installed some custom application (one of this is NAGIOS and the other is DEKIWIKI).

I have performed a double Upgrade on this 2 PC from 8.04 to 8.10 and then to 9.04.

Now, everuthings seems ok, but some custom service (inside /etc/init.d/) that have to start at boot automatically, do not work!

I have checked also with BUM, but even if service is active, do not start anymore, after upgrade.

I also tryed to put the command inside the /etc/rc.local but even in this way the service do not start. I have to run manually from command line (and it works!)

Can somebody help me to solve or to investigate (wich log I have to watch?) this stange problem??

THX

PiCo

---

### Post by m83 on 2009-05-05
What program do you want to run at startup? Generaly every daemon has it's log files. Try and find out where the program logs its stuff. Or see if the program has some kind of debug mode and try to run it in this way. Or run the program through strace (in the startup script) and redirect the output of strace to a file so that you can examine it later. Something like this:
```
strace -o/tmp/strace_output program
```

---

### Post by pico on 2009-05-05
Regarding the NAGIOS program the situation I have is very similar to this post:

[http://forums.meulie.net/viewtopic.php?f=61&t=4765&sid=dc19871c91e225cd0dc6b8d8c0d59012#p16227](http://forums.meulie.net/viewtopic.php?f=61&t=4765&sid=dc19871c91e225cd0dc6b8d8c0d59012#p16227)

BUT I have no APPAMOR installed. So I have no solution!

This is a very strange behaviour of Ubuntu 9.04.
No ideas ??

---

### Post by cebif on 2009-09-24
I had a similar problem see this:
[http://ubuntuforums.org/showthread.php?t=1266614](http://ubuntuforums.org/showthread.php?t=1266614)
I have partially solved it. If I stop the graphic booting process before gdm or kdm starts customized rc.local works. The problem for me is that every time at boot straight after the boot sequence I have to press "alt + f1". I am not certain how to make this permanent.
I know this post is late for you but I just found this out.
Any ideas how I can stop the graphic screen at bootup.
I think this problem must be a bug and a while ago posted a bug on launchpad but it was marked as invalid. It might have been marked this way because my report seemed more about the application that I wanted to start at boot "ups_mamager" but I ex;plained in the comments that it was probably a fault with both rc.local a only a slight problem with the application, that I could easily workaround.
I might try reposting another bug report if someone else hasn't already done so.

---

### Post by cebif on 2009-09-25
I've found how to stop the graphical boot.
I edited menu.lst
```
title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=915a4563-e2ee-4842-999f-f4c55be09bf8 ro [COLOR="RoyalBlue"][COLOR="Lime"]quiet splash[/COLOR][/COLOR]
initrd		/boot/initrd.img-2.6.28-15-generic
quiet
```
The colored text is deleted.
After a reboot I found the application was started by rc.local.

---

