---
title: "Removing Eclipse 3.3 from Ubuntu 8.4"
date: 2008-11-20
forum: General Help
---

### Post by Kingkarloz on 2008-11-20
Hello-

I'm pretty new w/ Ubuntu, and I recently installed Eclipse IDE to run Aptana to do some HTML/CSS/JavaScript/Ajax work, but it runs horribly slow and doesn't play well w/ Wine.  How do I uninstall this thing???  I can't find it in the "Add/Remove Programs" feature, and I'm a total newbie.  I installed it from a package at the Eclipse website.

Thanks in advance.

---

### Post by Nepherte on 2008-11-20
You run Eclipse in wine? Eclipse can be used with linux without wine as well. Anyways, programs installed with wine can be found in the directory /home/<user>/.wine/

---

### Post by Kingkarloz on 2008-11-30
Hey, thanks for getting back to me- no, I'm not using it w/ Wine, I followed the instructions from their site to install it natively to 8.04, but even after doing the Synaptic Package Manager uninstall, I think it's still in my computer.  I'd really like to get this thing off here and install Aptana instead, w/o having to wipe my Ubuntu and start over... (Which is sounding like what I'll have to do...)
Plz help!

---

### Post by Nepherte on 2008-11-30
Removing eclipse in synaptic does leave some files on your computer, but they are mainly the user's settings for that program (the folder in /home/username/.eclipse) and the archive file it downloaded, so you wouldn't have to download it again when you decide to install it again. So although there are some files left, you can consider it as removed when you also remove the .eclipse folder in your home.

This is only true when you installed eclipse through synaptic. I don't know what the installation instructions are on the eclipse site so I can't account for that.

---

