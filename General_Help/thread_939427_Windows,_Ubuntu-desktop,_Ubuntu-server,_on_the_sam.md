---
title: "Windows, Ubuntu-desktop, Ubuntu-server, on the same hard drive?"
date: 2008-10-05
forum: General Help
---

### Post by dividenot on 2008-10-05
I've read a couple things about multibooting windows and ubuntu and, booting, i have no problems.  Except that the grub bootloader installation isn't as efficient as i'd like it to be - my grub for ubuntu server comes up first and then when i select windows xp it runs the nt loader, or wubi loader(not sure which one it is) and from there i can select between windows and ubuntu desktop.  ideally i'd like them all on the same list.

however, that's not my main issue.  my main question is if having windows, ubuntu-desktop, and ubuntu-server all on the same hard drive will cause any problems if i wanted to utilize all three environments?

like i said, everything is installed and i have the disk partitioned more or less the way i'd like it.  i'm just kind of low on resources, disk space for one, and i would like to have the desktop environments run sometimes and the server at other times.

---

### Post by pytheas22 on 2008-10-05
You can install all three operating systems on the same hard drive, sure.  The only major disadvantage is that you waste some disk space.

Also keep in mind that if you just don't want to have a graphical interface running sometimes, you can stop X by typing:
```

sudo /etc/init.d/gdm stop
```

and start it later with:
```

sudo /etc/init.d/gdm start
```

So maybe you can just have normal Ubuntu installed, and kill the graphical server when you want it off.  Then you wouldn't have any need for Ubuntu server edition.

As for the boot menu issue, unfortunately I don't think there's a way to get around that.  The MS NT bootloader is of course closed and undocumented, and the best that grub can do is "chainload" into the MS bootloader.  If you had installed Ubuntu desktop to its own partition instead of using wubi, you wouldn't have this problem, though.

---

### Post by dividenot on 2008-10-06
Thanks alot.  I'll look into those options.

---

### Post by eldragon on 2008-10-06
exactly, why have a server and a desktop environment...

you could install the desktop environment alone and then add server daemons as you need them. thats what ive done for a mixed environment here...

if you installed through wubi, like the previous post pointed out, you cant get it in the main boot screen.

---

