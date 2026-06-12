---
title: "HOW TO install all emerald themes"
date: 2008-10-29
forum: General Help
---

### Post by realn on 2008-10-29
I don't know why, on my HH Kubuntu, emerald-themes package is missing. So here is what I did. I supposed it can be packed in a script - the only manual thing I had to do is to temporarl;y accept the signature from the SVN repository:

1) cd ~; mkdir temp; cd temp
2) svn co  [https://svn.generation.no/emerald-themes](https://svn.generation.no/emerald-themes) 
3) cd emerald-themes; rm -Rf .svn; mv visa_\(smoked_aero_glass\).emerald visa_smoked_aero_glass.emerald; rename 's/\.emerald$//' *.emerald; cd -
5) mkdir emerald-themes-temp
6) ls emerald-themes | awk '{print "mkdir ./emerald-themes-temp/"$0";cp ./emerald-themes/"$0" ./emerald-themes-temp/"$0";cd ./emerald-themes-temp/"$0";tar xvfz "$0";rm -f "$0";cd -"}' > temp.sh
7) chmod 755 temp.sh; ./temp.sh
8) cp -R emerald-themes-temp/* ~/.emerald/themes 
9) i'll let you delete the no longer needed ~/temp folder

Enjoy and by the way, the compiz fusion icon thing is super cool.
by

---

### Post by realn on 2008-10-31
If anyone knows about a simpler way to do it, please let me know.
Thanks!

---

### Post by thebitguru on 2008-11-13
I don't know if there is an easier way, but thanks a lot for writing the commands!  It was a breeze :)

---

### Post by loomsen on 2008-11-13
Maybe you want to take a look at this:

[Using Synaptic to install latest git-version. Emerald themes included as well](http://ubuntuforums.org/showthread.php?t=971379)

(Actually the emerald themes package hasn't changes for one year or so)

---

### Post by eternalnewbee on 2008-11-13
You could also download a theme you come across that you like, and save it to a folder in your home directory (for example **Emerald Themes**).
Then open Emerald and click on **Import** & navigate to the folder and open the theme. Doesn't always work, but usually.

---

### Post by binbash on 2008-11-13
There are around 20 themes there and it is not updated.Better to go gnome-look.org and install via hand.You can also browse the svn via firefox and download all .emerald files and import them via emerald manager

---

