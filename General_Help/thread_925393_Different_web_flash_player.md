---
title: "Different web flash player"
date: 2008-09-20
forum: General Help
---

### Post by Udi on 2008-09-20
Hi.
I don't really know if this is a OS issue, but in Windows I didn't had this "problem".

My Firefox is pretty problematic with Flash, lot of flash files don't run,
I have Shockwave flash  9.0 r100 plugin, and it look like this:
[IMG]http://img37.picoodle.com/data/img37/3/9/20/f_flashPlayerm_bc675c9.jpg[/IMG]

is there any other flash player I can install for Firefox? or for Ubuntu that will affect my Firefox? I didn't find any way to delete the current plugin for installing different one.

Thank you.

---

### Post by Monotoko on 2008-09-20
Its not an issue with the OS, its an issue with firefox, try reinstalling flash:

Open Applications->Accessories->Terminal and paste:
sudo apt-get install --reinstall flashplugin-nonfree

If that doesnt work, downgrade to firefox 2, as firefox 3 seems to be having this problem a lot.

---

### Post by Udi on 2008-09-20
Amazing! that works!

Thank you!!:guitar:

---

### Post by Monotoko on 2008-09-20
No problemo, just glad to help

---

### Post by ahuman on 2008-09-20
Weird - I just had the same problem. I'd automatically upgraded to 8.04. Is that what set this problem off?

---

### Post by Monotoko on 2008-09-20
Kind of, when you upgraded, if you downloaded all the updates, it will have given you firefox 3, the most recent version is buggy with flash.

The new version is coming out tomorow, and there is a fix for this bug.

---

### Post by ahuman on 2008-09-20
Thanks! How can I downgrade to Firefox 2.0 for the day? I'm a newbie. I just downloaded the old version, but don't know how to complete the installation now that the files have downloaded to my desktop.

I also tried to find Firefox 3.0 to delete it, but don't know where to find it. I tried to delete it from the Add/Remove option, but was told I couldn't because other files were relying on it.

---

### Post by mb_webguy on 2008-09-20
You may also want to try installing the Flash 10 plugin from the backports repository.  It's considerably better than the one in the general repositories.

---

### Post by Monotoko on 2008-09-20
You would have to manually do it, its best just to reinstall flash, as the new version should be coming out tomorow

---

### Post by mb_webguy on 2008-09-20
Monotoko, just for clarification, are you saying that a new version of Flash is coming out tomorrow, or a new version of Firefox?

---

### Post by ahuman on 2008-09-20
Ever since this 8.04 upgrade, I'm being told I don't have Flash installed. I installed the plugin recommended above. Do I need to reinstall Flash and watch videos on a different browser? I tried on a different browser and am still being told I don't have flash installed.

Argh, frustrating!:-x

---

### Post by mb_webguy on 2008-09-20
That's why I always do a clean install with a new version of Ubuntu instead of an upgrade.  Upgrades aren't always as painless as they should be.

Try backing up your bookmarks and passwords in Firefox -- the Password Exporter extension is handy for the latter -- and then completely uninstalling Firefox and the Flash plugin.  Then go through and delete any folders and files that weren't removed, like the .mozilla folder in your home directory.  You can use "sudo find / -name *lashplaye*" to look for any lingering references to the Flash plugin.  Delete anything that looks like it doesn't belong to another application.  Also, make sure you don't have any other Flash-plugin-related packages, like other Flash plugins (such as Gnash) or the libflashsupport package.

Then reinstall Firefox and the Flash 10 plugin.  You should now see the Flash 10 plugin listed in about:plugins page in Firefox.  If so, import your bookmarks and passwords, reinstall your extensions and themes, and go watch some Hulu.

---

### Post by ahuman on 2008-09-20
Thanks so much. I found out my problem is that I have a 64-bit architecture and Flash only supports 32-bit (I'm sure you already know that -- just added the tip in case somebody else reads this thread and needs the help). I was able to fix things by following the steps found here: [http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Only problem is now I don't have any audio, and I'm getting the same image as the first person in the post got when trying to watch a video (a "play" symbol in a circle). I think it's from a plug-in for Firefox I downloaded earlier. I'm trying to find it to get rid of it. Any suggestions?

---

### Post by Monotoko on 2008-09-20
> **mb_webguy said:**
> Monotoko, just for clarification, are you saying that a new version of Flash is coming out tomorrow, or a new version of Firefox?

New version of firefox, small update, it might not be on synaptics tomorow though, but with the need for it, i assume it should be.

---

### Post by ahuman on 2008-09-21
My Flash is working again. I re-installed it using the link found here for Gusty-Hardy users (aka people who use Ubuntu 7.10 and Ubuntu 8.04 versions): [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924).

I also downgraded to Firefox 2 first by going to System/Synaptic Package Manager and searching Firefox-3. I deleted anything from the results with a green square next to it (aka anything installed) and deleted it. Then, I went to Add/Remove programs, searched for Firefox-2 and installed it.

:guitar:

---

