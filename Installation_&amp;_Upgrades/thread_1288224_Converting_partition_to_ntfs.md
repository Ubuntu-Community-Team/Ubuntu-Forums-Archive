---
title: "Converting partition to ntfs"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by obvious_hat on 2009-10-11
I have recently been having troubles with windows vista, I tried to fix it without reinstalling but nothing worked. So I'm working with ubuntu to reinstall it. However in order to do this I needed to delete windows manually via partition editor. However I can't change the partition format into ntfs. If anyone knows how I can do this I would appreciate the knowledge

---

### Post by LinuxRules1 on 2009-10-11
you should be able to delete the windows partition and format it to ntfs with gparted.

to install gparted go to terminal an type this command.

```

sudo apt-get install gparted

```

to add ntfs support for gparted type this command into terminal.

```

sudo apt-get install ntfsprogs

```

Hope This Helps.

---

### Post by obvious_hat on 2009-10-11
> **LinuxRules1 said:**
> you should be able to delete the windows partition and format it to ntfs with gparted.

to install gparted go to terminal an type this command.

```

sudo apt-get install gparted

```

to add ntfs support for gparted type this command into terminal.

```

sudo apt-get install ntfsprogs

```

Hope This Helps.

This didn't work, is there anything else I could do?

---

### Post by obvious_hat on 2009-10-11
wait... nevermind, it worked, thankyou :)

---

### Post by Bartender on 2009-10-11
For this kind of work, I strongly suggest creating a stand-alone partitioning CD.  Link below my sig.  Look for the latest stable .iso, download it, convert to a bootable CD just like you would an Ubuntu download.

---

