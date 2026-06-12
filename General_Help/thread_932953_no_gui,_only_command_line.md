---
title: "no gui, only command line"
date: 2008-09-28
forum: General Help
---

### Post by spotsworth on 2008-09-28
hi,
i have a laptop(dell) that has been running well with gutsy, but today i came back to it and there is no longer any kind of graphical interface.  it was fine when i left it and i have no idea what was done to it in my absence.  when i rebooted it went directly back to the screen that only has the command line.

any help would be greatly appreciated.
-spotsworth

---

### Post by p_quarles on 2008-09-28
> **spotsworth said:**
> hi,
i have a laptop(dell) that has been running well with gutsy, but today i came back to it and there is no longer any kind of graphical interface.  it was fine when i left it and i have no idea what was done to it in my absence.  when i rebooted it went directly back to the screen that only has the command line.

any help would be greatly appreciated.
-spotsworth
Try running:
```
sudo /etc/init.d/gdm start
```
You may go an error message -- if so, please post it here.

---

### Post by spotsworth on 2008-09-28
there's no error message, the next line says:
Starting Gnome Display Manager...             [ok]

and then back to the command line...?

---

### Post by p_quarles on 2008-09-29
Try running:
```
echo 'gnome-session' > .xinitrc && startx
```
and see what happens there.

---

### Post by spotsworth on 2008-09-29
thankyou so much for the help.  i rebooted a third time and it seems to be okay.

---

