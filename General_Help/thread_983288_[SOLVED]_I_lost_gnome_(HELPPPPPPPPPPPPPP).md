---
title: "[SOLVED] I lost gnome (HELPPPPPPPPPPPPPP)"
date: 2008-11-15
forum: General Help
---

### Post by Hyper Tails on 2008-11-15
Hi I run intrepid ibex and I have some broken pakages That I need fixed and I went into recovery mode and Now I't deleted gnome :cry:

I really need help with this

PS: I still got kubuntu and xubuntu

---

### Post by taurus on 2008-11-15
What happens if you reinstall it as

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by Hyper Tails on 2008-11-15
this is what i got
```
liam@liam-desktop:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done                           
Building dependency tree                                
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: fast-user-switch-applet but it is not going to be installed
                  Depends: gdebi but it is not going to be installed
                  Depends: gnome-app-install but it is not going to be installed
                  Depends: gnome-applets but it is not going to be installed
                  Depends: gnome-control-center but it is not going to be installed
                  Depends: gnome-panel but it is not going to be installed
                  Depends: gnome-session but it is not going to be installed
                  Depends: language-selector but it is not going to be installed
                  Depends: nautilus but it is not going to be installed
                  Depends: nautilus-cd-burner but it is not going to be installed
                  Depends: software-properties-gtk but it is not going to be installed
                  Depends: synaptic but it is not going to be installed
                  Depends: update-manager but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
                  Recommends: apport-gtk but it is not going to be installed
                  Recommends: jockey-gtk but it is not going to be installed
                  Recommends: nautilus-share but it is not going to be installed
                  Recommends: totem but it is not going to be installed
                  Recommends: ubufox but it is not going to be installed
E: Broken packages
liam@liam-desktop:~$

```

---

### Post by taurus on 2008-11-15
Try

```
sudo apt-get -f install
```

---

### Post by Hyper Tails on 2008-11-15
this is my results
```
liam@liam-desktop:~$ sudo apt-get -f install
[sudo] password for liam:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 mythbuntu-lirc-generator libsdl-ttf2.0-0 menu libntfs10
  libphysfs-1.0-0 jfsutils mythbuntu-common libalut0 xfsprogs expect ntfsprogs
  python-mysqldb vnc4-common neverball-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
liam@liam-desktop:~$
```

did i do it right?

---

### Post by taurus on 2008-11-15
Now just run

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by Hyper Tails on 2008-11-15
i'm still getting the same thing

---

### Post by Hyper Tails on 2008-11-15
I reinstalled ubuntu 

that worked

---

