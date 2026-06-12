---
title: "Questions upgrading to Breezy"
date: 2005-11-27
forum: General Help
---

### Post by lightcastle on 2005-11-27
Hi everyone. 

I installed Hoary for AMD64 at the urging of a friend back when I got my new desktop in May.  It was an immensely frustrating experience as nothing worked with 64-bit architecture and the whole thing just pissed me off. After swearing that Ubuntu was crippleware, I eventually calmed down and realized it was just that 64-bit stuff is too new, and so I should just try it again later.

I went an installed SimplyMEPIS on a second partition and that's fine, although I don't like the cluttered KDE desktop and it doesn't seem to have an automatic update warnings for security like Ubuntu does.

So, it is November and I would like to try Breezy, and see how it works.

Some questions, keeping in mind I am an utter newbie who thinks this magic box is best placated by sacrificing chickens *grin*: 

1) How the hell do I update to Breezy, anyway? I seem to have found some instructions on the web, but the fact that there isn't a "how to" on the Ubuntu site itself scares me. Especially since I am updating from the 64-bit version. I can't figure out if there are separate versions again, or if it is all integrated, or if I should care.

2) I have my home directory off in a separate partition. The last 2 people I know who updated from Hoary to Breezy lost all their data and package installs. How do I avoid this?

3) I have heard that WINE doesn't run on 64-bit machines with Ubuntu, and I now find myself in need of it. True, false, Urban legend?

4) If I do upgrade Ubuntu, will I lose the ability to dual-boot my system (that became an issue when I put Mepis on.)

Thanks for any help you can give.

---

### Post by aysiu on 2005-11-27
[QUOTE=lightcastle]After swearing that Ubuntu was crippleware, I eventually calmed down and realized it was just that 64-bit stuff is too new, and so I should just try it again later.[/quote] Have you tried the regular x86 edition on your 64-bit computer? That may work.

> 
1) How the hell do I update to Breezy, anyway? I seem to have found some instructions on the web, but the fact that there isn't a "how to" on the Ubuntu site itself scares me. Especially since I am updating from the 64-bit version. I can't figure out if there are separate versions again, or if it is all integrated, or if I should care. You change all your sources from Hoary ones to Breezy ones (see the first link in my sig) and then type this in a terminal ```
sudo apt-get update
sudo apt-get dist-upgrade
``` This assumes, of course, you already have Hoary installed.

> 
2) I have my home directory off in a separate partition. The last 2 people I know who updated from Hoary to Breezy lost all their data and package installs. How do I avoid this? If it's in a separate partition, make sure to **mount** that partition as /home and choose to **not format** the partition.

> 
3) I have heard that WINE doesn't run on 64-bit machines with Ubuntu, and I now find myself in need of it. True, false, Urban legend? According to [this](http://www.winehq.com/hypermail/wine-devel/2003/12/0043.html), it should run just fine.

> 
4) If I do upgrade Ubuntu, will I lose the ability to dual-boot my system (that became an issue when I put Mepis on.) Not if you install Grub to the MBR. I'm assuming you mean dual-booting with Windows (not dual-booting with Mepis--though, that can be arranged, too).

---

### Post by Iandefor on 2005-11-27
Hi! Which Ubuntu page were you looking at? Try the [wiki]("https://wiki.ubuntu.com/"). 

I'll tell you what I did to upgrade:

1. Open up a terminal
2. Type in ```
sudo vi /etc/apt/sources.list 
``` It should be filled with a bunch of lines that look generally like this: 

```

deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

``` Before you go any farther, be sure that, on the bottom of the screen, it says "-- Insert --". If it doesn't, give the "Insert" key a thwack.
Now, wherever it says "hoary" go in and change it to "breezy". So, the above example should become 
```

deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

``` Done that? Hit [ESC], type in ":x" and hit enter. It should save and quit. Now, when you're back at the terminal, type in ```
sudo apt-get update
``` and, when that's finished, enter ```
sudo apt-get dist-ugrade
``` which'll then install all the new Breezy packages. Or, you could just reinstall over Hoary :). Using the method mentioned above, you're separate /home partition should be safe. I don't know whether or not WINE runs in 64-bit. What application do you need? Upgrading shouldn't become an issue with dual-booting.

EDIT: Just fixed an issue with formatting

---

