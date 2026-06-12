---
title: "Windows MCE Remote on Hardy"
date: 2008-11-25
forum: General Help
---

### Post by gjr5017 on 2008-11-25
I have a Windows MCE Remote that I got a while ago with my old Dell Laptop. I was wondering if there was a way to get this to work with Ubuntu so that I could skip songs in my media player and turn up the volume....these are basically all the functions I'll need from it. This is the remote that I have.

[http://gbpvr.com/pmwiki/uploads/Main/MS-MCE_Remote_2005_w_Beanbag.jpg](http://gbpvr.com/pmwiki/uploads/Main/MS-MCE_Remote_2005_w_Beanbag.jpg)

---

### Post by gjr5017 on 2008-11-26
Anyone?

---

### Post by Fire_Chief on 2008-11-26
I have this same remote for my Mythbuntu system and it works great out of the box. For a normal Ubuntu system, you'll need to install and configure Lirc. 

Have a look here
[https://help.ubuntu.com/community/InstallLirc/Hardy]("https://help.ubuntu.com/community/InstallLirc/Hardy")

Cheers!

---

### Post by gjr5017 on 2008-11-26
I've tried to go about installing it and I select the MCE Remote - the new phillips one and none for the 2nd option. Then when I do the $ irw and press buttons on my remote nothing shows up at all.

---

### Post by gjr5017 on 2008-11-26
Anyone? I'm not really sure what I'm doing wrong with installing lirc

---

### Post by bthessel on 2008-11-28
> **gjr5017 said:**
> Anyone? I'm not really sure what I'm doing wrong with installing lirc

When you run irw does it just come back to a prompt or give an error? I am having the same problem with it just coming back to the prompt.

---

### Post by gjr5017 on 2008-11-28
It just goes down to the next line and nothing happens at all.

---

### Post by gjr5017 on 2008-11-30
Bump.

---

### Post by Fire_Chief on 2008-12-01
Are you running irw as root? I had problems where I was not seeing the input in irw unless I ran as root (not sure why though).

Also, just to be sure, do you have Lirc started?
```
sudo /etc/init.d/lircd start
```

Cheers!

---

### Post by gjr5017 on 2008-12-01
Tried sudo irw and nothing came but hten tried the command you gave me to start lircd and it says command not found then i ran the same thing you gave me but just /etc/init.d/lirc start - no d on the end and it says - Starting Remote Control Daemons - Fail

---

### Post by Fire_Chief on 2008-12-01
Is there anything in the logs indicating why it failed to start?

---

### Post by gjr5017 on 2008-12-01
Where are the logs that would say anything about that?

---

### Post by Fire_Chief on 2008-12-02
You may find related errors in the messages log file
```
tail -n 300 /var/log/messages
```
Or in the syslog
```
tail -n 300 /var/log/syslog
```

---

### Post by gjr5017 on 2008-12-12
I didn't really find anything while sifting through both of those logs...any other ideas as to how I can get this to work?

---

### Post by Fire_Chief on 2008-12-15
I suppose you could remove and reinstall LIRC and try it from a clean config? When you press buttons on the remote, does the receiver have a red light that blinks indicating that it is receiving the signal?

---

