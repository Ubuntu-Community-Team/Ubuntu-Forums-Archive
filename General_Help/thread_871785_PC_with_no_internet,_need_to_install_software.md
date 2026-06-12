---
title: "PC with no internet, need to install software"
date: 2008-07-27
forum: General Help
---

### Post by tom66 on 2008-07-27
I would like to install Xawtv on an old PC of mine which has no internet connection, preferably in the form of a .deb. How would I do this? 

Thanks.

---

### Post by northern lights on 2008-07-27
Check at [getdeb.net]("http://www.getdeb.net").

I was going to just now, seems to be down. Can sum1 confirm?

---

### Post by tom66 on 2008-07-27
Trouble loading too.

I tried a deb before, but it can't satisfy dependencies. In this case it hasn't got 'xawtv-plugins'.

---

### Post by mbarak on 2008-07-27
On your old PC go into Synaptic (System > Administration > Synaptic) click on everything you want to install (it will automatically select its dependencies).
Once that is done go to File > Generate Package Download Script
Save the file as anything you want

Go to a computer with internet access
If you go to another Unix computer (Ubuntu/Fedora/BSD/Mac OSX might even work) just run the script in a new folder - it will download all the .deb files needed for Ubuntu to install

If you are in a Windows environment, you will have to open the file and download manually all those .deb files listed in that file (not so fun/easy as in Ubuntu I know - it's why you switched in the first place right ;) )

anyways, once you have all those .deb files, you put them a folder, put them in a zip file (optional) then put them on your old pc (via network/floppy/usb/whatever you want)
Open Synaptic on your old PC again, go to File > Add downloaded packages
Browse to the folder where you're downloaded .debs are (make sure you're inside the folder - you won't be able to select any files)
Click Open
Click Apply
Watch + Enjoy as your programs are being installed

---

### Post by tom66 on 2008-07-27
Thanks, it worked. But I had to make a minor alteration.

Instead of using Synaptic on the PC without the internet connection, I used mine because it didn't know about the xawtv package. I then installed manually grabbing each dependency. Luckily I had a USB stick, or a lot of DVDs would have been sacrificed :O

Thanks, 
Tom

---

### Post by mbarak on 2008-07-27
If your PCs are in the same house, you should look into networking them - save you some trouble in the long run

---

### Post by dexter.deepak on 2008-07-27
you can make local-repository on a different ubuntu system(with internet connection) and use that on your system.
you may like to see the link in my sig. for making local repositories.

---

