---
title: "[SOLVED] Customizing the Terminal"
date: 2008-11-22
forum: General Help
---

### Post by COLiNx86 on 2008-11-22
I saw this picture when I was lookin around and I was wondering if I could really do this.
[IMG]http://www.taimila.com/files/osx-logo.png[/IMG]
If you look you can see a terminal, but only the first part is blue. How could I do that?
thanks in advanced.

---

### Post by eternalnewbee on 2008-11-22
> If you look you can see a terminal, but only the first part is blue. How could I do that?
It's not blue. It looks that way because the terminal is a little transparant.
You can adjust the transparancy by opening the terminal, and clicking **Edit**, and **Profile Preferences** and then the **Background** tab.

---

### Post by Locutus_of_Borg on 2008-11-23
You mean the text?

color10 is the number corresponding to the user@hostname section

so for an xterm, put in .Xdefaults:
XTerm*color10: #00ff00

change to whatever color you want, or whatever terminal you want

---

### Post by eternalnewbee on 2008-11-23
I see it now. Good eye you've got there;)

---

### Post by COLiNx86 on 2008-11-23
> **Locutus_of_Borg said:**
> You mean the text?

color10 is the number corresponding to the user@hostname section

so for an xterm, put in .Xdefaults:
XTerm*color10: #00ff00

change to whatever color you want, or whatever terminal you want

Yes, thank you that's what I wanted.
@eternalnewbee Sorry should of been a little clearer.

---

### Post by eternalnewbee on 2008-11-23
> @eternalnewbee Sorry should of been a little clearer.
No problem. Lucky we've got Borg technology here:-D
Btw, if your issue is solved, you should mark this thread as solved, at the top of this page, under [COLOR="Red"]Thread Tools[/COLOR].

---

### Post by COLiNx86 on 2008-11-23
> **eternalnewbee said:**
> No problem. Lucky we've got Borg technology here:-D
Btw, if your issue is solved, you should mark this thread as solved, at the top of this page, under [COLOR=Red]Thread Tools[/COLOR].
haha yeah. Dang I always forget about that.

---

