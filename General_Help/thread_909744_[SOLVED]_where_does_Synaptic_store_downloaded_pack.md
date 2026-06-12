---
title: "[SOLVED] where does Synaptic store downloaded packages"
date: 2008-09-03
forum: General Help
---

### Post by charonred on 2008-09-03
When I add other apps via Synaptic from the various repositories, where does Synaptic store these packages before installing them?

I was thinking I could burn them to disc and use as another repository for Ubuntu installs on my other PCs instead of downloading them again.

---

### Post by lucho64 on 2008-09-03
> **charonred said:**
> When I add other apps via Synaptic from the various repositories, where does Synaptic store these packages before installing them?

I was thinking I could burn them to disc and use as another repository for Ubuntu installs on my other PCs instead of downloading them again.

/var/cache/apt/archives

---

### Post by charonred on 2008-09-03
thanks for that, will see if it works as intended later today.

---

### Post by drs305 on 2008-09-03
> **charonred said:**
> 
I was thinking I could burn them to disc and use as another repository for Ubuntu installs on my other PCs instead of downloading them again.

There is a utility called APTonCD for backing up the archives. Here's the link:
[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

You can also save a *[COLOR="Blue"]list[/COLOR]* of apps so your new computer has the same packages on it as the first one. Note it's only the list, all the packages will need to be downloaded:

Run on old computer, creating a file on the desktop called 'packages':
```
sudo dpkg --get-selections >~/Desktop/packages
```

Copy the file 'packages' to $HOME/Desktop on new computer, then run: 
```

sudo apt-get update
sudo dpkg --clear-selections
sudo dpkg --set-selections <~/Desktop/packages 	
sudo apt-get dselect-upgrade
```

---

### Post by charonred on 2008-09-04
Thanks drs305,
downloaded, installed and run aptoncd, then burnt a CD - excellent idea

---

