---
title: "skype for kubuntu"
date: 2008-11-25
forum: General Help
---

### Post by gaffajoiner on 2008-11-25
Hi, How do i get and install skype in kubuntu

---

### Post by aysiu on 2008-11-25
Unfortunately, Kubuntu doesn't have something like GDebi (something Ubuntu does have that allows you to double-click-install a .deb file).

So launch Konqueror.

Go to the Skype website.

Click the Ubuntu download.

Save it (by default Kubuntu saves to your /home/*username*/Documents folder).

Open a Konsole terminal.

Paste in the commands ```
cd ~/Documents
sudo dpkg -i skype*.deb
sudo apt-get -f install
```

---

### Post by PCessna on 2008-11-25
> **aysiu said:**
> Just go to the Skype website and download the Ubuntu .deb:
[http://psychocats.net/ubuntu/installingsoftware#gdebi](http://psychocats.net/ubuntu/installingsoftware#gdebi)

**Edit**: Oh, wait. Does Kubuntu have something like GDebi for double-click-installing .deb files?

Yes, KDE 4.1 does offer GDebi installer, I used it just 2-3 weeks ago. Installed a few Ubuntu packages.

Enjoy
-PCessna

---

### Post by aysiu on 2008-11-25
> **PCessna said:**
> Yes, KDE 4.1 does offer GDebi installer, I used it just 2-3 weeks ago. Installed a few Ubuntu packages.

Enjoy
-PCessna
Shoot. You're right. It doesn't appear in the menus, though. Okay... revised instructions.

**Step 1**
Go to the Skype download page and click on the Ubuntu download link.

**Step 2**
Instead of saving the file, choose to open it with an application. You have to type the application name ```
gdebi-kde
``` as it won't be in the menus.

**Step 3**
Wait for the .deb file to download and then click *Install package*

---

### Post by gaffajoiner on 2008-11-26
Thanks for the help, done as you say,now installed and loged  to Skype, can i ask you a question, went to set up my web cam but there is no web cam in the box please can you tell me how to make it show my web cam,

---

### Post by aysiu on 2008-11-26
> **gaffajoiner said:**
> Thanks for the help, done as you say,now installed and loged  to Skype, can i ask you a question, went to set up my web cam but there is no web cam in the box please can you tell me how to make it show my web cam,
It's possible your webcam isn't Linux-compatible.

You can check here:
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

---

### Post by gaffajoiner on 2008-11-26
been to the site i think it is compatible my web cam is logitech quickcam 5.3

---

### Post by PeonDevelopments on 2009-01-10
Check for /dev/video

Usually that's where the webcam is mounted.
Sorry I can't be more helpful.

---

