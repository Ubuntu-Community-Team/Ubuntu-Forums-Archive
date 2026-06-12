---
title: "How to Remove Encryption from Home Directory"
date: 2009-06-05
forum: Hardware
---

### Post by larry on 2009-06-05
Dear All,
I made a fresh install of Ubuntu 9.04 on my new laptop.
Only one question (for now ;-): during the installation, I chose to have my /home encrypted. It looks a safe choice...but what if at some point I should change my mind? Say for instance that I want to change my OS (i.e. another linux distro) and install something different than Ubuntu (I have /home on its own partition); will then new OS be able to mount /home ? In other words: is the choice I made irreversible?
Many thanks

larry77

---

### Post by petersohn on 2009-06-05
There is a way to recover the passphrase, so that you can leave the encryption if the distro you install supports ecryptfs. I don't know how it works exactly though.

E don't know what the most convenient way to remove the encryption, but I did the following: I booted in recovery mode with a root shell. Logged in with my username (so it mounted the encrypted directory), copied the files to a temporary location (for example to /tmp), and then logged out. cd into my home diretory (now unmounted, and deleted the contents of the encrypted directory (.Private). Then, in /home/username/.ecryptfs/Private.mnt I changed the line "/home/username" to "/home/username/Private". Finally, I moved the files from /tmp to the home directory. Now, only files you put in your ~/Private directory is encrypted.

---

### Post by larry on 2009-06-05
Mmmhhhh....so, in other words, could I simply (in case of necessity) backup my data to an external hard disk and then do the part I quote below

> **petersohn said:**
>  cd into my home diretory (now unmounted, and deleted the contents of the encrypted directory (.Private). Then, in /home/username/.ecryptfs/Private.mnt I changed the line "/home/username" to "/home/username/Private". Finally, I moved the files from /tmp to the home directory. Now, only files you put in your ~/Private directory is encrypted.

so that I can move the data back? Why is it necessary that \home is unmounted? Can I unmount it after a normal login?
Cheers

larry77

---

### Post by petersohn on 2009-06-05
You have to unmount because by default your home directory is mounted to /home/username, while the encrypted filesystem is in /home/username/.Private. In other words, you don't see your unencrypted home directory while the encrypted one is mounted.

But wait, you are right, I remember wrong. You simply have to change the line in the /home/username/.ecryptfs/Private.mnt file (while logged off -- home directory unmounted), and then log in. This way the original contents of your home directory will be mounted at /home/username/Private, so you just have to move them to /home/username.

And one more thing: you have to create the directory /home/username/Private in order to mount your files in that. If you do it as root, then don't forget to chown it to your user.

Probably you can do this whole thing without messing with the root login, but I didn't try it. I suppose if you change your settings in /home/username/.ecryptfs/Private.mnt, then you have to log out and in for it to take effect. However, if you do this, then you shouldn't use your graphical environment, because your settings will be messed up.

---

