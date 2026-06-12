---
title: "Dual HDD, Dual Boot, XP &amp; Ubuntu"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by Elecmn on 2009-08-29
Newbie here. I have already install Ubuntu via Wubi on my XP systems second HD, but would like to install Ubuntu on the second HD as a dual boot OS on the entire second disk. My question is do I need to uninstall Ubuntu (Wubi) before attempting a reinstall from a live disk?  Also do I need to do any pre-formatting the second disk?

---

### Post by raymondh on 2009-08-29
> **Elecmn said:**
> Newbie here. I have already install Ubuntu via Wubi on my XP systems second HD, but would like to install Ubuntu on the second HD as a dual boot OS on the entire second disk. My question is do I need to uninstall Ubuntu (Wubi) before attempting a reinstall from a live disk?  Also do I need to do any pre-formatting the second disk?

I would (if wubi-ubuntu is on the same HD you plan to put the new ubuuntu):

-  Uninstall the wubi-ubuntu
-  Delete  **JUST** the wubi-related line in the boot.ini file
-  Check if XP boots fine
-  Decide whether to have a separate /home or not
-  If not .... proceed with the install, choosing the appropriate HD during the install.
-  If so, create the partitions beforehand and install manually.

Back-up your files.  

Wubi has the option to transfer current installation to a real partition (using LVM, I think) but I have not experimented on that.  Sorry.  Best to check the [wubiguide]("https://wiki.ubuntu.com/WubiGuide") if you decide to do LVM.

Good luck.

---

### Post by presence1960 on 2009-08-29
to edit boot.ini from windows to remove wubi reference see post # 3 [here]("http://ubuntuforums.org/showthread.php?t=1234516&highlight=wubi+boot.ini")

---

### Post by darthnerd on 2009-08-29
you can refer to [this]("http://ubuntuforums.org/showthread.php?t=179902") for your future setup..

---

### Post by raymondh on 2009-08-29
> **presence1960 said:**
> to edit boot.ini from windows to remove wubi reference see post # 3 [here]("http://ubuntuforums.org/showthread.php?t=1234516&highlight=wubi+boot.ini")

thanks Presence :)

---

### Post by Elecmn on 2009-08-30
Thanks to all who responded to this post.  I will post again to let you know how it turns out.  BUDDING COMPUTER GURU

---

### Post by Elecmn on 2009-09-02
[SIZE=2]Everything turned out good. My other half won't go to Ubuntu for fear of not being able to do all the things she likes about Windows XP. For a short while I thought I would need more help, but I have learned if at first you don't suceed then ....... I couldn't get the boot menu to come up but after reading the second post by "Confused57", I went into bios and changed the boot order. That solved everything. I'm up and running. Thanks "Darthnerd", "Raymondhenson", and "Presence1960". Linux people are the best.
[/SIZE]

---

### Post by presence1960 on 2009-09-02
> **Elecmn said:**
> [SIZE=2]Everything turned out good. My other half won't go to Ubuntu for fear of not being able to do all the things she likes about Windows XP. For a short while I thought I would need more help, but I have learned if at first you don't suceed then ....... I couldn't get the boot menu to come up but after reading the second post by "Confused57", I went into bios and changed the boot order. That solved everything. I'm up and running. Thanks "Darthnerd", "Raymondhenson", and "Presence1960". Linux people are the best.
[/SIZE]

Glad everything worked out. Enjoy Ubuntu!

---

### Post by raymondh on 2009-09-02
as well, congratulations and happy ubuntu-ing.

---

### Post by Elecmn on 2009-09-08
Since this last post a new problem has occured.  Now when switching back to Windows the clock has the incorrect time.  I can double click and re-sync to time.nist.gov time and it sync's fine.  But I would like it to sync on re-start.  Is there any batch file or other ways to accomplish this?

---

### Post by presence1960 on 2009-09-08
> **Elecmn said:**
> Since this last post a new problem has occured.  Now when switching back to Windows the clock has the incorrect time.  I can double click and re-sync to time.nist.gov time and it sync's fine.  But I would like it to sync on re-start.  Is there any batch file or other ways to accomplish this?
That I do not know, sorry.

---

### Post by raymondh on 2009-09-08
Hope this can help

[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

I *think* windows sets time in sync with your BIOS  whilst Ubuntu sets per UTC/GMT.

---

