---
title: "Backing Up Data"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by shadowayex on 2009-11-09
After an upgrade that has left my system shakey and some important features unusable, I've decided to do a clean install.

It seems most of my data is in the home folder, but I have one quick question.

There are a lost of hidden folders that have (no doubt) been created by different programs. I don't know exactly what's in these, but I'm assuming settings of some kind.

My question is would it be safe to moves these as well? Or should I just leave them and start from scratch with those programs or what?

My main concern is actually my Firefox bookmarks. I'm sure anything else I can pretty much redo. So if I can't copy all those files, how would I get my bookmarks?

---

### Post by rygar on 2009-11-09
it should be safe to backup your entire home folder, including hidden folders.  as you pointed out, these folders are mostly for application settings and whatnot.  i don't think it will do any harm to your new installation.

to backup your firefox bookmarks, go to bookmarks -> organize bookmarks, import and backup -> backup, and save your bookmarks to a  .json file (you can also export to .html if you'd like).  save these files somewhere before you reformat.

---

### Post by presence1960 on 2009-11-09
> **rygar said:**
> it should be safe to backup your entire home folder, including hidden folders.  as you pointed out, these folders are mostly for application settings and whatnot.  i don't think it will do any harm to your new installation.

to backup your firefox bookmarks, go to bookmarks -> organize bookmarks, import and backup -> backup, and save your bookmarks to a  .json file (you can also export to .html if you'd like).  save these files somewhere before you reformat.

+1

Besides backing up home directory you could do this. Then after clean install you will be qable to have all your packages that are in the repositories reinstalled on the new OS with one command in terminal:

To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```


This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```


It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository.

---

### Post by phillw on 2009-11-09
> **rygar said:**
> it should be safe to backup your entire home folder, including hidden folders.  as you pointed out, these folders are mostly for application settings and whatnot.  i don't think it will do any harm to your new installation.

to backup your firefox bookmarks, go to bookmarks -> organize bookmarks, import and backup -> backup, and save your bookmarks to a  .json file (you can also export to .html if you'd like).  save these files somewhere before you reformat.

I'd also backup any saved passwords... that's an addon you can get for FF called Password Exporter, you can get hold of it over here -->> [https://addons.mozilla.org/en-US/firefox/addon/2848](https://addons.mozilla.org/en-US/firefox/addon/2848)

I love backups :D

There's a decent thread for a terminal command for doing backups, saving file permissions etc, over here -->>  [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

It's the basis of my backup script.

Regards,

Phill.

---

