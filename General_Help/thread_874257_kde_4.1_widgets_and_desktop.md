---
title: "kde 4.1 widgets and desktop"
date: 2008-07-29
forum: General Help
---

### Post by aeleneski on 2008-07-29
Two questions after installing KDE 4.1:

1. I have Kubuntu 8.04 and have been using kde 3.5 until now, I originally tried KDE4 for a bit, but switched back. Now upon opening 4.1, I notice that my Desktop is not what is in my ~/Desktop directory. Why is this? And is there a way to get my Desktop to display these items. What is currently there is the items that were on my desktop at the time I initially tried kde 4. 

2. I am trying out some widgets. But I seem unable to add any. If I do Add Widgets -> Install New Widgets -> Download from the Internet. I get a popup with a bunch of different widgets to install. I choose to install one, and it seems to go successfully (it at least seems like it gets downloaded). But when I close that and go back to the Add Widgets dialog box I do not see the widget I just downloaded. I tried closing this, and re-opening the Add Widgets dialog but to no avail. I am doing something wrong?

Thanks.

---

### Post by kuja on 2008-07-29
Well, until KDE 4.2 (when it should be properly reimplemented from what I've read), I think what you're supposed to is add a Folder View widget to the desktop, you can have it display your ~/Desktop folder. That or you can add icons to the desktop by hand like you apparently had in 4.0. 

Edit: from what I've seen googling around, it looks like the problem is that the widgets it's trying to get from kde-look.org are not in a format that khotnewstuff2 can use. That would probably be the problem. [http://dot.kde.org/1216132899/1216232735/1216301550/](http://dot.kde.org/1216132899/1216232735/1216301550/)

---

### Post by aeleneski on 2008-07-30
Well that is unfortunate for both points. Another thing I have noticed is that I updated my bottom panel to have the clock, application launcher, system tray, etc. When I restart my computer and log back in, all I see is the clock centered on the screen. Anybody else see this before?

---

### Post by kuja on 2008-07-30
Get things set up the way you like, then run "kquitapp plasma && sleep 5 && plasma", that should prevent things from going whacky after logout.

---

### Post by kuja on 2008-07-30
.

---

### Post by aeleneski on 2008-07-30
Ah great that worked. Thanks! Now just curious, is this some sort of KDE bug or Kubuntu specific where this information is not saved? Also, any time I change the panel will I need to re-run that command set? Thanks again.

---

### Post by kuja on 2008-07-30
I've heard it might involve plasma crashing on exit or something, I'm not sure, but yeah, run this every time just to be safe.

---

