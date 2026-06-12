---
title: "NVIDIA Splash Screen"
date: 2008-08-21
forum: General Help
---

### Post by Captain666 on 2008-08-21
When Ubuntu loads, it shows its loading screen, then goes to an NVIDIA splash screen that shows the NVIDIA logo. Ive always just put up with the splash screen, but im getting sick of seeing it and having to wait the extra 10 seconds :P so i was wondering if theres anyway to eliminate the splash screen. 

Using Ubuntu 8.04

Any tips are appreciated!!!

---

### Post by Captain666 on 2008-08-21
The splash screen comes after I see the Ubuntu loading bar page, but before the log in screen,

---

### Post by mb_webguy on 2008-08-21
Open the terminal and type "gksu gedit /etc/X11/xorg.conf".

Look for the "Device" section that mentions the nVidia driver.  In that section, insert the line:```
Option "NoLogo" "True"
```

Save and exit, and then restart X with Ctrl-Alt-Backspace.

---

### Post by forger on 2008-08-21
10 seconds? Must be the loading time

to disable the nvidia splash screen, head to: Applications > Accessories > Terminal and execute:
gksu gedit /etc/X11/xorg.conf

Now you can edit your xorg.conf file! Find the **Section "Device"** and add a line just **[COLOR="Red"]before[/COLOR]** the "EndSection":
```
Option "NoLogo" "True"
```

Click Save in the text editor and close it.
Now log out and log back in, this should disable the logo :)

---

### Post by mb_webguy on 2008-08-21
Ha ha!  I posted first for once!!!

---

### Post by Captain666 on 2008-08-21
Easy enough and it worked perfectly!! Thanks dude

---

### Post by Captain666 on 2008-08-21
whats with the ¨true¨? does it do much, cause i didnt add it in..?

---

### Post by kpkeerthi on 2008-08-21
```

Option "NoLogo" "True"

```
is same as saying
```

Option "NoLogo"

```
"True" is assumed by default.

---

### Post by mb_webguy on 2008-08-21
The default value for the NoLogo option is "True", but it's always better to be explicit than to rely on the implicit value, because it may not be what you think it is...

EDIT:  Frak!  kpkeerthi beat me to it...

---

### Post by Captain666 on 2008-08-21
Oh ok, Thanks a lot guys!!!

---

### Post by posterpaint on 2008-08-21
My x org conf has "no logo true". I like the logo, how do I get the nvidia logo to open?

---

### Post by MindFlayer on 2008-08-21
> **posterpaint said:**
> My x org conf has "no logo true". I like the logo, how do I get the nvidia logo to open?

Try Option "NoLogo" "False"

---

### Post by TheBig3 on 2009-02-05
I like the Nvidia screen too, but the trouble I'm having is that it won't allow me to save the file. When I try to change the permissions it state that I'm not the owner. There are no other users on this system. BTW, I'm using ubuntu 8.10. Any help would be greatly appreciated, thank you.

---

### Post by mb_webguy on 2009-02-07
You need to open the file as root using "gksu gedit /etc/X11/xorg.conf".  If you leave off the gksu part, you'll be opening it as your own user account, and you don't have write permissions for that file.

---

