---
title: "flash plugin"
date: 2008-09-13
forum: General Help
---

### Post by heiNey on 2008-09-13
im having a problem with my flash plugin.  whenever i try to visit a site like youtube, i cant see any video.  the weird thing is ive tried to do a ```
 sudo apt-get remove flashplugin-nonfree 
``` and then immediately do a ```
 sudo apt-get install flashplugin-nonfree 
``` and it starts working again.  i can watch a few videos, but if i close firefox and open up youtube again, it doesnt work anymore.

all of this started happening after i tried to install the latest flash plugin beta from adobe to fix the firefox crashing when watching flash videos  problem.  it didnt work and i uninstalled the beta, but now im having this problem.  anyone know whats going on?

---

### Post by mb_webguy on 2008-09-13
Have you tried installing Flash 10 from the backports repository?  Check the link in my signature.

---

### Post by heiNey on 2008-09-13
im still running gutsy.  your sig says for hardy.  is that a problem?

---

### Post by mb_webguy on 2008-09-13
Hrmm...  Good question.  You can give it a try and see if it works.  If not, you can always just uninstall it.

I just checked, and Flash 10 hasn't been backported to Gutsy, but you can get the deb from [this page]("http://packages.ubuntu.com/hardy-backports/web/flashplugin-nonfree").  It *should* still work with Gutsy.

---

### Post by heiNey on 2008-09-13
ok..tried that...we'll see if this fixes it.  thanks.

---

### Post by heiNey on 2008-09-13
nope...still doesnt work.

---

### Post by frankleeee on 2008-09-13
Have you installed any of the restricted extras in add remove. I am running Gutsy and installed the deb link via gdebi and it seems to work fine for me.

---

### Post by mb_webguy on 2008-09-13
Hrm... You said that it started after you tried installing Flash beta from the Adobe website?  It could be that it wasn't removed cleanly.

Uninstall flashplugin-nonfree using "sudo apt-get remove --purge flashplugin-nonfree".  Now try "sudo find /usr/lib -name *flash*" and "sudo find /home -name *flash*" and see what shows up.  If you see anything that looks like it belongs to the Flash plugin -- particularly anything in /usr/lib/flashplugin-nonfree, /usr/lib/mozilla/plugins, /home/<user>/.macromedia, or /home/<user>/.mozilla -- then delete it.

Then try reinstalling the Flash 10 deb package.

---

### Post by heiNey on 2008-09-13
ok, just did all of that.

ill try to play some vids and see if it happens again.

EDIT: hmmm, it says "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player." after installing that deb.  i no longer have a /home/user/.macromedia/Flash_Player folder, since i deleted it and it wasnt reinstalled when i installed the deb.  should it be there?

---

