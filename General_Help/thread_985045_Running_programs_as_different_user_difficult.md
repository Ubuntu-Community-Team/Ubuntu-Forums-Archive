---
title: "Running programs as different user difficult"
date: 2008-11-17
forum: General Help
---

### Post by Thorjelly on 2008-11-17
I like keeping different uses of my laptop, such as business and personal, separated into separate user accounts. It's both an organization and a security issue. I much more often launch applications of my business account while in my personal desktop, or visa versa, as a matter of convenience. In KDE3 this was very simple to do. Simply press ALT F2 and you can choose to run a program as a separate user.

In KDE4 this is so much more difficult than it needs to be! The functionality I need of KRunner is missing completely. su doesn't work, giving display errors or "can not find D-Bus session server" in the case of Dolphin.

I don't like the idea of cluttering my desktop with multiple icons for the same program, but when I try to make a new desktop icon and set 'run as different user' it doesn't work anyway. Dolphin completely fails to open, probably for the same reason it fails to open under su, and while Firefox opens fine with my other user's profile I can not save files to that user's home folder (<file path> could not be saved, because you cannot change the contents of that folder).

Please help me! This was a very important feature for me in KDE3. Running applications as different users is very important to my work flow. Please help me try to find some reasonable, working way to do this in KDE4.

---

### Post by Thorjelly on 2008-12-02
Wow, nobody? For two/three weeks? *bump* Please help!

---

### Post by -Zeus- on 2008-12-02
try using gksu, I think it has an argument for another user other than root.

---

### Post by oldos2er on 2008-12-02
> **-Zeus- said:**
> try using gksu, I think it has an argument for another user other than root.

 "gksu" is for Gnome; KDE would use "kdesu".

 Also, "su" isn't going to work in Ubuntu (including Kubuntu) because the root account is disabled by default. Use "sudo" or "kdesu" instead.

---

### Post by -Zeus- on 2008-12-02
su works fine in ubuntu... and you're right, he needs kdesu

---

### Post by Thorjelly on 2008-12-02
Alright, thank works great, thanks! I actually would have tried that much sooner if kdesu weren't inexplicably missing and I had to go search for it and put it in /usr/bin/ :/

---

### Post by dagnabit dang doohickey on 2008-12-02
Use the -u option with kdesu (or gksu).

```
kdesu -u *otheruser command*
```

---

### Post by oldos2er on 2008-12-02
"su works fine in ubuntu"

 Only if you've enabled a root account, which is discouraged on these forums. Otherwise you see "su: Authentication failure". You can use "sudo su" though.

---

### Post by Thorjelly on 2008-12-03
Okay, nevermind. Using kdesu I am getting the same result I get when I try to make icons to open Dolphin as another user.

"Could not start process Cannot talk to klauncher: The name org.kde.klauncher was not provided by any .service files"

:/ How do I fix this?

---

### Post by Thorjelly on 2008-12-05
*bump* Does anyone know why this is happening or have a solution for this?

---

### Post by rampageoberon on 2008-12-05
I'm not sure if "su" has to be replaced with "kdesu" but this is what I do in ubuntu (gnome)

```
xhost +si:localuser:<username>
su <username>
```

The xhost command gives access control to <username> to use your Xdisplay.
Now run application as <username> from command line as usual.

Hope that helps

---

### Post by Thorjelly on 2008-12-06
Thanks! That seems to have fixed the problem :) Do I need to use that command every time I restart my xserv, though?

---

