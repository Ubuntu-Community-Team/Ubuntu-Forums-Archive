---
title: "Failing to install on Amilo Xa2528"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by marksken on 2009-03-05
Can't install Ubuntu on a laptop Amilo Xa2528, not even boot the live cd.

I've been looking on lots of forums and the problem seems to be in the kernel, i've got a solution in the mail but don't understand how to do it 

[http://bugzilla.kernel.org/attachment.cgi?id=18748&action=view](http://bugzilla.kernel.org/attachment.cgi?id=18748&action=view)

Any one who can help me ?

---

### Post by Rockard on 2009-03-09
Same problem here with my xa2528. I bought my computer a year ago and recently looked around if the problem had been fixed... still looks bad! =(

Seems like a fix has been submitted to the kernel.
This thread indicates that is has been fixed, but ubuntu still seems to have problems: [http://www.amilo-forum.de/topic,19913,15,-Getting-the-DVDdrive-to-work-Amilo-XA2528.html?sid=c5bd41679f8b5b957e5408993058ff2c](http://www.amilo-forum.de/topic,19913,15,-Getting-the-DVDdrive-to-work-Amilo-XA2528.html?sid=c5bd41679f8b5b957e5408993058ff2c)

I tried downloaded the latest ubuntu jaunty beta - still won't work.

I'm a programmer but I am too new to linux to be able to understand the simplyfied instructions in link in above post.

---

### Post by gedesby on 2009-04-19
hey there
i'm the ovner of a xa2528 and i got ubuntu to work but still missing webcam and dvd

here is my solution

in windovs:
download unetbootin 
download ubuntu
run unetbootin in "open as admin"and follow the instrucs.
i usede the isomenubar and locadede the ubuntu and installede it on a usb
then i rebooted in usb and it workd
i installede the ubuntu on the clean hdd2 drive and i use the bios to choose vista or ubuntu.
vista on hdd1 and ubuntu on hdd2

**_*[COLOR="Red"]DON'T[/COLOR]*_** install the bootmanager to boot from hdd1 if you still vant to use windovs.
i tryed and lost both "os"
but it can be restored.

---

### Post by gedesby on 2009-05-15
you can also try this french distro it is working for me

[http://74.125.79.132/translate_c?hl=da&langpair=auto%7Cda&u=http://www.neufgiga.com/n/50-17/share/LNK711849f2dacf0e171/&rurl=translate.google.com&usg=ALkJrhivDqVTy7d_nNDKG4AR2AINZfbq2w](http://74.125.79.132/translate_c?hl=da&langpair=auto%7Cda&u=http://www.neufgiga.com/n/50-17/share/LNK711849f2dacf0e171/&rurl=translate.google.com&usg=ALkJrhivDqVTy7d_nNDKG4AR2AINZfbq2w)

but still missing:
sound (but working on it)

---

### Post by marksken on 2009-05-17
Hello, 

i found a config file that you have to use with kernel 2.6.29.1 or higher, i tried it and now cd/dvd drive works, is used a netinstall disk and than i compiled the kernel with this config file

---

### Post by marksken on 2009-06-15
Did you make that french distro ?
Or any idea who made it?

---

### Post by gedesby on 2009-06-15
no. i read on the French forum ;)and found it but i don't no ho made it

---

### Post by marksken on 2009-06-22
Do you still know what forum you found it ?

Thanx

---

### Post by gedesby on 2009-06-28
hey i found it here:
[http://forum.ubuntu-fr.org/viewtopic.php?id=180604&p=13](http://forum.ubuntu-fr.org/viewtopic.php?id=180604&p=13)

24/4 2009 12:25   topic 318

when you push the iso file it redirect you to another site just Wait and the isofile will be showen

---

