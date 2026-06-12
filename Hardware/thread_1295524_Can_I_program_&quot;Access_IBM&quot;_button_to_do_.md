---
title: "Can I program &quot;Access IBM&quot; button to do something?"
date: 2009-10-19
forum: Hardware
---

### Post by kn_mpls on 2009-10-19
Greetings.
I have Ubuntu 9 running beautifully on an IBM T40 laptop. I'm wondering if there's any way to tell Ubuntu to do something when I press the "Access IBM" button. It would be really slick if I could make that launch Firefox or some other commonly used app. Any advice appreciated. Thanks in advance.
Cheers.

---

### Post by Giblet5 on 2009-10-19
Bring up a terminal window and enter ```
xev
```

Put the mouse cursor in the little window and hit that key a few times. Does it generate KeyPress and KeyRelease events? If so, then yeah. You can use it for anything you do with any other key.

---

### Post by kn_mpls on 2009-10-19
Indeed it does generate KeyPress and KeyRelease events. How do I go about assigning those events?

---

### Post by kn_mpls on 2009-10-20
Here's the solution that worked perfectly for my purposes:

[LIST=1]
[*]Go to **System > Preferences > Keyboard Shortcuts**
[*]In Keyboard Shortcuts there are lots of predefined actions and their shortcuts (or lack thereof). I simply clicked the shortcut for the **Launch web browser** action then pressed the "Access IBM" button to assign the shortcut.
[*]Custom actions can also be created through this control panel.
[/LIST]
I suppose you could get more advanced by creating a script then telling the button to launch the script.

---

### Post by Dark_Stang on 2009-10-20
> **kn_mpls said:**
> I suppose you could get more advanced by creating a script then telling the button to launch the script.

Yup. With a little bash you can do just about anything.

---

