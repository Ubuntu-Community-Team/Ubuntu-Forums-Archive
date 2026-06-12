---
title: "lirc unknown remote control, need to change button commands"
date: 2008-10-27
forum: General Help
---

### Post by lmellor on 2008-10-27
Hi, I have recently purchased a remote control from ebay which registers as a linux input layer compatible remote.  The red, yellow, green and blue buttons seem to give commands of ctrl+alt+f1, f2, f3, and f4 however.  Obviously these are not commands I'd like to have at the disposal of the remote control.  Can anybody suggest how to go about changing these? I have installed the remote control panel from the ubuntu repository yet I don't seem to be able to affect these buttons.

Any help would be massively appreciated.

:confused:

---

### Post by lmellor on 2008-11-02
hmmm, nobody's quite sure it seems, the odd thing is that my remote was operating rhythmbox perfectly well, yet what I noticed this morning was that the lirc plugin for rhythmbox wasn't switched on which leads me to believe that maybe some other app is giving me control.  I am now even more confused, can anybody shed any light into what program would be the best one to start looking at, this remote has loads of buttons that could benefit from having something useful attached to them rather than ttl, etc.

---

### Post by lmellor on 2008-11-02
even more confusion if at all possible, I have removed all lirc packages with the exception of liblircclient0 which informs me that it will be uninstalling all kinds of things along with it, 1 of which is rhythmbox which I certainly want to keep.  The remote still functions exactly the same as it always has, even after a reboot or two.  Something else must be receiving the commands from the remote other than lirc.

Please somebody help, this is really really confusing me now.

As far as my ubuntu installation goes it was originally a fresh install of hardy which I have recently upgraded to intrepid, I am running on the AMD64 architecture.

---

### Post by lmellor on 2008-11-04
further inspection has uncovered that windows xp picks this up as a hid compliant device which suggests to me that it is running as some sort of virtual mouse, I have included a link to the item on ebay, this really seems weird to me, can nobody shed any light on this?

[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=260298643014]("http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=260298643014")

---

