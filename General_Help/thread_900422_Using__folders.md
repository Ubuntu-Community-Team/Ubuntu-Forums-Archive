---
title: "Using / folders"
date: 2008-08-25
forum: General Help
---

### Post by DPMR on 2008-08-25
I am trying my hand at installing Seamonkey.
I open SeaMonkey launcher and found I could not create a folder in user/lib.
Permission denied.

I used the terminal to create a folder /user/lib/seamonkey.
Now when I try SeaMonkey installer I get permission denied to use folder /user/lib/seamonkey that I created.

The permission denied seams to tell me I have to use a terminal or something.

The installer I am trying to use is in /home/dpmr/Downloads/seamonkey-installer
The installer is seamonkey-installer-bin

---

### Post by WRDN on 2008-08-25
Why not just install it from Synaptic or Add/ Remove? That way, when it is updated in the repositories, the update for it will appear in the Update Manager. If you install manually, I don't think any updates will appear in the Update Manager.

---

### Post by Kevbert on 2008-08-25
Seamonkey is in the repositories.  You can install it via Synaptic Package Manager (just search for seamonkey).  Your problem is due to privileges not being allowed for directories other than /home.  To install to other directories you need to use Applications-Accessories-Terminal with the use of 'sudo'.  So to install via terminal you would use:
```
sudo apt-get install seamonkey
```

---

### Post by raphaelr on 2008-08-25
/us**e**r/lib? Are you sure? I think it is "/usr/lib".
So it would be "mkdir -p /usr/lib/seamonkey".

Then...```
cd /usr/lib/seamonkey
sudo chmod 777 .
```And it should work.

---

### Post by DPMR on 2008-08-25
Used Synaptic Package Manager.

It has an out of date version of SeaMonkey.

How do these packages get updated.


@raphaelr
My typo here, it was /usr.

---

