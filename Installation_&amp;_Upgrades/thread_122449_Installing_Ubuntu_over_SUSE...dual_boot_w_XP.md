---
title: "Installing Ubuntu over SUSE...dual boot w/ XP"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by DisposableHero on 2006-01-27
I have my harddrive partitioned.  /hda1 is windows and /hda2 is where my nonfunctional suse is /hda5 is the swap area.  I've only been toying with linux for about a week now (noob :)).  I installed Ubuntu several days ago on the /hda2 but then tried SUSE.  Now I want to go back to Ubuntu and when im installing I noticed something that I don't remember from the first install.  on /hda2...where my Ubuntu will be located...should the boot flag be "on"?  I started wondering if that meant whether or not it would install GRUB because I still use XP...hence the dual boot that it was set up with.  Any help would be greatly appreciated.

---

### Post by Alpha_toxic on 2006-01-27
Just do the same thing you did the first time you installed it. The boot flag should be "on", as you're going to boot from that pratition. This has nothing to do with installing GRUB. If Ubuntu detects that XP is present on /hda1 , than it's safe to install GRUB on the Master Boot Record (MBR), but if you plan to remove all Linux from you'r machine at some later poin it would be better not ot install GRUB on the MBR, but find a you to boot Ubuntu from XP's boot loader. ATM I can't tell you how to do that, but I'll google it and i may post sth later.
good luck :)

---

### Post by DisposableHero on 2006-01-27
Awesome.  Thanx alot.  I know this doesn't pertain exactly to my thread topic...but...does anyone have any suggestions on learning the codes for terminal and all of that?  books, websites, doesnt matter.  Thanx again. :)

---

### Post by Alpha_toxic on 2006-01-27
Well about XP' boot loader - it's possible but I wouldn't do it...
[Here]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_to_Dual_boot_with_XP_2000_NT_and_install_linux_windows_whenever_You_want") and [here]("http://hacks.oreilly.com/pub/h/2337") it's explained how.
About the commands: [here]("http://www.ss64.com/bash/") is sth I just found, but you are not going to need most of these. Basicaly you need to know just about a dozen or so.
[COLOR="Red"]cp[/COLOR] = copy
[COLOR="#ff0000"]mv[/COLOR] = move or rename files or dirs (basicaly moving a file to the same dir with other name equals renaming it)
[COLOR="#ff0000"]cd[/COLOR] = change dir ("cd .." is "one level up")
[COLOR="#ff0000"]mount[/COLOR] and [COLOR="#ff0000"]umount[/COLOR] = mount and unmount devices
[COLOR="#ff0000"]dir[/COLOR] = list everything in the current dir
[COLOR="#ff0000"]ls[/COLOR] = same as dir, but with some colours :)
and of course:
[COLOR="#ff0000"]sudo[/COLOR] = put this before any other command to do it as administrator.
[COLOR="Red"]apt-get <install> <remove> <update> <upgrade> package name[/COLOR] = install stuff from the repos. You can use Synaptic for that.
[COLOR="#ff0000"]killall <proc name>[/COLOR] = stop a process that has gone wild for some reason (crashed, hanged...)

Basicaly most programs corespondent to a command exactly the same as the prog's name. Some are not exctly the same - like [COLOR="#ff0000"]ooffice2[/COLOR] will start OpenOfice. Try a programs name and [COLOR="#ff0000"]--help[/COLOR] or [COLOR="Red"]-h[/COLOR] after it or [COLOR="#ff0000"]man[/COLOR], [COLOR="#ff0000"]info[/COLOR] or [COLOR="#ff0000"]help[/COLOR] before it. This should give you basic info on what the exat syntax is. If you type the first 2-3 letters of a command and press TAB a few times it will give you a list of all posibilities. If you press TAB a few times without typing anything it will give you a list of ALL commands - better don't do that as they are more than 2000...
Happy Ubunting/Command Lining  :D

Edit: you might try [this]("http://www.er.uqam.ca/nobel/r10735/unixcomm.html") as well. I haven't checked exactly what it's like, but it looks good.

---

