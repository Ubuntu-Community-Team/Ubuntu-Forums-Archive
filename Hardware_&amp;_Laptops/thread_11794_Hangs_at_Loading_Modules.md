---
title: "Hangs at Loading Modules"
date: 2005-01-19
forum: Hardware &amp; Laptops
---

### Post by hongyihu on 2005-01-19
I switched over to Ubuntu about two weeks ago.  I didn't have this particular issue until about a week ago.  I'm running kernel 2.6.8.1-4-386, and I'm also using ndiswrapper to make wireless work.  This is for a Dell Inspiron 600M.

Sometimes when I boot into Ubuntu, the system will hang at the "Loading Modules" message and not go anywhere.  Booting into "recovery mode" will often work, though sometimes it hangs at a ndiswrapper message.  This problem occurs for kernel version 2.6.8.1-3-386 as well.  When this happens I look like a moron in public repeatedly restarting my machine to see if it will complete bootup :)

---

### Post by tux61 on 2005-01-19
Same problem here (Dell Latitude D800) !
My "solution" for the moment :
Don't load ndiswrapper on boot (remove it from /etc/modules). You need to  load it after boot with a "modprobe ndiswrapper".

---

### Post by Seth on 2005-02-05
[QUOTE=tux61]Same problem here (Dell Latitude D800) !
My "solution" for the moment :
Don't load ndiswrapper on boot (remove it from /etc/modules). You need to  load it after boot with a "modprobe ndiswrapper".[/QUOTE]
 Is there any better solution? I suppose this is acceptable, but it's sure not drop-dead simple like my SuSE install... or Windows XP.

---

### Post by crashd on 2005-07-26
[QUOTE=tux61]Same problem here (Dell Latitude D800) !
My "solution" for the moment :
Don't load ndiswrapper on boot (remove it from /etc/modules). You need to  load it after boot with a "modprobe ndiswrapper".[/QUOTE]
I have the same problem but in /etc/modules i have only:

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
nvidia

Any ideas?
thx

---

### Post by alesis on 2005-07-27
:| I'm running on Latitude D600 with Broadcom (or Dell) 1350 card. This is what I have: if booted in failsafe mode, ndiswrapper never hangs the boot on my machine, even though it does get loaded. If I do failsafe then shutdown -r (to reboot right after safe boot) normal mode boot never hangs. Also I've noticed that ndiswrapper shares same interrupt (5) with Intel 82801 (whatever the hell that is) which I cannot change (or don't know how, most likely). Could this be a problem?  Any input will be a big help, thanks!  ](*,)

---

### Post by pjman on 2005-10-19
I'm having this same problem on a Dell Latitude D600 running 5.10. Is there a fix?

-pjman

---

