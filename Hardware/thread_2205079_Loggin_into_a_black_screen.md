---
title: "Loggin into a black screen"
date: 2014-02-11
forum: Hardware
---

### Post by andrea18 on 2014-02-11
Trying to fix what my daughter did to her laptop. I know she was having issues with her mouse and League of Legends being a little jumpy so she was looking at installing some drivers. What driver mix up she installed, even she doesn't remember.

I myself am a Ubuntu newbie, she decided I needed a challenge before I even get mine out the box good. :)

Any place to start looking or figure out how to reinstall Ubuntu would be of great help. I can only get the computer to reboot from the CD, can't get it to a reinstall state. Is there a way to get it to reinstall?

Her laptop: Dell XPS
Ubuntu version: 13.10

I can get to the terminal ok and I can boot from the CD ok. Still have a black screen either way.

---

### Post by ubudog on 2014-02-11
If you are wanting to reinstall, just boot a live Ubuntu CD or flash drive, and fire up the installer.

---

### Post by Bucky Ball on 2014-02-11
A reinstall is generally a last resort. If there is personal data on this machine, I suggest you boot from the live media (the install disk/USB) to a desktop and back it up to an external device or another drive.

You tell us virtually nothing so a bit hard to help. Please go through the steps from switching the machine on to when it halts and report any and all error messages and what is happening when it does stop. Is there a cursor?

If you are stuck at a cursor but you can type (or it is asking you to login) login and issue:

```
sudo service lightdm start
```

You might like to have a scan of the third link in my signature. Cheers.

---

### Post by ppjdee on 2014-02-12
Could a reboot into kernel generic recovery mode maybe shorten the list? reboot then enter grub, select advanced options for ubuntu. choose recovery mode, what ever lateset kernel is...choose failsafeX in the menue that follows after. maybe it will boot into desktop.

edit: worse case/fastest solution...boot into live cd and try to move all your data to external drive. then reinstall the os.

---

