---
title: "Password for ubuntu user on live CD?"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by deangl on 2005-12-09
I am trying to run the live CD on an eMachine AMD64 with an ATI Radeon X200.
If I enter fglrx for the video driver, the Ubuntu login screen shows up.  It will not let me login as root.  And I don't know the password for the default ubuntu user.  Any other ideas???

Thanks,
Dale   :-)

---

### Post by dbott67 on 2005-12-09
As far as I know, there is no password for the Live CD.  I'm just taking a wild guess here, but you may try this:
```
sudo passwd root
```

Read this thread (it's for the 'installed' version, not the Live CD) but it may work.
[http://www.ubuntuguide.org/#setchangeenablerootpassword](http://www.ubuntuguide.org/#setchangeenablerootpassword)

-Dave

---

### Post by deangl on 2005-12-09
Thanks for the suggestion, however I can't get logged in to run a sudo command.  I was unable to CTRL-ALT-F1, F2, ... to alternate TTY terminals.  So it appears that I need the password for the default user which I believe is 'ubuntu'...

Anybody else have suggestions?

Thanks in advance.

Dale

---

### Post by aysiu on 2005-12-10
Here's what you do:

1. Boot up the live CD.
2. Before doing anything else, go to System > Administration > Users and Groups and reset your user password to something you want it to be (your username is *ubuntu*).
3. Do whatever you want--Ubuntu is the username, and it has sudo privileges, and you just set the password to something you can remember.

---

### Post by matthewv on 2005-12-10
Whenever the live cd asked for a password eg sudo, I found that "ubuntu" worked fine... could be way out.. but thats wat I remember

---

### Post by deangl on 2005-12-12
Hi,

Thanks to all that replied.  I am passed this now, although I am not sure what the unbuntu username password is on the LiveCD...

I was booting the Live CD, and due to challenges with brand new eMachine hardware (which includes a Radeon X200 on board), I was booting with "live-expert".  At the "run level" question I was able to put in "1" and get around my problem (of needing password).  

My original goal was to use the Live CD to confirm hardware compatibility with my new system, before actually writing to the hard drive.  I am using "fglrx" (instead of the probed "ATI" value) and things are working better.  I have now completed my initial Unbuntu install and proceeding to acquire needed packages for my system.

Again thanks for the assistance and I hope this discuss helps somebody else.

Dale   :-)

---

### Post by pedstunite on 2006-05-21
i think i have the same problem.  run level 1...what does this mean anyways?

---

### Post by pedstunite on 2006-05-21
i still can't change any of the parameters that need me to give a password.  I used run level 5.  I was not prompted to give a new username.  I did give a password for the root user though.  Am I missing something?

---

