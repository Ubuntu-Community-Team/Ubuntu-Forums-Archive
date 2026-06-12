---
title: "nVidia Driver"
date: 2022-02-07
forum: Hardware
---

### Post by waffen on 2022-02-07
Hello,

Im using Ubuntu 21.10 + Ci5-10400F + nVidia GTX 1650 card, by default the OS install nVidia driver v. 470, but I can see in the repos v.510

Can I install it with no risk? I have Steam +  Proton installed and running with no issues, I'm playing some windows games like: Age of Empires 2 and 4, WotBlitz, Doom, etc.

Thanks!

---

### Post by Autodave on 2022-02-07
Go to "Additional drivers" and let it search for a moment.  It will then recommend the correct driver (which is the 510}.  Click on the 510 that is recommended and it will install.

---

### Post by waffen on 2022-02-07
I just installed it, alll good. Thanks

---

### Post by DAB4970 on 2022-02-10
I have the same card in my custom desktop.  It's not allowing me to switch to what shows as the metapackage 510.  Is there a cmd to use in the CLI?  I am using 20.04.3 LTS.  Current driver 470 shows as  "manually installed".

Update:
I searched www and found article on linuxcapable dot com.  Completed upgrade and installation of 510.47.03 without errors.  I was almost to the point of giving up on nVidia with Ubuntu.

---

### Post by waffen on 2022-02-10
> **DAB4970 said:**
> I have the same card in my custom desktop.  It's not allowing me to switch to what shows as the metapackage 510.  Is there a cmd to use in the CLI?  I am using 20.04.3 LTS.  Current driver 470 shows as  "manually installed".

Sure, go to Software Update>Config>More Controllers  and choose the metapackage v. 510 (privative,tested)  and apply changes. My Ubuntu is in Spanish I just translate the names...

---

### Post by Autodave on 2022-02-11
Please remember to mark this thread as "closed" by going to top of thread, right corner, "Thread Tools".

---

