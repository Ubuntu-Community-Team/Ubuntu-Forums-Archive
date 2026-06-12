---
title: "tutorial : how to remove amsn's blue boxes"
date: 2008-09-12
forum: General Help
---

### Post by x_error on 2008-09-12
hey every amsn user this is a common issue  a lot of people  suffered  from ,  if you are bothered from those blue boxes in amsn and you want to remove them and make your amsn's skins look cooler here is a very easy  tutorial to remove those  blue boxes and feel free with your amsn :
1.first thing you need to quit amsn
2.then write in the  terminal: cp /usr/share/amsn/skins/default/pixmaps/box_*.png $HOME/Desktop
3.the files are copied to your desktop so open each one with gimp or any other drawing program and erase them to make them transparent after you finish save the file.
4.open the terminal and write: sudo rm /usr/share/amsn/skins/default/pixmaps/box_*.png
5.finally write on the terminal again: sudo mv  $HOME/Desktop/box_*.png  /usr/share/amsn/skins/default/pixmaps 
6.open amsn and poof good bye to those blue boxes ! enjoy :)

---

