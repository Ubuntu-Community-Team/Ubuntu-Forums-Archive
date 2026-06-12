---
title: "uninstalling KDE4?"
date: 2008-09-02
forum: General Help
---

### Post by evencoil on 2008-09-02
I tried installing Kubuntu KDE4 over a Xubuntu install and didn't like it, so I installed Kubuntu KDE3 over it. So now I have Xubuntu, Kubuntu KDE3, Kubuntu KDE4. I'm going to only keep Kubuntu KDE3. I installed the KDE4 version with

```

sudo aptitude update && sudo aptitude install kubuntu-kde4-desktop

```

then I thought I would uninstall it by doing

```

sudo aptitude remove kubuntu-kde4-desktop

```
but nothing got removed. So then I tried
```

sudo aptitude remove kde4-core kde4

```
and then
```

sudo aptitude purge kde4-core kde4

```
and still nothing got removed.

I'd like to get rid of all of these KDE4 programs! Any suggestions? (Oh and doing a fresh install is not an option as I have a lot of non-free third party programs I use that are a pain to install.) Thanks!

---

### Post by Amarsingh0793 on 2008-09-03
Try uninstalling through Adept or Synaptic.

---

### Post by Malac on 2008-09-03
Most, if not all, of the kde4 programs have "kde4" somewhere in there dpkg name so open synaptic and search for kde4 then mark all in the list for removal including config files

Hope this helps.

---

### Post by Zorael on 2008-09-03
```
$ sudo aptitude purge ~nkde4
```
Removes all packages containing 'kde4'.

---

