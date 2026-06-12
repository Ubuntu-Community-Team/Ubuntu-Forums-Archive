---
title: "DVD Problems in Hardy"
date: 2008-09-02
forum: General Help
---

### Post by gspawn69 on 2008-09-02
I've seen a few posts with similar issues to mine, but none of the solutions I've found have worked. DVDs played fine in Gutsy, but since I've upgraded to Hardy, first of all DVDs no longer start up automatically. When I load mplayer and tell it to play the disk, it skips the menu and goes right to the movie. In VLC, the menu displays, but when I click a menu option the program just hangs and nothing happens. Can someone give me any suggestions on how to get my DVDs playing properly again?

---

### Post by mc4man on 2008-09-02
> first of all DVDs no longer start up automatically
By default your only given 3 choices - open with totem, do nothing , ask. 

To ck. go to preferences -> file management -> media (disabled by default, enable in edit menus or browse there - home -> edit -> preferences -> media.

Another easy way to ck. setting or to change is to **hold down shift button** while inserting media, you should get a pop up, whatever you choose is made the new default. (handy when and if you add multiple choices for autorun of inserted media of any type.


> When I load mplayer and tell it to play the disk, it skips the menu


I don't use gmplayer much but a quick ck. of 10 titles shows no ability to open to or access menus. The one that it did (pbs title on Seabiscuit) the menu was a dead end, no way out.

> In VLC, the menu.....

Try setting vlc's launch command to vlc %m
Right click Applications -> edit menus -> expand sound & video -> on the right side, right click on vlc -> properties. In command box insert > vlc %m

To set vlc as default movie player see here

[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

For adding additional players as default choices some methods here (don't do what you don't understand

[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

