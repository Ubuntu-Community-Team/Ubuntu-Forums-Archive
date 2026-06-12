---
title: "Downloading Opera"
date: 2008-10-09
forum: General Help
---

### Post by Kyle FTW on 2008-10-09
My Firfox has been acting up lately and instead of updating to the newest version(not too keen on it), I want to upgrade to Opera. I've used it plenty of times before and am happy with it, but when I download it, what should I open the download with to run it like on Windows? I want to be able to download the browser so I can simply click it on my desktop to access it.

Thank you.

---

### Post by Bakon Jarser on 2008-10-09
Click on applications and go to add/remove programs and search for opera.

---

### Post by Kyle FTW on 2008-10-09
I can't seem to find it. I searched for it Opera in there but it doesn't show up.

---

### Post by ww711 on 2008-10-09
Load up a terminal - Navigate to Applications -> Accessories -> Terminal

use the terminal to move to the directory to where you saved the Opera .deb file, if you saved the file in your home directory, then feed this command:

***sudo dkpg -i opera_9.60.2444.gcc4.qt3_i386.deb***

(you can type the first couple of characters of the file name and use the tab key to auto complete the file name.)

---

### Post by OutOfReach on 2008-10-09
Download Opera from [http://www.opera.com/download/](http://www.opera.com/download/)

It should recognize your operating as Ubuntu, so click Download Opera and wait for the download to finish.

Now goto the location to where you saved the download, and double click the file and select Install on the dialog that comes up, or alternatively you can goto a terminal and goto the directory that you download in and do:
```
sudo dpkg -i opera_9.60.2444.gcc4.qt3_i386.deb
```

---

### Post by frankleeee on 2008-10-09
I don't remember if gdebi is included in the ditros I use, it has been a little while since I installed, but this is a easy way of installing deb packages, let the computer do the work if your lazy like me.

---

