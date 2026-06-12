---
title: "Obex File Transfer"
date: 2008-07-03
forum: Hardware
---

### Post by Windsurfer619 on 2008-07-03
When I was using Gutsy, I could just pair my phone (bluetooth) to browse it using Obex, and I even copied a few songs over using nautilus drag and drop.
Since upgrading to Hardy, I can browse and copy files FROM the phone just like before, but now when I try to copy a file TO the phone, it gives me the error:
```
Operation not supported by backend
```

Any ideas how I can fix this?

PS. My phone does not support Obex push, so I can't do the whole "Send To..." routine.

---

### Post by Windsurfer619 on 2008-07-20
buuuuump

---

### Post by Windsurfer619 on 2008-10-11
Jesus christ I just upgraded to Intrepid and this problem was not fixed. Went on google searching to see if it's been fixed and saw this post and I thought "Hey! That's my exact problem!" and I went to reply... only to see I was replying to myself.
I guess I'm just trying to say "Buuuummmmmmppppp!"

---

### Post by kwhitefoot on 2008-10-31
I have exactly the same experience.  Is anyone working on fixing this, or is there a workaround?  It's really embarrassing, I used to be able to say to my colleagues that Ubuntu and Blue Tooth worked so much better than Windows.  But now it's not true.

---

### Post by Windsurfer619 on 2008-11-01
After googling and reading man pages for a while, it would seem that "obexftp" does exactly what nautilus used to do.
To use it, simply type in a terminal 
<code>obexftp -b 00:13:00:6C:3E:22 -p song.mp3</code>
Where that mac address is your phone and song.mp3 is the file you want to send. It doesn't have to be music, either.

---

### Post by oddish2211 on 2008-11-11
i have the same problem, but the workaround you said isn't working for me because i want to transfer 50> files to a directory somewhere on my bluetooth enabled phone.
isn't there another application for browsing + sending files over bluetooth?

---

### Post by CTho9305 on 2009-07-12
In Intrepid, a command-line app called "bluetooth-browser" shows me a list of bluetooth devices and then lets me browse the chosen device with Nautilus.  There's probably some way to invoke bluetooth-browser with a GUI, but I didn't find it.

---

### Post by Roy Damman on 2010-06-02
Try to install package 'openobex-apps'. This solved my problems.

---

### Post by Reggino on 2011-02-04
Hi,

I had the same problem when i tried to copy files from a (samba) network share to my Bluetooth device. I somehow solved this by first copying the files to my local disk and THEN transfer it to my phone. Hope this helps

---

