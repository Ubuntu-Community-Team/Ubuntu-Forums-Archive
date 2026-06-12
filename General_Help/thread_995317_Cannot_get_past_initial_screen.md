---
title: "Cannot get past initial screen"
date: 2008-11-27
forum: General Help
---

### Post by fordguydude on 2008-11-27
I just got done downloading Ubuntu, put it on a CD, made it boot. When prompted, I selected the english language, pressed enter and it worked. Next screen brought me to a few options--

Start ubuntu without changing anything on your computer
test memory
Check disk for errors

There were a few others, but that's not pertinent. 

After I selected the first option to start Ubuntu without changing my computer, nothing happened. The screen didn't go any further. I waited a couple minutes and still nothing. Obviously the keyboard worked as I mentioned above. I'm SO close to being windows free, any help greatly appreciated.

---

### Post by fordguydude on 2008-11-27
bump

---

### Post by adaptr on 2008-11-27
A detailed description of the hardware might help.
Those other options **are **pertinent in your case, since it doesn't work the normal way.
There is detailed help on how to use the LiveCD boot menu both on the menu itself and on the ubuntu site.
Something that often helps is to just start the kernel, and see if that works.
Hit the key to enter advanced options, get to the screen where you can edit the boot line, and add "single" to the end of the line.
Now boot.
Report what happens, if anything.

---

### Post by fordguydude on 2008-11-27
> **adaptr said:**
> A detailed description of the hardware might help.
Those other options **are **pertinent in your case, since it doesn't work the normal way.
There is detailed help on how to use the LiveCD boot menu both on the menu itself and on the ubuntu site.
Something that often helps is to just start the kernel, and see if that works.
Hit the key to enter advanced options, get to the screen where you can edit the boot line, and add "single" to the end of the line.
Now boot.
Report what happens, if anything.

I cannot find any information on the Ubuntu site on how to use the boot menu.

I'll give your suggestion a try though.

---

### Post by fordguydude on 2008-11-27
Okay I tried that and it didn't work. Here is what I get on the boot screen--

Try Ubuntu without making any changes to your computer
Install Ubuntu
Check CD for defects
Test memory
Boot from first hard disk

F1 Help
F2 Language
F3 Key Map
F4 Modes
F5 Accessability
F6 Other options

There is no advanced options option.

I'm also currently running on Kubuntu 5.10 live disk.

---

### Post by CatKiller on 2008-11-27
> **fordguydude said:**
> I'm also currently running on Kubuntu 5.10 live disk.

5.10? Are you sure? That release was three years ago.

If it is 5.10 that you're trying, are you able to download one of the newer versions? There have been many improvements in the last three years that might have fixed the problem you're experiencing. 8.04.1 LTS is the latest Long Term Support release, and 8.10 is the latest release.

If it was a typo, ignore this comment :)

---

### Post by fordguydude on 2008-11-27
> **CatKiller said:**
> 5.10? Are you sure? That release was three years ago.

If it is 5.10 that you're trying, are you able to download one of the newer versions? There have been many improvements in the last three years that might have fixed the problem you're experiencing. 8.04.1 LTS is the latest Long Term Support release, and 8.10 is the latest release.

If it was a typo, ignore this comment :)

It is indeed 5.10. :( I bought it a couple years ago, was planning on installing it, but something changed my mind. Now, I actually need it. I feel like I'm on Windows 98. 

I think to update I would need to install first, which I'm not going to do. I've been in Gnome and I like it markedly better than KDE.

---

### Post by CatKiller on 2008-11-27
> **fordguydude said:**
> It is indeed 5.10. :( I bought it a couple years ago, was planning on installing it, but something changed my mind. Now, I actually need it. I feel like I'm on Windows 98. 

I think to update I would need to install first, which I'm not going to do. I've been in Gnome and I like it markedly better than KDE.

If you haven't installed it yet, there's no need to install an old version and upgrade to the newer. Just grab an .iso of one of the later versions from [www.ubuntu.com](www.ubuntu.com), burn it to cd and install from there. Kubuntu is KDE. Ubuntu is Gnome. If you prefer Gnome, just pick the [Ubuntu 8.04 image]("http://www.ubuntu.com/getubuntu/download").

There are other install methods available if you don't have a CD burner.

EDIT: Or are you saying that you initially tried one of the more recent one releases, experienced the problem you posted about, and are now running Kubuntu 5.10 to post to this forum?

---

### Post by fordguydude on 2008-11-27
> **CatKiller said:**
> If you haven't installed it yet, there's no need to install an old version and upgrade to the newer. Just grab an .iso of one of the later versions from [www.ubuntu.com](www.ubuntu.com), burn it to cd and install from there. Kubuntu is KDE. Ubuntu is Gnome. If you prefer Gnome, just pick the [Ubuntu 8.04 image]("http://www.ubuntu.com/getubuntu/download").

There are other install methods available if you don't have a CD burner.

EDIT: Or are you saying that you initially tried one of the more recent one releases, experienced the problem you posted about, and are now running Kubuntu 5.10 to post to this forum?

Yes, I've done all that, but now I can't get past the Ubuntu screen where it leaves you options on what to do.

But I did download 8.10.

---

### Post by CatKiller on 2008-11-28
Have you checked the hash of the file you downloaded? ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM))

Did you try the CD check from the boot menu?

Far more installation problems than you'd imagine are caused by cd errors.

---

