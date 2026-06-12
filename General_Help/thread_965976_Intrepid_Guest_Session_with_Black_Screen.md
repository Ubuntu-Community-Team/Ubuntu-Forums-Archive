---
title: "Intrepid Guest Session with Black Screen"
date: 2008-11-01
forum: General Help
---

### Post by Qchan on 2008-11-01
[b][color=darkred]
I fixed the issue by going to System --> Administration --> Login Window

Under Default Session, it was set as "Run Xclient Script". It was supposed to be set to Gnome. So, I set it to Gnome and it works!

-----------------------------------------------------------------------

I just upgraded to Intrepid Ibex. However, when I try to switch over to the Guest Session, I just get a black screen with just a mouse cursor.

I did have a previous guest account I made in Hardy. I deleted it after I found I couldn't switch to it. After I deleted the account, I rebooted and tried to switch to the guest session.
Heck, I even installed the guest-session-launch thing. That didn't work.

Help!
[/b][/color]

---

### Post by Marat89 on 2008-11-02
same problem here. Using a radeon HD 2400 PRO.
I think it is a graphical driver problem of "fglrx"

---

### Post by Qchan on 2008-11-02
> **Marat89 said:**
> same problem here. Using a radeon HD 2400 PRO.
I think it is a graphical driver problem of "fglrx"

[b][color=darkred]
I have an nVidia card.
[/b][/color]

---

### Post by Marat89 on 2008-11-02
do you now if this bug is reported in Launchpad?

---

### Post by Roasted on 2008-11-02
I'm having similar problems. I have Intrepid Ibex 64 bit and a Nvidia 9600GT with 177 drivers installed.

When I go to guest session, it works fine. The trick is, when I try go to back to my session, I get a white screen. I still hear sounds though, as if I'm getting instant messages and whatnot. But I can't get rid of the white screen. I'm forced to CTRL ALT Backspace my way back to the original login screen and log in all over again.

---

### Post by Marat89 on 2008-11-02
I think Its a bug, we have to wait till its fixed.

---

### Post by Qchan on 2008-11-02
[b][color=darkred]
I saw this:
[https://bugs.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/266911](https://bugs.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/266911)

I went ahead and replied to it. That guy fixed his issue by deleting a previous Guest account on Hardy. I did the same thing, but I still get the problem. I even ran the script the other guy replied with.
[/b][/color]

---

### Post by Marat89 on 2008-11-03
Hey, but i installed Intrepid new, not a Update.?!

---

### Post by Roasted on 2008-11-03
I installed Intrepid from CD too, and did not do a distro upgrade from Hardy, and I have this problem.

We'll just wait for the team to come up with a patch. They always do.

---

