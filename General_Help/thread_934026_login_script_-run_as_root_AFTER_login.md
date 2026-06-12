---
title: "login script -run as root AFTER login?"
date: 2008-09-30
forum: General Help
---

### Post by bazzer on 2008-09-30
I've got an ELO touch screen device that only seems to pop into the /dev/input/ directory after you're logged in. 

To use the ELO calibration routine, you must have permissions over /dev/input/elo and the install guide says to chmod them to 777. And this works - log in, drop to a shell, sudo chmod it and pop back to Gnome and all is very well indeed. So I added a line to rc.local to chmod it but it doesn't work. After I'm logged in I check the permissions and they're still at default.

So what next then? Every time I boot, the device's permissions are reset and I don't seem to have control over them. I did a rather clunky workaround with the root's crontab running every minute but I'm sure there's a far more elegant solution..... Anyone?

---

### Post by justleen on 2008-09-30
you could add that command to the /etc/sudoers file, and then run in from your .profile as a normal user?

just a thought..

---

### Post by bazzer on 2008-09-30
Good idea, quick too! Unfortunately, I don't want the normal user to be able to chmod things... I tried making a script that just included the chmod command, but even after wrestling with vi (visudo is EVIL!!) I couldn't make it work...

---

### Post by 3rdalbum on 2008-09-30
Make sure that when you put the chmod command into rc.local, that it doesn't have "sudo" in front of it. Rc.local runs as root anyway.

If you need a script to run as root without prompting for password, make it root owned and enable the setuid flag. You can do this in the GUI:

1. gksudo gconf-editor
2. Somewhere in the Nautilus settings in gconf-editor there's a setting called "Use Advanced Permissions". Make sure this is enabled.
3. gksudo nautilus
4. Find the script you want. Right-click it and go to Properties, then the Permissions tab. Change the "Owner" to "root", and click the "Set user ID" checkbox.

Now whenever you run the script, it will automatically run as root.

Be careful with setuid scripts; use them sparingly. Good luck!

---

### Post by bazzer on 2008-09-30
Further ramblings...
Doing anything in rc.local has no effect. I tried chmodding in there, nothing happened. I made a script and put the script location in there, still nothing. So I enabled 'chmod' for the normal user in the sudoers file and had the script I wrote fire with .profile - and this worked....

So I am starting to believe the rc.local isn't the last thing to run.... Any further ideas?

---

### Post by bazzer on 2008-10-20
it's a phrase I don't like, but....

BUMP... :confused:

What user does rc.local run as? I appreciate the above by 3rdalbum, but if it was running as root, surely my first attempt would work?

The only way I have been able to do this so far is by adding the chmod command to the root crontab and having it run every minute. But that's a HUGE bodge.

---

