---
title: "KAudioCreator"
date: 2008-10-19
forum: General Help
---

### Post by WMG_Perth on 2008-10-19
Is there a way to install KAudioCreator in Kubuntu 8.10 beta.
When I try to install it with apt-get install kaudiocreator, the system tells me that it couldn find kaudiocreator.
Is there a specific repository I need to enable?

Thanks

---

### Post by clickwir on 2008-10-19
I'd like to second the "me too".

clickwir@mach:~$ sudo apt-get install kaudiocreator
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package kaudiocreator is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kaudiocreator has no installation candidate


What happened to it, it was there in hardy, I upgrade and now it's gone. This was a very useful app, I think if it's been removed for good, that I'll need to go find a .deb for it and install it manually.

---

### Post by tehsi on 2008-11-04
I'm missing this app too; what's happened to it?

---

### Post by clickwir on 2008-11-11
Anyone have any ideas? I'm assuming it's either no longer made/supported with KDE4 or it's just not ready yet. Honestly, for me, it was just about perfect and I think I'm going to have to install a VM of Kubuntu Hardy just to get it back so I can use it. KDE4 is growing on me, but it's still lacking huge chucks of things that KDE3 had, and I'm assuming KAudioCreator is one of them.


PS. Why do you have to "activate" the quick reply section? It should just be on.

---

### Post by markus42 on 2008-11-23
I just hit the same problem. Some quick research, however, revealed to me that K3B is not just a CD burning tool but also quite a wonderful application for ripping audio CDs in all kinds of formats. The according option is called "Audio CD auslesen" in German (literally: "Read out audio CD") and can be fond under the "Futher actions" button after startup.

Combined with suitable add-ons, K3B supports OGG, MP3, Flac, and WAV ripping (maybe more), one-file ripping, CDDB ad CD Text, file-size preview, and many other options. I think it lives up to KAudioCreator very well.

---

### Post by Lord Landis on 2008-12-13
I agree that K3B has some terrific functions built-in, and it does do a fairly good job as a ripper, but at the same time I don't want to have to install it on my laptop just so I can rip a CD every so often.

You can still download the .deb of kaudiocreator from Launchpad, though I haven't tried installing it manually yet, so I can't tell you if you'll hit any dependency issues or not.

[https://launchpad.net/ubuntu/intrepid/i386/kaudiocreator/4:3.5.9-0ubuntu2]("https://launchpad.net/ubuntu/intrepid/i386/kaudiocreator/4:3.5.9-0ubuntu2")

---

### Post by luggw1 on 2009-03-05
Well, I just tried installing kaudiocreator from the link in the previous message and gdebi baulks at kdemultimedia-kio-plugins as an unresolvable dependency.  That package is already installed, but is apparently a different version than kaudiocreator needs to work.

Now, regarding K3b, has anyone actually gotten it to work ripping mp3 files from a CD?  When I try, it immediately returns an error:

> Command failed: lame -h --tt Inside Out --ta David Meece --tl Once In A Lifetime --ty 1993 --tc - /music//David_Meece/Once_In_A_Lifetime/01-Inside_Out.mp3
Error while encoding track 1

This is the command that K3b supplied for the lame encoder:
```
lame -h --tt %t --ta %a --tl %m --ty %y --tc %c - %f
```

If I read the command line right, the "-" before the command line is telling lame to get its input from stdin, but there is something amiss.  I'd be interested to hear is someone is actually getting this to work and how they did it.

Thanks.
Bill Lugg

---

