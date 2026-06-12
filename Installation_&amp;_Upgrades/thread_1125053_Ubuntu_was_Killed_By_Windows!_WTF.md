---
title: "Ubuntu was Killed By Windows! WTF?"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by PolloE on 2009-04-14
OK, so what happened was that after a looong time of using Ubuntu I re-installed windows, (I had 40 spear un-partitioned GB in my HHD and gave 30 to windows) but when the installationg was over (It's Windows XP Proffesianal SP3) i restarted my PC, and it loaded Windows right away, it skipped the boot options.

I tried turning on my PC again and pressed F12 (boot menu) and there was nothing but windows' options...

I loaded ubuntu demo from the CD, the original Ubuntu partiotion still exists with all my files; I tried copying my home folder but it wouldn't let me; WTF? it said is was private...

Is there anyway I can at restore my ORIGINAL ubuntu, or at least my HOME folrder?

Plz help!

---

### Post by kyle99 on 2009-04-14
You need to reinstall the grub loader.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by lisati on 2009-04-14
You might have to reinstall GRUB. Have a look here: [http://ubuntuforums.org/showthread.php?t=333210&highlight=insall+grub](http://ubuntuforums.org/showthread.php?t=333210&highlight=insall+grub)

---

### Post by PolloE on 2009-04-14
thx! i'll try that...

---

### Post by PolloE on 2009-04-14
I just wanna make sure before i screw up...

I typed:

[COLOR="Blue"]ubuntu@ubuntu:~$ Sudo Grub[/COLOR]

then i got "grub>" 
and i typed [find /boot/grub/stage1] and got this
"(hd0,4)
 (hd1,4)"


[COLOR="Blue"]grub> find /boot/grub/stage1
 (hd0,4)
 (hd1,4)[/COLOR]

then in the instructions from the other thread

>  Re: Insall WinXP next to existing Ubnuntu install?
This method will restore grub to the MBR of your first drive:

1. Boot from the Live CD

2. Open a Terminal.

3. Type "sudo grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hdx)"
[COLOR="Red"]
5. Type "root (hdx)". Whatever was listed by the above command. This tells grub where to look for menu.lst etc.[/COLOR]

6. Type "setup (hd0)". This writes grub to the MBR

7. Type "quit".

8. Restart the system. Remove the bootable CD.

in step 5 do i write...
a) root hdx   ?
b) root hd0,4 ?
c) root hd1,4 ?
d) or something else?

i just wanna make sure...

thx

---

### Post by lisati on 2009-04-14
The 'hdx' was an example. Quite likely the first - hd0 - will be the correct one to use.

---

### Post by PolloE on 2009-04-14
ok... so this is what i've typed so far

[COLOR="Blue"]ubuntu@ubuntu:~$ [/COLOR][COLOR="Red"]sudo grub[/COLOR]

[COLOR="Blue"]grub>[/COLOR] [COLOR="Red"]find /boot/grub/stage1[/COLOR]
[COLOR="Blue"](hd0, 4)
[/COLOR]
[COLOR="Blue"]grub> [/COLOR][COLOR="Red"]root (hd0)[/COLOR]

[COLOR="Blue"]grub> [/COLOR][COLOR="Red"]setup (hd0)[/COLOR]

[COLOR="Blue"]Error 17: Cannot mount selected partition

grub>[/COLOR]

Legend: Red is MY input, blue is the PC's output...

What do i do now? there is something wrong, im sure...

---

