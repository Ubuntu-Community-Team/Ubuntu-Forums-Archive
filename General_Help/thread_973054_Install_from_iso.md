---
title: "Install from iso?"
date: 2008-11-06
forum: General Help
---

### Post by wordmaster on 2008-11-06
I have  the new version of Ubuntu on my hard drive in a .iso file. Is it possible to get Wubi to load from that file rather than going through an 8 to 10 hour download of Ubuntu? Thank you kindly for any help you can give.

---

### Post by brandon88tube on 2008-11-06
Yes, just take the iso or the wubi.exe and put them in the same folder. Then temporarily turn off your internet connection and instead of wubi going online to find the iso it will see it in the same location as the installer and use that.

---

### Post by uncaspi on 2008-11-07
I copied all the files from the iso to an folder in windows. The I ran wubi.exe from windows. It didn't work to run wubi.exe from cd.:) I got an error message that says the cd writer was in use in the beginning of the installation.

---

### Post by brandon88tube on 2008-11-07
> **uncaspi said:**
> I copied all the files from the iso to an folder in windows. The I ran wubi.exe from windows. It didn't work to run wubi.exe from cd.:) I got an error message that says the cd writer was in use in the beginning of the installation.

Do you mean you copied the ISO over or the files inside the ISO? If you used the files that were contained in the ISO, then you did it wrong. You just want to ISO itself. Example: ubuntu-8.10-desktop-amd64.iso  Also you didn't state clearly if you put the ISO within the same exact folder as the wubi.exe

---

### Post by uncaspi on 2008-11-08
The files inside the iso.
I did this in windows xp.

1) Downloaded the Ubuntu iso for my platform(ubuntu-8.10.i386-desktop.iso).

2) Selected burn image in Nero

3) Copied the files to a folder in windows

4) Ran Wubi from the folder contained the files from the iso.

Probably you can extract the downloaded Ubuntu iso to a folder without burning it first. But I'm not so familiar with windows so I didn't had the time to figure out how to do that :o

---

### Post by brandon88tube on 2008-11-09
What you want to do is
1. Download the iso (download wubi.exe if you already haven't)
2. Place wubi.exe and the iso in the same folder
3. Temporarily disconnect your internet connection
4. Run the wubi.exe

DO NOT ALTER THE ISO FILE IN ANY WAY! JUST USE THE FILE THAT WAS DOWNLOADED

---

