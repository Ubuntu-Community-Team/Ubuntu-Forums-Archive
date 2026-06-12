---
title: "firewire and minidv camcorder"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by rachii on 2005-06-14
-when i plug in the camera and turn it on ubuntu locks up.   if i turn the camera off, ubuntu unfreezes.  it seems like its trying to load it, but when it does it doesnt know what to do and locks up?  any clue why or what im missing to get it too work.  its onboard nforce2 firewire,  fully updated hoary, and the camera is the JVC gr-d270u

i have searched all over these forums, various guides, wiki's, irc's. and google.  but havent found an answer.

im trying to setup my dvcamera over firewire in ubuntu so i can capture the video.

i have /dev/raw1394

if i do  "sudo lsmod | grep 1394"
i get:

  video1394              17740  0
  ohci1394               31876  1 video1394
  raw1394                28652  0
  ieee1394              100408  4 video1394,ohci1394,raw1394,sbp2 

i have sbp2, raw1394, and video1394 in my /etc/modules

kino does not report any problems with /dev/raw1394 permissions.

any thoughts or ideas would be great

thanks

---

### Post by CrackersKeenan on 2005-08-27
[QUOTE=rachii]-when i plug in the camera and turn it on ubuntu locks up.   if i turn the camera off, ubuntu unfreezes.  it seems like its trying to load it, but when it does it doesnt know what to do and locks up?  any clue why or what im missing to get it too work.  its onboard nforce2 firewire,  fully updated hoary, and the camera is the JVC gr-d270u

i have searched all over these forums, various guides, wiki's, irc's. and google.  but havent found an answer.

im trying to setup my dvcamera over firewire in ubuntu so i can capture the video.

i have /dev/raw1394

if i do  "sudo lsmod | grep 1394"
i get:

  video1394              17740  0
  ohci1394               31876  1 video1394
  raw1394                28652  0
  ieee1394              100408  4 video1394,ohci1394,raw1394,sbp2 

i have sbp2, raw1394, and video1394 in my /etc/modules

kino does not report any problems with /dev/raw1394 permissions.

any thoughts or ideas would be great

thanks[/QUOTE]
 This might not be much help (as I didn't really fix much) but I'll post in case.  I have a JVC GR-DVL510 which I started trying to use yesterday.  The first time I plugged it in, I had a lot of things running (XMMS, Firefox, Limewire) and the computer totally froze.  The second time, I did two things differently: (1) I used a different socket in my 1394 (Firewire) card, which has three sockets, and (2) Shut down all the other applications before plugging my camera in.  This worked, in that when I started kino I could capture.  But only if I started as root (sudo kino).

So, maybe try shutting other apps down, or try using a different port on your Firewire card?  Worked for me.  At some point I'll try the first port again and see if that was the problem.  At the moment I'm still a little tentative about crashing my computer again...

One prob I then had with kino was that I couldn't export as mpeg (etc).  It gave me some kind of error about how it couldn't write to the KINO audio channel... I'm still working on that one!

Hope this helps!

-- CK

---

### Post by CrackersKeenan on 2005-08-29
Fixed the exporting problem by adding the packages listed at 

[http://ubuntuforums.org/showthread.php?p=200211&highlight=kino#post200211](http://ubuntuforums.org/showthread.php?p=200211&highlight=kino#post200211)

---

