---
title: "updatedb problem"
date: 2008-11-08
forum: General Help
---

### Post by V00D00M0NKY on 2008-11-08
Hi I was using GNOME-do and was trying to use their locate files plug-in and it wasn't working so I looked deeper into it and it says it uses GNU locate. Reading further I found that reads from `/var/lib/mlocate/mlocate.db', updated by updatedb, initialized by cron. So looking at the man pages for each I tried to run updatedb and got:

 " `/var/lib/mlocate/mlocate.db'"

so i looked further into the man pages specifically cron's and i found that if "cron -L" is set to 0 it won't run updatedb. so i tried to change "cron -L" to 2 and got: 

" `/var/lib/mlocate/mlocate.db'"

Am I doing something wrong to begin with or is there something somewhere else that I have to fix?

---

### Post by soro2005 on 2008-11-08
How is gnome-do not working? In the first field, you type "locate files," in the second field, you type what you want to locate, and the result should be the same as when you type```
locate xyz
``` at a command prompt. Does that not do it?

In any case, before you screw up your cron tab, please try it out at the command prompt. If it works in the terminal, but not in gnome-do, then the problem is with gnome-do, not with gnu locate.

Also, cron's -L switch is about log level, not about running or not running particular commands.

---

### Post by V00D00M0NKY on 2008-11-08
ok... it wasn't finding as i typed like in the vid tutorial i saw... but when i hit enter it makes a list. but one question on top of that now that i realise how to use it properly, 

How do I add something like an external drive or a flash drive to mlocate.db?

---

### Post by soro2005 on 2008-11-08
You don't add anything to mlocate.db. It is maintained by gnu locate + cron, and unless you want to produce a major screw up with your system, you just keep your hands off of it and let it do its thing.

Locate has a certain lag, so it's not good for removable media. The lag is good, b/c if not, your computer would be updating the database all the time, and you couldn't use it for whatever it is you use it for.

You can use the files/folders plugin in Gnome-Do to locate files. It updates more frequently. I still don't recommend you have it index your removable media as that is going to produce a major mess and use a lot of cpu.

Bottom line: Your removable media will have to wait outside, for the time being.

---

### Post by V00D00M0NKY on 2008-11-08
alright... well then that just means that GNOME-do's locate isn't going to be as useful for me as I had expected.

---

### Post by soro2005 on 2008-11-08
> **V00D00M0NKY said:**
> alright... well then that just means that GNOME-do's locate isn't going to be as useful for me as I had expected.

Try files and folders plugin and put /media/Mountpoint-of-your-USB-drive into it's configuration as a path to be indexed. If you have the usb drive connected always or most of the time, then that might give you decent results. If not, it'll likely use a lot of CPU and not be good for anything.

---

### Post by V00D00M0NKY on 2008-11-08
ok well i can do that for my external HDD. that's connected via USB 24/7. with what you said i won't do that to my flash drive cuz that goes almost everywhere with me.

---

