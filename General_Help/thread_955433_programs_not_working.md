---
title: "programs not working?"
date: 2008-10-22
forum: General Help
---

### Post by mickeyd1965 on 2008-10-22
Hi,
I have noticed that after a week or so my computer has slowed down and certain programs don't work anymore( hardware drivers,hardware testing,synaptic package manager).

can anyone help please.

mickeyd1965

---

### Post by mkvnmtr on 2008-10-22
Someone can probably help you but you have to give more information. Tell us what operating system you are using. Then the machine and the specs for the machine. Then explain the problems one at a time. Just saying it runs slow doesn't give any idea what the problem might be.

---

### Post by mickeyd1965 on 2008-10-23
i'm running ubuntu 8.04 on a dell gx270 with 2.26Ghz cpu and an nvidia geforce ge6200 video card. after a week or so it takes longer for anything to open . I mean 30sec instead of 5 sec. Hardware drivers,hardware testing and synaptic package manager do not open at all any more. You click on it then you get the icon telling you to wait which disappears after about 30 sec, then nothing happens.

---

### Post by mickeyd1965 on 2008-10-23
now my updates won't work either.
I'll have to re-install AGAIN.

---

### Post by melojo on 2008-10-23
open up a terminal and type sudo synaptic and post the error messages from the terminal window.

---

### Post by mickeyd1965 on 2008-10-23
there were no errors. synaptic package manager worked, but it won't work when i try to access it from the 'system" tab

---

### Post by melojo on 2008-10-23
goto system>main menu>scroll down to Administration and click then on the right side click synaptic package manager and then properties and tell us what it says in the command line

---

### Post by dave.com on 2008-10-23
Sry to interrupt ya but this situation appears urgent, I have lost my Desktop display. There's no gui access the display screen is not found and I am afraid to logout in case I dun even get back in. Closed Terminals do NOT open again. Maybe its loosely related? 

With sudo synaptic my comp returns: ```
 $sudo synaptic
$Invalid MIT-MAGIC-COOKIE-1 key
$(synaptic:8173): Gtk-WARNING **: cannot open display: :0.0

```

---

### Post by patrickballeux on 2008-10-23
> **dave.com said:**
> Sry to interrupt ya but this situation appears urgent, I have lost my Desktop display. There's no gui access the display screen is not found and I am afraid to logout in case I dun even get back in. Closed Terminals do NOT open again. Maybe its loosely related? 

With sudo synaptic my comp returns: ```
 $sudo synaptic
$Invalid MIT-MAGIC-COOKIE-1 key
$(synaptic:8173): Gtk-WARNING **: cannot open display: :0.0

```

Synaptic cannot work without the Xorg server (Graphic server)...  Instead run this:

```
sudo apt-get update
sudo apt-get upgrade
```

This will ensure that you have the latest updates installed.

---

### Post by mickeyd1965 on 2008-10-23
it says  gksu /usr/sbin/synaptic

---

### Post by patrickballeux on 2008-10-23
> **mickeyd1965 said:**
> it says  gksu /usr/sbin/synaptic

In a terminal, can you run "dmesg" and paste the results here.  I hope that your harddisk is not crashing because this is the kind of problem when a hd is near it's death...

---

