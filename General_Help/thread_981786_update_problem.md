---
title: "update problem"
date: 2008-11-14
forum: General Help
---

### Post by chrismitt2002 on 2008-11-14
the update info is outdated this maybe caused by network problems please update manualy by clicking on this icon and then selecting check but when i do i get this after it it attemts to update 


Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
(12:10:12 AM) solid-snake: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.



amy help would be great

---

### Post by volaer on 2008-11-14
did you try it by clicking Appliction>Add Remove Programs> WINE>

??? That's how I installed my wine and never had a problem.

---

### Post by chrismitt2002 on 2008-11-14
same error 

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

no clue what to do or how to fix this

---

### Post by Crafty Kisses on 2008-11-14
I'm not sure what version of Ubuntu you are using, but it appears these packages are for Ubuntu 6.10 Edgy. You can try cleaning and reconfiguring your package manager I guess, but I'm not sure how good that's going to do you if you're using something higher than Ubuntu 6.10, but here give it a shot:
```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
```
Once you have done that, it wouldn't hurt to update your repositories list either, just for the fact that whatever you're looking for, which appears to be Wine which can easily be installed through Synaptic, but if that's not what you're looking for, try updating your repositories:
```
deb http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse

deb http://security.ubuntu.com/ubuntu/ intrepid-security universe main multiverse restricted

deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe main multiverse restricted

deb http://packages.medibuntu.org/ intrepid free non-free
```
Run that command, after that has finished your repositories should be up to date and try again, if it's Wine your trying to install you can do that through Synaptic or through the terminal, here is how you would install it through the terminal:
```
sudo apt-get install wine
```
Try that and let's see if that gets you back up and running, please post back if you have any issues.

---

### Post by Lovejoy on 2008-11-14
You're suggesting using the intrepid repositories for edgy? That will cause problems. 

You should either  change your apt sources.lists to point to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)  or upgrade to a more recent version. Edgy's support was only for 18 months. It has now been over two years since it was released.  See this thread for more on this. [http://ubuntuforums.org/showthread.php?t=812714](http://ubuntuforums.org/showthread.php?t=812714)  

I'm in the same boat, I've just been putting off upgrading. It can be done one version at a time without breaking anything (maybe). Good guidance on upgrading is here; [https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)

---

