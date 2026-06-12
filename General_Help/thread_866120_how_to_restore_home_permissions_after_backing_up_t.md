---
title: "how to restore /home permissions after backing up to a fat32 drive!"
date: 2008-07-21
forum: General Help
---

### Post by vjkeito on 2008-07-21
I went a foolishly backed up my entire /home directory onto a fat32 drive and now after I've overwritten my nearly fresh install with the backed up version it appears to have played around with the permissions. I logged out and back in again receiving an error relating to .dmrc and the permissions needing to be 644 for that file.  also to make sure they belonged to the correct user (jondoe for the sake of this article).

though it did boot into gnome. compiz appears to have reverted to default settings though and has not reloaded my backed up settings,  firefox on the other hand has! (weird)

Is there an easy way out of this, I've read certain threads about sudo chmod -R 755 /home/jondoe/

and others [http://ubuntuforums.org/archive/index.php/t-105156.html]("http://ubuntuforums.org/archive/index.php/t-105156.html") & [http://ubuntuforums.org/archive/index.php/t-524986.html]("http://ubuntuforums.org/archive/index.php/t-524986.html") but none seem to all agree on what the correct way out of this is.

I've run ls -l and my permissions regarding read/write/execute seem ok

please someone break this down for me in plain english! ;0)

---

### Post by TeeAhr1 on 2008-07-21
First question: Can you show me an example of the ls output?
Second question: Have you tried "chown -R jondoe /home/jondoe"? I've had files mysterously re-owner themselves before.

---

### Post by TeeAhr1 on 2008-07-21
Sorry, somehow I managed to post a reply to the wrong thread here. Read the one above this one, it's real, and pretend this one's not here ;)

---

### Post by drs305 on 2008-07-21
```
sudo chmod 644 /home/*username*/.dmrc
sudo chmod 755 /home/*username*
sudo chown *username*: /home/*username*
sudo shutdown -r now

```

The last line reboots the system. Substitute your username.

---

### Post by vjkeito on 2008-07-21
thank you !

---

