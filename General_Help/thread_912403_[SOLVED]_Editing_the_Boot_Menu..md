---
title: "[SOLVED] Editing the Boot Menu."
date: 2008-09-06
forum: General Help
---

### Post by Virtua-Touch on 2008-09-06
I've just finished downloading the ISO through Wubi, and I chose Manually Reboot Later. How do I remove the Ubuntu option from the boot menu? The reason I ask this is because my dad is swapping computers for a new one he got and we're getting this one, but I do not want him to know I have Ubuntu on the computer yet. I am using Windows XP Home Edition.

---

### Post by caljohnsmith on 2008-09-06
So are you saying that you have Ubuntu installed with Wubi, and you want to get rid of the option to boot Ubuntu on start up? If that is true, just modify your C:\boot.ini file. At the end of that file you'll see something like:
```
c:\wubildr.mbr="Ubuntu"
```
All you need to do is delete that line. Let me know how it goes or if you need more info/details.

---

### Post by Virtua-Touch on 2008-09-06
Okay. I typed in C:\boot.ini in the address bar and it opened up. I saw the option and deleted it. When saving, it says **"Cannot create the C:\boot.ini file. Make sure that the path and filename are correct."**

[EDIT] I think I should mention, I've ticked Show Hidden Folders and I'm in the C:\ location, but there is no boot.ini file. Although, it opens when I type C:\boot.ini in the address bar.

---

### Post by caljohnsmith on 2008-09-06
> **Virtua-Touch said:**
> Okay. I typed in C:\boot.ini in the address bar and it opened up. I saw the option and deleted it. When saving, it says **"Cannot create the C:\boot.ini file. Make sure that the path and filename are correct."**

[EDIT] I think I should mention, I've ticked Show Hidden Folders and I'm in the C:\ location, but there is no boot.ini file. Although, it opens when I type C:\boot.ini in the address bar.
Follow the directions on this page to modify your boot.ini file:
[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)
Let me know how it goes.

---

### Post by Virtua-Touch on 2008-09-06
I have just noticed that the boot.ini file is in a folder completely hidden, even with the option ticked, called Recent. (Full Path: C:\Documents and Settings\Jared\Recent)

[EDIT] Thank you. It saved. I'll update you if it worked after I restart.

---

### Post by Virtua-Touch on 2008-09-06
Thank you. Everything worked. No more boot option for Ubuntu, just starts up as normal. I don't have time to do the installer right now, it's 8 and I have to get off at 9:30. My dad's awake which means he could spot it. Is there any way to switch to Windows quickly while installing Ubuntu?

---

### Post by DrMelon on 2008-09-11
What's the problem if your Dad sees it anyway? It's just another OS. If, however, for any reason you shouldn't be doing it (i.e. he told you not to) you shouldn't be doing it behind his back.

---

### Post by Virtua-Touch on 2008-09-11
It's his computer, but it's also the family computer. He doesn't like a lot of this stuff that I want (which doesn't do anything harmful - like Ubuntu) on it. But, I'm getting this computer sooner or later.

---

