---
title: "How to make sure Hardy stays?"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Z_God on 2009-04-26
I'm having some big problems with some of my users. I had them running Ubuntu Hardy without any issues. But for one Intrepid was offered as a important upgrade when it came out and now another one just told me he got Jaunty as an urgent upgrade.

This is really giving issues, since I can only support one or two versions (Dapper & Hardy) and these non-LTS versions have significantly more problems (which both users are experiencing as painfull and they do both regret the upgrade).

Can someone explain me what measures I need to take to make sure Hardy stays on a system and it only gets upgraded when it's manually asked to?

Thanks a lot in advance!

---

### Post by steveneddy on 2009-04-26
Make sure the "users" aren't set up as administrators.

go to system, administration, software sources

click the updates tab

at the bottom, choose release upgrade - never

---

### Post by Z_God on 2009-04-26
Thanks for your quick message! I can't seem to find this however, I guess this is through Synaptic? I only have Adept installed. Is it possible to configure this in another way too? I can't seem to find it in Adept.

Unfortunately I'm not in the position to fully administer their systems and the users have to do (& learn) most things themselves. I'm surprised however Ubuntu's upgrade system doesn't seem to make a difference between LTS and non-LTS releases.

---

### Post by ninjapirate89 on 2009-04-26
Its in the menu you click System -> Administration -> Software Sources

Type in admin password and click on the tab titled Updates. At the bottom where it says release upgrade there is a dropdown box. Click on this and select Never.

---

### Post by Buffalo Soldier on 2009-04-26
> **Z_God said:**
> Thanks for your quick message! I can't seem to find this however, I guess this is through Synaptic? I only have Adept installed. Is it possible to configure this in another way too? I can't seem to find it in Adept.

Unfortunately I'm not in the position to fully administer their systems and the users have to do (& learn) most things themselves. I'm surprised however Ubuntu's upgrade system doesn't seem to make a difference between LTS and non-LTS releases.

If you're using Ubuntu (GNOME), it should be there in the System menu.

---

### Post by Z_God on 2009-04-26
I haven't got Gnome installed (just KDE). Is there another way to achieve the same?

---

