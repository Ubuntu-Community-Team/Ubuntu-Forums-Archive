---
title: "images issue with kde3.5"
date: 2005-11-30
forum: General Help
---

### Post by puelocesar on 2005-11-30
I'm having problems with kde 3.5. I was using Ubuntu 5.10 with gnome, and I decided to install kde 3.5

I installed kde with the repositorie posted here: [http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php)

Everything runs well, except the jpeg, gif and png images!

Konqueror dont preview these file types and kuickshow dont show them

It's really weird, because KImageview show these file types

Can anyone help me with this?

---

### Post by GoldBuggie on 2005-11-30
Is it perhaps that you are in system:/ in konqueror? Try using the normal path /home/$USER/ and see if preview works then. For me it does. system:/ isn't fully usable at the moment. Don't ask me why since nobpdy can explain it.

---

### Post by jamboarder on 2005-12-01
run kcontrol and under "KDE Components/File Manager"  on the "Previews and Metadata" tab make sure the "system" protocol is checked.  You should see previews again if you were having problems when konqueror is browsing the local filesystem as  "system:/home/...." or "system:/..." whatever.  Why the switch from the cross desktop/platform "file:/" protocol, I can't figure out.  Good thing is the tree view/navigation panel (if you use it) still uses the "file:/" protocol when you click on a folder.  A sharp eye might notice that the "file:/" protocol also respects the .directory file in each folder that contains folder specific information like backgrounds, etc. ("system:/" doesn't...)

(me thinks they were getting a little happy with these kioslaves)

---

### Post by puelocesar on 2005-12-01
thanks, but that Isn't my problem, the preview doesn't work even whith file://
(/home/paulo/Sem título-1.png)

In the desktop the image preview doesn't work too

This problem only  occurs with **jpg**, **gif** and **png**. 

With avi, mpeg, xcf, txt files the preview works

---

### Post by puelocesar on 2005-12-01
And I hated the system protocol, It's only work with kde apps!

---

### Post by Asraniel on 2005-12-01
ive got another bug with konqueror and images. it was also present in kde 3.4
if you look at many images on the web, i mean fullscreen, then after, i dont know 100 or so, you cant see then anymore, the normal embeded images in webpages still work, but if you want to watch one in full screen ([http://....jpg](http://....jpg)) it just doesent get displayd.

---

### Post by puelocesar on 2005-12-01
I think that's something related with the place of the libs libjpeg, libgif and libpng.

I read of some problems like this somewere, but it was with compilation of kde 2... and they dont have the solution

---

### Post by puelocesar on 2005-12-02
It appears that nobody knows how to fix it... I think I will remove my Ubuntu installation and install Kubuntu or Underground Linux, which one I'm downloading to test now, and it has Reiser4 support

thanks

---

### Post by xantHippe on 2006-01-05
This problem comes from Crossover. You need to delete mime-link installed by  this soft in ./kde/share/mimelnk/*.

---

