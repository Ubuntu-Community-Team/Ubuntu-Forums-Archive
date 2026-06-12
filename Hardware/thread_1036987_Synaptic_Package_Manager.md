---
title: "Synaptic Package Manager"
date: 2009-01-11
forum: Hardware
---

### Post by Wespen on 2009-01-11
New User Question. I was downloading Limewire last night and somehow the installation was interupted. When I open the Synaptic Package Manager, a window comes up and says:

An Error Occurred

E: dpkg -- configure - a' to correct problem
E: -cache - > open()failed please report

Everything on the computer still works fine, however I am unable to install new programs, or run the syaptic package manager. I would appreciate any help anyone can offer.

---

### Post by tbj61898 on 2009-01-11
> **Wespen said:**
> 
E: dpkg -- configure - a' to correct problem
E: -cache - > open()failed please report

Hello Wespen,
unfortunately I'm not able to reproduce your issue but, basing on [this]("http://www.linuxquestions.org/questions/ubuntu-63/dpkg-configure-a-error-361965/"), you should be able to restore the corruption by issuing:

```
# dpkg --configure -a
```

If it's not working, try to do the following:
```
cd /var/lib/dpkg/updates
mv * /tmp
```

Please keep in mind [COLOR="Red"]You are about to remove files[/COLOR] from that directory, moving them to /tmp (just in case You remove something that wasn't supposed to be removed). Pay special attention to your current working directory and backup anything important on your machine before operating.

Please have a look to the above weblink and follow entire thread to understand if that problem apply exactly to your issue and let Us know.

Hope this helps,
Andrè

---

### Post by howefield on 2009-01-11
You might need to precede the command with sudo
```

sudo dpkg --configure -a
```

---

### Post by Wespen on 2009-01-11
I tried preceding the command with sudo and the system appears to be back to normal. I sincerely thank you for your help to a new user. I used windows since the late 80's and switched over to Unbuntu in the summer. It is a great operating system is all I can say. This is the first issue that I have had, and it was caused by my own error. Again, thanks.

Jim

---

### Post by yue232qi121 on 2009-01-11
is [runescape powerleveling](http://www.powerleveling-runescape.com) safe??every one know.

---

### Post by mLeenie on 2009-02-02
Adding sudo to the beginning worked for me as well. Thank you very much for answering this question.

---

