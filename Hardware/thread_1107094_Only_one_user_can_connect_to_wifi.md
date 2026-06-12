---
title: "Only one user can connect to wifi"
date: 2009-03-26
forum: Hardware
---

### Post by Mlok on 2009-03-26
Hi all,

a strange problem showed up on my machine.
The first user created on this machine (let's call her A) can log in and connect to the wifi (automatically). If another user (his name is B) starts his own session without closing A's, he can access the wifi too. Great.

Unfortunately, if A is not logged when B logs in, a password is asked to access the keyring (my own translation from "Trousseau de cles") to get the WPA password probably, but no user "login password" works, neither A's password (A is the first user created for this install, therefore she has administrator rights by default), nor B's (who happen to be have admin status too).

Why is that?


The workaround is obvious as explained in the first paragraph, but I feel uncomfortable with this weird behaviour, something is wrong in my setup and I'd better sort it out before a biggest problem builds on...


Thanks!

FYI : this has also been posted on the French Ubuntu forums
[http://forum.ubuntu-fr.org/viewtopic.php?id=303929](http://forum.ubuntu-fr.org/viewtopic.php?id=303929)

---

### Post by Mlok on 2009-04-04
[deleted post - mistakes were too confusing]

---

### Post by Mlok on 2009-04-04
Actually, the problem is about the keyring.

Each time I try to create a new wifi connection, I give a wifi-password but in the end nm-manager fails to save it, because it cannot unlock the "keyring". (whatever admin-user password I give it, be it A's user-password, or B's user-password)

When trying to add a wifi-password to my keyring directly (through Applications/Accessories/"Passwords & cryptographic keys" - approximative translation) /usr/bin/seahorse is pushed back : cannot unlock the keyring again.

This is strange, how come in my own session I cannot access my own keyring?

Any help would be much appreciated.

---

### Post by Mlok on 2009-04-04
Given that the problem is located around the keyring, I would like to change the title of this thread into "Cannot unlock keyring", but I can't find the "edit thread title" button...

---

### Post by Mlok on 2009-04-04
I went to Applications/Accessories/"Passwords & cryptographic keys" (approximative translation) menu "Edit/Preferences" and clicked on "Add a new keyring" calling it "KeyRingB". (I give it the same password as my login)
There was already the default keyring named "login" which is (supposed to be) unlocked on login.
I choose my newly created keyring KeyRingB as the default one.

On the next login nm-applet tries to connect to the wifi network, ask me for a wifi password which I provide, and next ask me for the keyring password. I give it (as set just before) and it is accepted.
Now the wifi password is stored in my KeyRingB keyring.

And it works fine!

Unfortunately, this new keyring is not automatically unlocked on login, so I need to reenter its password on each login.

Not perfect, but not too bad.

---

### Post by Mlok on 2009-04-04
I deleted the ~/.gnome2/keyrings directory and went back to create a new keyring as explained before. Selected it to be my default keyring for applications.

Next time I logged in I was asked the wifi password, then my default keyring password which I gave + I checked the checkbox asking me if I wanted this keyring to be unlocked each time I login.

Should be fine now.
This is SOLVED.
(but I have no clue how to express it in the title)

Hope this monologue will be useful to somebody.
It's 4am here - my insomnia has been productive.

---

### Post by Mlok on 2009-04-05
On the French forum someone showed that you could also edit your network connexion and check "System Parameter" .
To do this, log in as the admin user which has a proper wifi connexion working. Right click on the nm-applet, then click "Connexions modifications" (my approximative translation) the go to the "wireless" tab, select the right connexion and click "Modify". There you can check "System Parameter". From now on this connexion is used system-wide if I understand well, and is therefore used for every user.
Normally, "Automatic connexion on login" should be checked as well.

This is actually the best approach (I have removed my fix in the meantime) and the one which must be installed by default for everybody, but for some reason it wasn't set up properly on this machine. (or possibly I did mess with it myself somehow?)

Sorry for the approximative translation of button names etc.

---

