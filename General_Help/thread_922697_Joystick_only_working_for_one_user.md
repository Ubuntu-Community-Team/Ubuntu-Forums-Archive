---
title: "Joystick only working for one user"
date: 2008-09-17
forum: General Help
---

### Post by SailBlue5 on 2008-09-17
I have a Saitek Joystick/gamepad. It works well when I log on and I can play zsnes with it no problem. But when any other user logs in (one of which is mythtv) they don't see the controller and zsnes doesn't see it. Any ideas how to get it so everyone sees it?

Michael

---

### Post by unutbu on 2008-09-17
I do not have a joystick, so I don't have first-hand knowledge that this works.
However, going by the info on this page: [http://wiki.antlinux.com/pmwiki.php?n=HowTos.LinuxJoystickTroubleshooting](http://wiki.antlinux.com/pmwiki.php?n=HowTos.LinuxJoystickTroubleshooting), I think what you want to do is

[list]
[*]Make each user a member of the "games" group:

For each user who wants to use the joystick (but can't) run this:
```

sudo usermod -a -G games USERNAME
```

Change USERNAME to the correct username.
[*]Make the group ownership of the joystick device "games", and and make the device readable and writable by everybody:
```
cd /dev/input/
ls -l > ~/ls_dev_input   # Save the current state so we can revert if necessary.

```
```

for x in js*;do sudo chgrp games $x;done
for x in js*;do sudo chmod 666 $x;done
```
[/list]

---

