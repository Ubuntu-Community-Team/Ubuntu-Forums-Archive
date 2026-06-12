---
title: "New Motherboard"
date: 2012-04-02
forum: Hardware
---

### Post by burpootus on 2012-04-02
I have a good Linux install, configured just the way I like. I'm having trouble with my motherboard and will be replacing it soon. The new MOBO is a different brand than the old one, but will re-use the same CPU, memory, etc.. This PC dual boots Win 7 and Linux, although I use Linux almost exclusively now. I do not want to go through the hassle of re-installing either of the OS's after the hardware change. I'm pretty clear on the Win side with the sysprep tool so it will basically boot like it's the first time and install the new MOBO drivers. My concern is the Linux side, is there anything special to have it boot up and automatically configure to the new hardware without re-installing?

---

### Post by QIII on 2012-04-02
First:  DO BACKUPS!

Include your sources list.  Also do

```
dpkg --get-selections > selections.txt
```

That will save a list of your software installed via apt.  You'll have to take note of your third party apps.

(Do that before you back up /home so you will have it for later.)

Disable all third party drivers.

Then you can change your hardware.

This sort of switch generally works, but I have had it fail completely.  Prepare for the worst, but it is more than likely that things will generally go well.

---

### Post by Mark Phelps on 2012-04-02
I would do research on a Windows 7 forum (sevenforums.com) before presuming what sysprep will do in Win7.  Consider the following post I found there:

> I ran Sysprep on Windows 7, and it cleaned out all the files and shortcuts that were on it. It reset the wallpapers and taskbar and everything. I had like close to 200GB worth of movies, audio, and stuff. Sysprep cleaned it out. So basically, it eradicates everything, and converts Windows 7 to its original state leaving installed software alone.

When you switch to a new one, it MIGHT reactivate OK, especially if it a retail version.  But, be prepared to contact MS if it does not reactivate.

---

### Post by burpootus on 2012-04-02
> **Mark Phelps said:**
> I would do research on a Windows 7 forum (sevenforums.com) before presuming what sysprep will do in Win7.  Consider the following post I found there:



When you switch to a new one, it MIGHT reactivate OK, especially if it a retail version.  But, be prepared to contact MS if it does not reactivate.

Luckily I don't use My Documents, My Videos, My Pictures, etc. folders to store stuff in Windows, so worse case it blows away my user I can just add it back. My understanding of sysprep is that it does nothing to users, only uninstalls drivers and sets up the OS to re-install drivers as a new system. This used to be a registry thing in XP, but it's been so long I can't remember how I did it. It appears that my understanding of sysprep and the poster's experience are very different, I hope my mileage varies.

---

### Post by QIII on 2012-04-02
Base nothing on hope.

Back it all up.  "Luck is the residue of good planning."

Backups.  Don't leave home without them.

---

### Post by Mark Phelps on 2012-04-04
> **QIII said:**
> Base nothing on hope.

Well said ...

The person didn't say that their 200GB of stuff was stored in their "personal" folders, although that's likely the case.  Most folks probably just download and import stuff, and really don't know (or care) where it ends up in MS Windows, as long as they can get to it when they need to.

Also, Documents and Settings haven't really been used to store anything since the XP days. MS did away with that folder in Vista (and now in Win7 as well) and uses an entirely different scheme now. 

So, if this is your understanding of sysprep as well, you're taking a real chance on presuming how it will work under Win7.

---

