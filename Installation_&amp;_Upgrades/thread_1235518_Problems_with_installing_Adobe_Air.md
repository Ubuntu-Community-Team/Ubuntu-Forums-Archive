---
title: "Problems with installing Adobe Air"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by ChiVampir on 2009-08-09
After I have done something wrong Adobe Air was gone. 

And I though that I would just have to reinstall it.

I downloaded the .bin file from Adobe's pages and opened the terminal:
```
cd /home/chi/
chmod +x ./AdobeAIRInstaller.bin
sudo ./AdobeAIRInstaller.bin
```(I have also tried without sudo)

Untill here everything goes fine, and i Acept the terms and Air is starting to install. But then I get this message:

> **Sorry, an error has occurred**

An error occurred while installing Adobe AIR. Installation may not be allowed by your administrator. Please contact your administrator.The problem here is that I'm the administrator.

I have googled and found different solutions: Rename the old Adobe Air folder in  /op and closed all the internet programs. But nothing worked... I have also tried to install after restarting the computer. And I have dowloaded the .bin file lots of times.

I run Ubuntu 9.04 32-bit.

---

### Post by wojox on 2009-08-09
```
gksudo nautilus
```

Rename the folder adobeair try again.

---

### Post by ChiVampir on 2009-08-09
> **wojox said:**
> ```
gksudo nautilus
```Rename the folder adobeair try again.

Like I said the folder is already renamed

**Edit: **And now it seems like the folder has disappeared :S

---

### Post by kostkon on 2009-08-09
You don't need to put sudo. Thus, just call it like this:
```
./AdobeAIRInstaller.bin
```

---

### Post by ChiVampir on 2009-08-09
> **kostkon said:**
> You don't need to put sudo. Thus, just call it like this:
```
./AdobeAIRInstaller.bin
```

Like I wrote in my first post I have tried with and without sudo, but I still get the same result :(

---

### Post by ChiVampir on 2009-08-10
Then I have tried and tried again and now I'm giving up I think.

Do you think that the problem could be fixed with a fresh ubuntu installation?

---

### Post by Partyboi2 on 2009-08-10
Hi, make sure firefox is not open as well as Synaptic Package Manager before running the installer.

---

### Post by ChiVampir on 2009-08-10
> **Partyboi2 said:**
> Hi, make sure firefox is not open as well as Synaptic Package Manager before running the installer.

Like I said in my first post I have tried this as well, but with no different result.

It's weird because the first time I installed Adobe Air it went without any problems.

---

