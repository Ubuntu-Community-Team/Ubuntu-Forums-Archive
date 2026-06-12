---
title: "Ipod Touch successfully mounts, but Rhythmbox cant see it"
date: 2008-11-01
forum: Hardware
---

### Post by snowball1288 on 2008-11-01
So i have an iPod Touch, jailbroken w/ 1.1.1 firmware.  I had it fully functioning under Hardy with the ipod-convenience package.  once it was mounted, it would sync properly with amarok, gtkpod, and rhythmbox.  

After upgrading to Intrepid and setting it all back up again, syncing with Amarok and gtkpod still work just fine, but it seems Rhythmbox doesnt see it.  Its mounted just as it was before, but somehow rhythmbox's iPod plugin just misses it.  

Is this a bug?  perhaps im forgetting something?  Can anyone else use an iPod touch in rhythmbox under Intrepid?

---

### Post by dima338 on 2008-11-03
Were you using SSH before?

---

### Post by snowball1288 on 2008-11-08
yes, it was using SSH.  the ipod convenience package scripts "ipod-touch-mount" and "ipod-touch-umount".  these successfully execute and i see an ipod icon on my desktop and can transfer music/video using gtkpod or amarok.  im going to pull my old ipod-touch-mount script off my hardy partition and see if its different from the version in intrepid.

---

### Post by snowball1288 on 2008-11-08
and those scripts use sshfs.  Also, i just checked with my roommate's 80gb ipod classic, and it mounts just fine and shows up in rhythmbox.  so rhythmbox does see some ipods.

---

### Post by snowball1288 on 2008-11-08
also, i just examined the ipod-touch-mount and umount scripts and they're identical between hardy and intrepid.  i even copied out the old one from /usr/share/ipod-convenience from my hardy partition and moved it to my intrepid partition.  again, it mounts, gtkpod reads it, amarok reads it, but rhythmbox acts like theres no ipod mounted.  i also tried manually mounting it using "sshfs root@[ipod's IP]:/var/root/Media /media/ipod".  again, gtkpod and amarok find this okay but rhythmbox doesnt.  im wondering if this is a bug in the new rhythmbox.  also, my sony vaio and my Asus Eee are both showing the same behavior... two systems, both working before but recently upgraded to intrepid (fresh installs though).  any other ideas?

---

### Post by myddewji13 on 2009-03-12
I'm having the same problem...Rhythmbox can't seem to see my touch at all...please let me know if anyone finds a solution!

---

### Post by Freezing Hot on 2009-03-13
Just throwing in that I have the same issue and am googling like all hell for an answer.

---

