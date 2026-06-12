---
title: "Catalyst 10.1 compiled properly, but is not working."
date: 2010-02-12
forum: Hardware
---

### Post by Hoshikage on 2010-02-12
After distro hopping around for what seems like forever, I've settled on Ubuntu 8.04 LTS, until 10.04 comes out.

Anyway, I think I've gotten this problem before in the past, but I cannot for the life of me remember how I fixed it. 

Whenever I try to run... anything that'd use 3D, I get something like this

```
$ glxinfo |grep direct
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  13
  Current serial number in output stream:  13

```And I've got really horrible 2D performance. 

My system specs are as follows:
AMD Sempron 3400+ (2.01Ghz)
2GB DDR 400
Radeon HD 3450 w/ 256mb DDR2

and, I'm pretty sure everything else doesn't really matter. I've got it in my head that maybe building a newer kernel then rebuilding Catalyst might fix it, but I wonder if there's anything I can do to avoid rebuilding my kernel, as I have really slow compile times on this 6 year old machine. Thanks much.

---

### Post by markbuntu on 2010-02-12
Did you just run the installer or did you build the Hardy packages yourself?

---

### Post by Hoshikage on 2010-02-12
Oh sorry, I forgot add that in. I simply ran the installer rather than building packages. I've had problems when I built packages in the past. 

fglrx-install.log has no errors listed in it, btw.

---

### Post by markbuntu on 2010-02-12
Are ther any (EE) messages in the Xorg.0.log?

---

### Post by Hoshikage on 2010-02-12
I didn't check because X starts fine... I'll take a look a bit later when I have time and edit this post after running 
less /var/log/Xorg.0.log | grep EE

---

### Post by Hoshikage on 2010-02-13
```
$ less /var/log/Xorg.0.log |grep EE
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(EE) fglrx(0): XMM failed to open CMMQS connection.

```

I'm unsure, do I need to add a DRI section to my xorg.conf?

---

