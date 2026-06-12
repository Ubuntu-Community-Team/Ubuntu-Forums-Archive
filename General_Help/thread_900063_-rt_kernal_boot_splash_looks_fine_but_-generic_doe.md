---
title: "-rt kernal boot splash looks fine but -generic does not"
date: 2008-08-25
forum: General Help
---

### Post by iamcims on 2008-08-25
boot splash prob fixed, the fonts appear fine during this process.

my log-in screen and everything after that, all fonts appear as blank boxes. as if im using a foreign font type without the fonts installed. Its odd and Im not sure what to do

---

### Post by iamcims on 2008-08-25
im speaking of the boot splash that loads after you hit enter on the kernel. I have been using -rt and it runs great.

---

### Post by carolinason on 2008-08-25
rt = real time.

look here
[https://wiki.ubuntu.com/RealTime/Hardy](https://wiki.ubuntu.com/RealTime/Hardy)

not sure about the boot splash corruption. make sure /boot/grub/menu.list looks similar to this
> /vmlinuz-2.6.26-5-generic root=UUID=a.along.hash.number ro quiet splash
with nothing after the word splash

---

### Post by iamcims on 2008-08-25
the menu.lst appears to look good with nothing after splash.

---

### Post by carolinason on 2008-08-25
Are you running Ibex?

---

### Post by iamcims on 2008-08-25
No, okay, somehow it works now.

But none of my fonts are loading, all i see are blank boxes, even under my font list/options.

---

### Post by oldmanteabags on 2008-08-25
This is happening in the boot splash.

---

### Post by iamcims on 2008-08-25
> **oldmanteabags said:**
> This is happening in the boot splash.

the fonts display fine in the boot splash but not after that.

---

### Post by oldmanteabags on 2008-08-25
can you check your local settings. i'm running kde, i'll boot into hardy live to see how to do it.

sorry i don't have the quick fix...

---

### Post by oldmanteabags on 2008-08-25
***EDIT wow you must think i'm in space. you explained your problem well but i was spacing out. 

check system->administration->language support make sure the language you need is selected.

i think your boxes are unicode boxes.

EDIT** who needs  dual boot with live cd's..

---

### Post by iamcims on 2008-08-25
> **oldmanteabags said:**
> ***EDIT wow you must think i'm in space. you explained your problem well but i was spacing out. 

check system->administration->language support make sure the language you need is selected.

i think your boxes are unicode boxes.

EDIT** who needs  dual boot with live cd's..

Ok, i booted my desktop live cd so i could see what i was doing. I counted the number of languages down the list so i would know which one was english. Problem is there is no "select" boxes like there should be, just the unicode boxes, I double clicked on it, tried everything i could, but no responses even after a hard reboot, and yes i hit Apply. When i first booted the language options, it downloaded a decent sized file(s) i figured this could be the new language so i thought might aswell let it do what it has to do. Well i did and rebooted and still the same boxes. I am really clueless as to what caused this and i dont really know what to do.

I really don't want to have to reinstall this would be a big problem to me.

---

### Post by iamcims on 2008-08-25
i tried running update manager, it downloaded some updates but no luck on fixing the text to a language.

Also, my terminal displays English and i can copy text from outside into this window to reveal what it means

---

