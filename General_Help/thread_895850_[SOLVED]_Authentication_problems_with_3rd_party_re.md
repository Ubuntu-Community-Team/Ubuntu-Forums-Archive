---
title: "[SOLVED] Authentication problems with 3rd party repos"
date: 2008-08-20
forum: General Help
---

### Post by sexcopter on 2008-08-20
Hi,

I have recently tried to install a couple of pieces of software from 3rd party repositories, and cannot get them to authenticate when installing. This is on Ubuntu Hardy. I have added the GPG key in both cases, run apt-get update, and in one case the developer responded with an updated key, which still didn't help. It could be either coincidence that the keys are not good (but I don't know enough about how they work to know what could be wrong with them), or there's something wrong at my end.

I do know that the regular out-of-the-box Ubuntu repos work fine (main, multi, uni, backports etc)

The two pieces of software in question are qbittorrent, and liveusb. If someone would be kind enough to try installing these using the repositories and the keys, and tell me if they have the same trouble, I would be very grateful.

Instructions for qbittorrent: [http://qbittorrent.sourceforge.net/download.php](http://qbittorrent.sourceforge.net/download.php)
Instructions for liveusb: [https://launchpad.net/~probono/+archive](https://launchpad.net/~probono/+archive) (probono's key is found here: [https://launchpad.net/~probono](https://launchpad.net/~probono))

Of course, I could just ignore the authentication warnings, but I thought it was worth taking a moment to see if the problem lies at my end or with the developers and let them know if something's up.

If anyone has any other ideas, please let me know!

Thanks,
James.

---

### Post by Nepherte on 2008-08-20
From what I know of launchpad repositories, it doesn't support authentication. That is just the personal gpg key of the user, not the repository.

---

### Post by markbuntu on 2008-08-20
No authentication at launchpad. 

That is to give you a permanent friendly reminder that what you are doing is not supported and may possibly destabilize your system.

---

### Post by sexcopter on 2008-08-20
Ahh. I did not know this! That accounts for the launchpad one. Does anyone know about qbittorrent?

Thanks,
James.

---

### Post by todak on 2008-08-20
Per the qtbittorrent website here is the method to get the GPG key:

```
Packages are signed, please enter the following command to get my public key :
wget http://hydr0g3n.free.fr/qbittorrent/hardy/qbittorrent.gpg -O- | sudo apt-key add - 
``` enter the **wget** line in a terminal and it will automatically add the key.

---

### Post by sexcopter on 2008-08-20
> **todak said:**
> Per the qtbittorrent website here is the method to get the GPG key:

```
Packages are signed, please enter the following command to get my public key :
wget http://hydr0g3n.free.fr/qbittorrent/hardy/qbittorrent.gpg -O- | sudo apt-key add - 
``` enter the **wget** line in a terminal and it will automatically add the key.
I did this already. The key for Christophe Dumez appears under Software Sources, but I still get the "cannot be authenticated" warning. I was hoping someone else could try it to see if they also have no joy after following the instructions.

---

### Post by todak on 2008-08-20
After you install the key, you must restart your package manager or the terminal for the settings to take effect.

---

### Post by sexcopter on 2008-08-21
I have also done this.

---

### Post by sexcopter on 2008-08-26
I heard back from the developer of qBittorrent, and it turns out I wasn't the only one with authentication problems, and it has been resolved. So, after all that, there was nothing wrong at my end! Phew!

---

### Post by happy_pig on 2009-04-27
Qbittorrent- 
Seems this problem is back with Jaunty 9.04
Anyone else had any joy getting the authentication going as per the website?

---

