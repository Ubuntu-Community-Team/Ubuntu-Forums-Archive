---
title: "Can't log in &quot;Authentication Failed&quot; [Intrepid]"
date: 2008-11-24
forum: General Help
---

### Post by missmaryrules on 2008-11-24
After installing a new login theme and disabling Automatic Login, I can't log in. When I rebooted and got to the login screen, it displayed "..." as the username and gave me an "Authentication Failed" error; clicking the "OK" for the error message doesn't make it go away and I an unable to type my username/password.

Not only am I unable to log in, but am also unable to copy files (schoolwork!) from my documents using the live disc to navigate.

How can I again enable automatic login or at least copy those files to an external hard drive?

---

### Post by The Cog on 2008-11-24
I don't know what's wrong with your login screen, but this should give you a work-round and get your data off, and maybe help you fix your configuration. 

At the login screen, press Ctrl-Alt-F1 to get a text console.
Log in using your username and password.
Kill the existing desktop manager with **sudo /etc/init.d/gdm stop**
Start a new X session with **startx**

---

### Post by Hartbuntu on 2008-12-01
I am having this same problem. I started a new x session and got in to my desktop. when i tried to open my login screen manaer, it couldnt open because gdm wasnt running. at this point, i just want to change it back to auto login and figure out the problem later. Any suggestions?

Thanks,
Hartbuntu

---

### Post by primaxx on 2009-02-03
I can also confirm this is a problem in Intrepid, at least when it comes to the "Easy Peasy"-version.

I managed to solve it though, thanks to the solution I found [here]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/203755"). 

What the user [ehpc]("https://bugs.launchpad.net/~ehpc") came up with was basically to edit the file /etc/pam.d/gdm.

Here you must comment out the line ```
@include common-pamkeyring (Place **#** in front of the line to comment it out.)
```
and then add the line ```
auth optional pam_gnome_keyring.so
``` just before the already existing line ```
session optional pam_gnome_keyring.so auto_start
```.
Save and restart, and your problems should be gone. (At least mine was...)

---

