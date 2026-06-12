---
title: "ffmpeg and libswscaled will not update"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by labinnsw on 2009-05-09
Just installed Cinelerra [http://ubuntuforums.org/showthread.php?t=596160]("http://ubuntuforums.org/showthread.php?t=596160"), but if I remember correctly the problem started just before not after the install. I can't remember the sequence for sure. Any way this is taken from auth.log. ```
May  9 20:40:28 labinnsw-desktop sudo: pam_smbpass(sudo:auth): unrecognized option [missingok]
May  9 20:40:28 labinnsw-desktop sudo: labinnsw : TTY=unknown ; PWD=/home/labinnsw ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 83886083 -o Synaptic::closeZvt=true --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpvqSMc2
May  9 20:40:28 labinnsw-desktop sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
May  9 20:40:28 labinnsw-desktop sudo: pam_unix(sudo:session): session closed for user root
May  9 20:41:46 labinnsw-desktop sudo: labinnsw : TTY=unknown ; PWD=/home/labinnsw ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 83886083 -o Synaptic::closeZvt=true --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpX00E-r
May  9 20:41:46 labinnsw-desktop sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
May  9 20:41:46 labinnsw-desktop sudo: pam_unix(sudo:session): session closed for user root
```

Any ideas as to cause and resolution?

---

### Post by Triptol on 2009-05-09
Looks like you have a problem with your authentication.

What happens if you try the following in a terminal:

```
sudo -i
aptitude dist-upgrade
```

---

### Post by labinnsw on 2009-05-09
This is the result.

```
root@labinnsw-desktop:~# aptitiude dist-upgrade
-bash: aptitiude: command not found
```

Sorry, just noticed the typo. I am trying it again.

---

### Post by labinnsw on 2009-05-09
Absolutely Brilliant!!! (Always wanted to say that)

That was the fix I needed. Thanks.

---

### Post by Triptol on 2009-05-09
Sorry...

```
aptitude 
```

is the right speling.

---

### Post by labinnsw on 2009-05-09
In the excitement I forgot to tag it solved.

---

### Post by Triptol on 2009-05-09
That is good news. Was this the solution, or did you find something else?

Edit: ooops, sorry you already answered that one... Glad it helped.

---

