---
title: "[jeos] how to install GNOME?"
date: 2008-09-11
forum: General Help
---

### Post by pioa on 2008-09-11
Hello!

I am using vmware workstation and just installed Ubuntu Jeos. It works but gnome installation didn't work.
depends: gnome-keyring-manager but is not installable. E: broken packages

sudo apt-get install gnome-keyring-manager says no installation candidate available.

I've successfully done sudo apt-get update and sudo apt-get upgrade before.

How can I install GNOME under Ubuntu Jeos?

---

### Post by Pro-reason on 2008-09-11
First make sure that you have no broken packages

Do this on the command line:

```

sudo apt-get -f install

```

---

### Post by pioa on 2008-09-11
> **Pro-reason said:**
> First make sure that you have no broken packages

Do this on the command line:

```

sudo apt-get -f install

```

Done that, same result.

---

### Post by rickycodie on 2008-09-11
try a reinstall

sudo apt-get insall gnome-desktop

---

### Post by rickycodie on 2008-09-11
try a reinstall

sudo apt-get install gnome-desktop

sorry about the double post

---

### Post by pioa on 2008-09-11
There is no such packet gnome-desktop.

Reinstall is pointless, it's already a clean installation and I did try this now already the third time. Each time I did gave up at some point, deleted everything and try again later. I thought it's a good idea to ask in the forums.

Or asked otherwise... Anyone had success installing GNOME after Jeos?

---

### Post by schauerlich on 2008-09-11
> **pioa said:**
> There is no such packet gnome-desktop.

Reinstall is pointless, it's already a clean installation and I did try this now already the third time. Each time I did gave up at some point, deleted everything and try again later. I thought it's a good idea to ask in the forums.

Or asked otherwise... Anyone had success installing GNOME after Jeos?

The package is named ubuntu-desktop.

---

### Post by Pro-reason on 2008-09-11
Do this:

```

sudo apt-get update && sudo apt-get install ubuntu-desktop

```

Does it still tell you that something is broken?

If so, it can be best to force the removal of anything it says is blocking the installation process.

Purely for example:

```

sudo dpkg --remove --force-depends *gnome-core gnome-keyring gnome-menus*
sudo apt-get install -f ubuntu-desktop

```

---

### Post by Yannick Le Saint kyncani on 2008-09-11
> **EDavidBurg said:**
> The package is named ubuntu-desktop.

Yeah, the gnome meta-package is broken in ubuntu hardy (and has always been like this in hardy). So just install ubuntu-desktop.

---

### Post by pioa on 2008-09-12
> **EDavidBurg said:**
> The package is named ubuntu-desktop.
Ok, this worked.

---

