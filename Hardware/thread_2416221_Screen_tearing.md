---
title: "Screen tearing"
date: 2019-04-07
forum: Hardware
---

### Post by fenix1jm on 2019-04-07
Hello, I'm experiencing some screen tearing by just moving some programs in window mode, I watched one of those screen tearing 60 fps test videos, and I can confirm that I have this issue. I've been looking around for a solution and I saw that enabling "Force Full Composition Pipeline" In Nvidia X Server Settings is the solution, but the problem is I don't have that option. My Nvidia Driver is  390, I should be able to see the option.

---

### Post by Autodave on 2019-04-07
Where did you get the driver from?

Please give some specs on your equipment again.

---

### Post by fenix1jm on 2019-04-07
> **Autodave said:**
> Where did you get the driver from?

Please give some specs on your equipment again.
GPU: Nvidia GTX 1060 I also have a integrated Intel gpu. I updated the drivers through "Software and Updates" and later I tried through the terminal to see if something changes. My driver version is 390. Another problem I have is when my laptop goes in to sleep mode, and when I turn back on, the screen starts acting weirdly, it shows a code or something and then it goes back to normal, all this happens very quickly.

---

### Post by poorpockets-mcnewhold on 2019-04-08
With a 1060 aswell, I’m on nvidia-driver-418. Despite I do have screen tearing issues aswell, even with V-sync enabled on games for this specific case, i would still recommend you to try to update them with the latest drivers.
```
sudo apt-get install nvidia-driver-418
```
[IMG]https://imgur.com/VQIeoyv.png[/IMG]
Another thing you could try, is to tweak the NVIDIA X server settings (In short, those are just the graphics drivers settings. You simply need to configure in the OpenGL settings, to **Sync to VBlank **like on the following picture.
[IMG]https://imgur.com/CwkiCod.png[/IMG]

---

### Post by fenix1jm on 2019-04-08
> **poorpockets-mcnewhold said:**
> With a 1060 aswell, I&#8217;m on nvidia-driver-418. Despite I do have screen tearing issues aswell, even with V-sync enabled on games for this specific case, i would still recommend you to try to update them with the latest drivers.
```
sudo apt-get install nvidia-driver-418
```
[IMG]https://imgur.com/VQIeoyv.png[/IMG]
Another thing you could try, is to tweak the NVIDIA X server settings (In short, those are just the graphics drivers settings. You simply need to configure in the OpenGL settings, to **Sync to VBlank **like on the following picture.
[IMG]https://imgur.com/CwkiCod.png[/IMG]
Is that the latest version? Is it safe if I update to that version?

Edit: When I try to update my driver it says "Unable to locate package nvidia-driver-418

---

### Post by fenix1jm on 2019-04-08
Now I get the message saying "Could not get lock /var/lib/dpkg/lock-frontend-open (11:resource temporarily unavailable)"
"Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?"

---

### Post by fenix1jm on 2019-04-09
I've managed to install the Nvidia  metapackage 418 driver through "Updates and Software" but I couldn't do it through the terminal for whatever reason. I'm going to let you know, if updating my driver fixes the screen tearing.

---

### Post by Autodave on 2019-04-09
There have been problems reported with the 418 driver.  I would recommend to both of you to use either the 410 or 415 package.

---

