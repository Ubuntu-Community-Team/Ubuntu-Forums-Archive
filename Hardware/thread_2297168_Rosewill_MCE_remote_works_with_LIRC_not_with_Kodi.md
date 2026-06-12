---
title: "Rosewill MCE remote works with LIRC not with Kodi"
date: 2015-10-01
forum: Hardware
---

### Post by SuperFreak on 2015-10-01
I have a Rosewill RHRC-11002 MCE Remote that I am trying to get to work with a new Giabyte Brix GB-BXBT-1900 HTPC loaded with Ubuntu 14.04. Out of the box the remote will work for the volume, mute left right up and down buttons but not much else (without being able to use the OK button to select options it is pretty well useless).
I installed LIRC and tried the buttons using irw which worked perfectly
```
david@MainSqueeze:~$ sudo dpkg-reconfigure lirc
[sudo] password for david: 
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) :                                   [ OK ] 
david@MainSqueeze:~$ irw
000000037ff07bde 00 KEY_RIGHT mceusb
000000037ff07bde 01 KEY_RIGHT mceusb
000000037ff07be0 00 KEY_DOWN mceusb
000000037ff07be0 01 KEY_DOWN mceusb
000000037ff07bf2 00 KEY_HOME mceusb
000000037ff07bf2 01 KEY_HOME mceusb
000000037ff07bed 00 KEY_CHANNELUP mceusb
000000037ff07bed 01 KEY_CHANNELUP mceusb
000000037ff07bdd 00 KEY_OK mceusb
000000037ff07bdd 01 KEY_OK mceusb
000000037ff07bee 00 KEY_VOLUMEDOWN mceusb
000000037ff07bee 01 KEY_VOLUMEDOWN mceusb
000000037ff07bb8 00 KEY_AUDIO mceusb
000000037ff07bb8 01 KEY_AUDIO mceusb
000000037ff07bfc 00 KEY_3 mceusb
000000037ff07bfc 01 KEY_3 mceusb
000000037ff07bfd 00 KEY_2 mceusb
000000037ff07bfd 01 KEY_2 mceusb


```
Problem is it still won't work with Kodi. Not sure what the problem is as I thought MCE remotes worked out of the box

---

### Post by TheFu on 2015-10-01
I just did a major update on my Kodi box last weekend and the MCE remote stopped working like it worked previously. It wasn't all bad, but the green button didn't work and double button presses were always seen.  The fix for me was easy.  Remove the softlink and put in a different one for  my RC6 remote.   In /etc/lirc  -  lircd.conf was a link. Just had to point that to rc6-mce-lircd.conf.  I rebooted because I was lazy. All has been good since then.

Normally, I don't reboot over some tiny change like this - just a restart should have been enough.

---

### Post by SuperFreak on 2015-10-01
Thanks for the reply.
Turns out to be a simple matter of rebooting after configuring LIRC. As soon as I rebooted it worked :0)

---

