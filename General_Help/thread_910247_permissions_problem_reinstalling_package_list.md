---
title: "permissions problem reinstalling package list"
date: 2008-09-04
forum: General Help
---

### Post by evencoil on 2008-09-04
I have a package list that was created from sbackup.

I then reinstalled Kubuntu and I want to restore the package list.

The package list is just called "package"

I'm using

```

sudo dpkg --set-selections <packages && apt-get dselect-upgrade

```

as per the instructions on the sbackup wiki.

But when I do this I get

```

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg), are you root?

```

What's going on?

---

### Post by oldos2er on 2008-09-04
You need to add "sudo" to the second command as well as the first. Should be 

sudo dpkg --set-selections <packages && sudo apt-get dselect-upgrade

---

### Post by evencoil on 2008-09-04
thanks!

---

### Post by Gannon8 on 2008-09-04
I had that problem before when one of my packages I was downloading had a problem. Rebooting fixes it.

---

