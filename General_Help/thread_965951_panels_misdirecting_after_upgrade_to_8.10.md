---
title: "panels misdirecting after upgrade to 8.10"
date: 2008-10-31
forum: General Help
---

### Post by serexia on 2008-10-31
Hi all

I just upgraded to 8.10 from 8.04, and all of a sudden the links in the Places menu of the top panel started misdirecting me (meaning, no matter if I click on Videos, Pictures, Music or whatever, it will always pop up the vlc player showing me the last video I played... )

I also uninstalled vlc, keeps opening totem. I think the links are simply pointing to the wrong location, but I have no idea of where to go looking for them...

Did anyone experienced something like this and found any solution? 

thanks
s

---

### Post by stoneage on 2008-10-31
Did you check the addresses? Open Nautilus File Manager and look in Bookmarks => Edit Bookmarks. If they point to vlc all you need to do is change them to point where they should go.

---

### Post by serexia on 2008-10-31
hi stoneage

in nautilus the bookmarks are set correctly. It must be somewhere else...

---

### Post by xhero0 on 2008-11-01
I had the same issue but in my case it brought up totem

i was helped in this thread: [http://ubuntuforums.org/showthread.php?t=963967](http://ubuntuforums.org/showthread.php?t=963967)

but what I did I RIGHT clicked on the folder and went to properties and under
OPEN WITH that is where I selected OPEN FOLDER....

Lates!

Joe M

---

### Post by Zeedok on 2008-11-01
I have also fixed this bug - we should check if it has been reported.

When trying to fix this myself I realised I could not edit the places menu (ie when I right clicked on the panel and selected edit menu).  All I could see was the Applications and System menus . . .

Is that normally the case?

---

### Post by serexia on 2008-11-01
thanks Joe

@zeedok
to edit the content of the place menu, you have to add or remove items as bookmark in the nautilus bookmarks menu, and the changes will occur also in the panel

---

### Post by xhero0 on 2008-11-01
oh wow!!!

cool! thanx for the tip! I will check it out now cos I was wondering that!

lates!

Joe M.

---

### Post by terry_gardener on 2008-11-02
i also had this fault, 

fixed it by previously stated by xhero0 right clicked my home folder and then clicked properties and then open with tab click open folder. 

this sorted all the subfolders properly also. 

big thanks this would have done my head in.

---

