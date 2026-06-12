---
title: "[linuxwacom]missing headers"
date: 2005-09-10
forum: Hardware &amp; Laptops
---

### Post by djib on 2005-09-10
Hello,
I have bought a wacom pen tablet and I found a package named linuxwacom. When I tried to install it it said that my kernel didn't have the proper headers... What can I do ? (I don't know what other information I could give you)
Thanks for your help.

---

### Post by Leif on 2005-09-10
do you have the appropriate headers installed ? ie linux-headers-386, or whatever is appropriate for your system. search for headers under synaptic.

---

### Post by djib on 2005-09-10
[QUOTE=Leif]do you have the appropriate headers installed ? ie linux-headers-386, or whatever is appropriate for your system. search for headers under synaptic.[/QUOTE]
 Ok, I'll try that.
What are 'headers' by the way ? I mean what are they here for ?

---

### Post by Leif on 2005-09-10
they are system libraries. c headers, if that means anything to you.

---

### Post by djib on 2005-09-12
[QUOTE=Leif]they are system libraries. c headers, if that means anything to you.[/QUOTE]
 Ok, I installed the package linux-headers-686 and reinstalled the wacom-kernel-source  package.
The error I get is :
```
Error: kernel headers not found in '/usr/src/linux/'
```

---

### Post by Leif on 2005-09-12
In that case I'm afraid I don't know.

---

### Post by [Koba] on 2005-09-12
Hi

I have a tablet from Wacom too and had to go through a manual install. It was a nightmare I tell you. Back then I was using Mepis so all I can suggest is you try to get that package working.

If you decide to do a manual install I can try to help you from what I remember. I might have to go through it again myself if I decide to get it working with ubuntu.

[Koba]

---

### Post by graigsmith on 2005-09-13
ubuntu comes with the driver PRE-INSTALLED.  :)

all you have to do is add some lines to your xorg.conf,  and you have to enable pressure sensitivity in gimp.

see this  thread. to get those files edited.  I got mine working flawlessly just by editing one file, and changing some settings in the gimp.

[http://www.ubuntuforums.org/showthread.php?t=24149](http://www.ubuntuforums.org/showthread.php?t=24149)

edit, oh yeah, someone made a how to on this.   this pages sums up everything you need to do a little better than the first link.

[http://www.ubuntuforums.org/showthread.php?t=25151](http://www.ubuntuforums.org/showthread.php?t=25151)

---

### Post by djib on 2005-09-13
[QUOTE=graigsmith]ubuntu comes with the driver PRE-INSTALLED.  :)

all you have to do is add some lines to your xorg.conf,  and you have to enable pressure sensitivity in gimp.

see this  thread. to get those files edited.  I got mine working flawlessly just by editing one file, and changing some settings in the gimp.

[http://www.ubuntuforums.org/showthread.php?t=24149](http://www.ubuntuforums.org/showthread.php?t=24149)

edit, oh yeah, someone made a how to on this.   this pages sums up everything you need to do a little better than the first link.

[http://www.ubuntuforums.org/showthread.php?t=25151](http://www.ubuntuforums.org/showthread.php?t=25151)[/QUOTE]
 Thank you so much !!!!!

Ubuntu rocks !!!

---

