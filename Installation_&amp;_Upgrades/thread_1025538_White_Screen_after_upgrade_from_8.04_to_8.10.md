---
title: "White Screen after upgrade from 8.04 to 8.10"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by Siedorf on 2008-12-30
Hello.

Specs: Intel Core2Quad Q9450 @2.66 Ghz, 4 Gb Ram, ATI Radeon EAH 4850.

After upgrade from 8.04 to 8.10 I reboot and get a white screen. I have access to TTY, but no graphic mode.

Can anyone help me on this one? 

Best Regards

---

### Post by wizard10000 on 2008-12-30
Do you get the white screen before or after the gdm login screen?

Just for fun try creating another user and see if the new user also has the same problem - from a terminal session:

sudo adduser *username*

then add the user to the admin group so you can use sudo if necessary

sudo useradd -G admin *username*

Log on as the new user and see if you still get a white screen - if so, X is broken - if not your user profile is broken.

---

### Post by Hydrid on 2008-12-30
I had the same problem and the solution was to install 8.10 from the cd with no graphics support in the beging of the installation.When u boot from the cd it has an option (i think its f4)to choose to install with generic graphics driver.Hope this helps you.

---

### Post by stderr on 2008-12-30
If you login to the TTY and execute

```
startx
```

is there any useful info/errors printed to screen? (startx just tries to START your X window environment, much like gdm would ordinarily do after you've logged in). 

It may also be helpful if we have the output of this command:

```
glxinfo
```

(normally glxinfo is a good place to start debugging gfx driver issues).

It may be wise to try wizard's suggestion first, as if it is an account issue this will just take you off on a different tangent.

---

### Post by teaker1s on 2008-12-30
it's compriz you need to switch window manager-trying to find post discussing this issue

Are you able to login via the normal GUI and THEN it goes to a white screen. If so this may be an issue with compiz/desktop effects. To get your gui back

> 1.login as normal, wait till the login sounds are finished allowing enough time for all your normal stuff to load (panels nautilus etc.)
2.press alt-f2 to bring up the run application dialog (obviously you won't see it but it should be there)
3.enter "metacity --replace" without the quotes and press enter

With any luck metacity should kill compiz and replace it as you window manager giving you you gui back. To make this change permanent go to system>prefs>appearance and turn of desktop effects.

---

