---
title: "[SOLVED] Need Help with HP Tx2000 and Hardy !"
date: 2008-11-11
forum: Hardware
---

### Post by Azyala on 2008-11-11
UPDATE:  After an update, the wacom stopped working and so did my nvidia graphics again.  This time, that xorg.txt I downloaded doesn't do anything to help either.  I'm confused...I don't want to have to keep using Vista...

I know there are several posts on this particular computer, but I haven't found anything that actually addresses the problem I'm having right now.

I am very new to ubuntu and thanks to all the helpful tutorials, I recently had everything except my tablet working on my machine.  However, when I was trying a tutorial to make wacom work I must have made a bad mistake and now my nvidia drivers won't work.  I have all the necessary downloads, I think, but when I try to enable the drivers, after I reboot, my computer starts in low graphics mode and it stays that way until I disable nvidia.  Can anyone help me? What do I need to do?

---

### Post by gali98 on 2008-11-12
Okay.. first of all, are you sure you have the tx2000? (check the model number on the bottom...) if you do, you can go to this post:
[http://ubuntuforums.org/showpost.php?p=5469447&postcount=5](http://ubuntuforums.org/showpost.php?p=5469447&postcount=5)
and download the xorg.conf at the bottom.
Then open up your own xorg.conf (at /etxc/X11/xorg.conf) and replace all the text with the one you downloaded. Save it then restart and everything should work. Only do this if you are for sure you have a tx2000 series!
If you have a tx2500 series, it will only make matters worse. Most importantly, before doing any of this, backup your xorg.conf!
Kory

---

### Post by Azyala on 2008-11-12
Thank you.  Yes I'm sure I have the tx2000. A few hours ago I was able to get my nvidia graphics working again after some fiddling, but I might still use that xorg.conf at the bottom if it will also get the wacom working.  

I do have a question though, how do I backup my xorg.conf?

---

### Post by gali98 on 2008-11-12
Basically the easiest way would be to just navigate to the folder /etc/X11 in the file manager and copy and paste it somewhere safe.
in the command line just do:
cp /etc/X11/xorg.conf ~/xorg.conf~

that copies it to your home folder as the file xorg.conf~...
If it messes up and you have to replace it back just run:
sudo cp /home/yourusername/xorg.conf~ /etc/X11/xorg.conf
and that will replace the new one with the backup.
As long as you have nvdia enabled and you have a tx2000, that xorg.conf should work perfect..
Kory

---

### Post by Azyala on 2008-11-13
Thank you so much, now everything works.  I am so excited!

---

### Post by gali98 on 2008-11-14
Glad its working!...
If you feel this thread is solved, could you mark it as so? Just go to thread tools then click "mark as solved"
Kory

---

