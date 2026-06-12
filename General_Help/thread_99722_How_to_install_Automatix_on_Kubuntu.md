---
title: "How to install Automatix on Kubuntu"
date: 2005-12-06
forum: General Help
---

### Post by parrusete on 2005-12-06
First off all i am spanish so i apologise for use of english ;) 
If you doesnt know what Automatix is i only can say hats is similir to easy ubuntu, whit it you can have your kubuntu full equip in only some steps.
Well the other day i achive to install Aotumatix in my kubuntu breezy y i needed to made some changes to the original ones, here comes my explication:
1- Download automatix
            [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)
2- Uncompress it where ever you want
3- install zenity -->   aptitude install zenity
4- execute in konsole -->   sudo xhost +localhost
5- navigate on the konsole to the new Automatix directory an execute the script 
     "sudo sh ./install"    is you are not allow to do that type "sudo chmod      +x ./install"
6- type in the konsole "kdesu kate /usr/bin/automatix"
7- Changes the last 3 lines , you have to changes 
     "gnome-terminal --commnad ="             
               by
     "kondole -e"
8- Save
9- And now you can execute by typing "automatix" on the konsole on clikink "Kmenu/System/Automatix"

I hope that is useful for you

---

### Post by Brando569 on 2005-12-07
automatix is no longer :( sad to see it go.....

---

