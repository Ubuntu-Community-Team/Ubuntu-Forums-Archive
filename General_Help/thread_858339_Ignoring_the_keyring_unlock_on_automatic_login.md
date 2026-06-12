---
title: "Ignoring the keyring unlock on automatic login"
date: 2008-07-13
forum: General Help
---

### Post by DizzyTech on 2008-07-13
For a faster boot, I've decided to set up an automatic login in GDM.  However, the Gnome keyring unlock prompts me on login.  Thanks for any help in advance.

EDIT:  Sorry I was being blunt; I was in a rush trying to get out of the house.  The Gnome keying screen, explicitly for the Network Manager startup, appears and prompts me for my password.  As you can probably guess, this defeats the purpose of an automatic login and takes too long for the wifi to get set up after logging in for the automatic login to be of any use.

Is there any way for the keyring unlock to be forgone?  I know it's a security thing, so I don't want to remove it.  I am also aware of the whole pam-keyring setup (how Ubuntu automatically unlocks the keyring through GDM's non-automatic login by default).

---

### Post by blazemore on 2008-12-27
Bump. Same problem!

---

### Post by orvils on 2009-03-30
Here is some info: [http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14](http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14)

In a nutshell: Looks like you have to set empty password for your keyring and then it is never locked. If you have set some password, change it to *empty pass*.

After 2 attempts worked for me in Jaunty beta. (see comments of the post)

---

### Post by Copernicus1234 on 2010-05-16
Just for other people who are trying to do this in later versions of Gnome... the "Password and Encryption Keys" program (seahorse) has changed so that there is no tab with "Password Keyrings" anymore.

What you do in Gnome 2.30 (in Lucid) is right click on the keyring you want to have no password in the main interface, and select "Change Password". Enter your user password where it asks for "previous password" and let the "new password" be blank.

This means that Gnome will now have no password for the keyring, so anyone with access to your computer will be able to see the passwords for every key in the keyring. But you will not be prompted every login for a password in return. If you are the only one using your computer, this is probably the behavior you want.

---

