---
title: "[SOLVED] Automagic after kernel update?"
date: 2008-10-17
forum: General Help
---

### Post by Niniel on 2008-10-17
I just applied the update to the 2.6.24.21 kernel, and when I went to (re)set a Grub background image with Kgrubeditor, it warned me that my menu list was Automagic protected. 
I have not ever used Automagic, so I'm wondering how I got that message. The start menu looks a bit strange as well...
Is this the editor being confused or what? But why would it claim Automagic protection?

---

### Post by Elfy on 2008-10-17
I assume that if you look at your menu list you will see the kernels which get updated between these lines

> ### BEGIN AUTOMAGIC KERNELS LIST
<snip>
### END DEBIAN AUTOMAGIC KERNELS LIST

I've never used Kgrubeditor, I was going to look but I'd need to download ~70Mb on gnome, so I still haven't :)

I would guess that it's warning that there are such entries in your grub. If you have normally used another editor and never had a problem then I would think that's all it is.

---

### Post by Niniel on 2008-10-17
Yes, I see those entries.
But since when is Ubuntu using Automagic? I thought that stuff was seen as "the devil" around here? :)

---

### Post by Elfy on 2008-10-17
No idea I've only been using buntu since May 2007 - it was like it when I turned up.

---

### Post by Niniel on 2008-10-18
I never had that, not when I installed 7.10 nor when I upgraded to 8.04 nor with any of the previous kernel upgrades.

And on top of that, the new 21 kernel isn't even booting right. Instead of going to the disk-unlock password it starts some junk (all usb-related as far as I can tell) and then just hangs. Which is not surprising since the hd is still encrypted. 
Had to go back to the 19 kernel to get my box up and running again.

---

### Post by Elfy on 2008-10-18
It's been there for a long tome to my knowledge; have you always used kgrubeditor, you don't get warnings with other editors.

There have been otheres with problems with the kernel it seems.

---

### Post by Artemis_Fowl on 2008-10-18
Yes, indeed. Automagic is not a recent addition. It has been there for quite some time (ever since the very first Ubuntu version, if I'm not mistaken).

Automagic is good because when your kernel gets updated, your boot menu automatically updates the *buntu entries so as to boot the new kernel. This warning you get is just to remind you that moving an Automagic entry should not be done, to avoid strange situations...

Btw, that KGRUBEditor version you use is old. Last release is 0.8.5 which will ship by default with Kubuntu Intrepid.

---

### Post by louieb on 2008-10-18
Automagic comes to Ubuntu from Debian. (Ubuntu is based on Debian). Its been  there since I started using Ubuntu Linux (v 5.10, the 2nd release) probably was in the 1st release too.  
 When there is a kernel upgrade the module update-grub uses the options  between the lines.     
```

## ## Start Default Options ##
... options here ...
## ## End Default Options ##

```to build the entry(s) for the new kernel.  
If you have changed something between those lines that might account for the new kernel not working.   You should compare the kernel statement  in the working and not working entries. If they are the same except for the kernel file name,  then you will know that its a problem with the new kernel. Might file a   [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu") report.

Good Luck.

---

