---
title: "all logs have errors"
date: 2008-07-28
forum: General Help
---

### Post by justborn on 2008-07-28
all my logs have errors ,i want to rectify them.


from where should i start ,how do i paste my logs here.

---

### Post by UbuntuNerd on 2008-07-28
take a screen shot and get the url and post it

---

### Post by justborn on 2008-07-28
> **jperez78 said:**
> take a screen shot and get the url and post it

but wher r the logs in my comp

---

### Post by ryanhaigh on 2008-07-28
> **justborn said:**
> all my logs have errors.

If you don't know where your logs are how are you sure that they ALL have errors. Most of your log files can be found in /var/log. Simply copy the files containing the errors you would like to rectify to your desktop, add .txt to the end of the file and upload with your next post. You can also use system>admin>system logs and copy and paste from there if you prefer that interface.

---

### Post by justborn on 2008-07-28
lets start by pasting the 'auth.log'

```
Jul 28 19:58:19 appy-desktop polkit-grant-helper-pam[32702]: pam_smbpass(polkit:auth): unrecognized option [missingok]
Jul 28 19:58:19 appy-desktop polkit-grant-helper[32699]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 32503 [uid=1000] [auth=appy]
Jul 28 20:12:36 appy-desktop gdm[5689]: pam_unix(gdm:session): session closed for user appy
Jul 28 20:15:26 appy-desktop gdm[5602]: pam_smbpass(gdm:auth): unrecognized option [missingok]
Jul 28 20:15:26 appy-desktop gdm[5602]: pam_unix(gdm:session): session opened for user appy by (uid=0)
Jul 28 20:17:02 appy-desktop CRON[6413]: pam_unix(cron:account): account root has expired (account expired)
```

---

### Post by justborn on 2008-07-30
someone please help me

---

### Post by unutbu on 2008-07-30
Perhaps try this: [http://ubuntuforums.org/showpost.php?p=5028796&postcount=2](http://ubuntuforums.org/showpost.php?p=5028796&postcount=2)

---

### Post by justborn on 2008-07-31
> **unutbu said:**
> Perhaps try this: [http://ubuntuforums.org/showpost.php?p=5028796&postcount=2](http://ubuntuforums.org/showpost.php?p=5028796&postcount=2)

ur thing helped me ,now i can boot the normal mode,but still have other problems with pulse-audio.




can u tell me why the problem occured & how did it get rectified ,when i followed the link.

---

### Post by unutbu on 2008-07-31
justborn, I'm sorry I don't understand this problem very well myself. All I did was google your error message and happened upon Markubuntu's post. Googling some more, it appears that he also filed a bug report:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/234479](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/234479)
That page should keep you abreast of any better solutions as they become known.

As for pulse-audio I know equally little, but you might want to check out these pages:

LordRaiden comprehensive guide to solving sound problems [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
PulseAudio fixes and System-Wide Equalizer Support hardy heron [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)
SoundTroubleshooting [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Also, posting a description of the problem, what you've tried, and any error messages you can find in logs or from terminal commands would be helpful.

---

