---
title: "Ubuntu Studio Usplash and Login Screen"
date: 2008-07-31
forum: General Help
---

### Post by KeybladeSephi on 2008-07-31
Hi, I was just wondering, how can I get the Ubuntu Studio usplash and login screen on Ubuntu? I have already installed Ubuntu Studio, but my usplash screen looks so plain. The screenshots of the usplash and login screens are in the attachments. Thanks

---

### Post by rainwalker on 2008-08-03
I'm pretty sure you just install everything UbuntuStudio-related in Synaptic, just search for "ubuntustudio"

---

### Post by Locutus_of_Borg on 2008-08-04
[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)

might help?

---

### Post by KeybladeSephi on 2008-08-05
Ah I did what the page told me to to, Locutus_of_Borg. It didn't work. It's the same USplash theme. It says Ubuntu Studio, but it's not anything like the pictures in my first post.

---

### Post by sayakb on 2008-08-05
Install the package **ubuntustudio-artwork **and [B]startupmanager
[/B]```
sudo apt-get install ubuntustudio-artwork startupmanager
```
Now goto System->Administration->Startup-manager, click on Appearance tab and select usplash theme.
Also, goto system->Administration->Login Window and change the gdm theme.

---

### Post by KeybladeSephi on 2008-08-07
I don't think the package exists in Hardy:

```
keybladesephi@Sheila:~$ sudo apt-get install ubuntustudio-artwork startupmanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntustudio-artwork is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ubuntustudio-look
E: Package ubuntustudio-artwork has no installation candidate
```

---

### Post by MatthewPlanchard on 2008-08-07
Also, StartUp-Manager seems to no longer have the option of configuring a USplash theme.  Is this just me?

See the attached screenshot.

---

### Post by Zopiac on 2008-08-07
how do you get that usplash? i installed an ubuntustudio usplash theme from the repos but it doesnt look like that :\

Edit: right, also the login, i didnt even look for that though

---

### Post by Zopiac on 2008-08-08
the ubuntustudio usplash theme in the repos does not have those particles, and is much more plain :/ i [found the login]("http://gnome-look.org/content/show.php/show.php?content=58047&vote=good&tan=63903985"), it was on gnome-look.org

still havent found the usplash, am looking for it currently!

---

