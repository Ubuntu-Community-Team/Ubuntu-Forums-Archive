---
title: "Upgrade issue"
date: 2008-07-17
forum: General Help
---

### Post by fgtf on 2008-07-17
Hello everyone,this is my first post at the ubuntuforums :).Alright here is what I am having trouble with,so I updated Fiesty Fawn to Gusty Gibbon,and everything worked fine using 
```
sudo do-release-upgrade
```
Well its the same as upgrading with the graphical program so I dont think it really matters,anyways I decided to continue upgrading to Hardy Heron,so I did the same thing..and everything got downloaded but while the upgrade was proceeding it got stuck at some point
telling me:```
Generating Locales..
                    en_AU.UTF-8..
```
and this lasted for about 30 minutes so i thought something was wrong..so i rebooted the computer and then logged on to Ubuntu
to check if everything worked or not cause i was having my doubt..
i tried```
sudo lsb_release -a
```
and getting what i wanted Ubuntu 8.04 as a result..but something was broken..
so i did ```
sudo dpkg --configure -a
```
and i get the same thing as before```
generating locales..
                                             en_AU.UTF-8
```
So I don't really know what to do..and maybe this is normal and its supposed to take that long?but I doubt it.Thanks for any help you might offer.
----------------
**Sorry if I am posting in the wrong section.**

---

### Post by ctlr on 2008-07-17
I think you want [this thread]("http://ubuntuforums.org/showthread.php?t=861194"). A workaround appears to be posted pretty deep in the discussion.

Hope this helps.

---

