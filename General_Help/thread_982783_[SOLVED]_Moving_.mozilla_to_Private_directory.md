---
title: "[SOLVED] Moving .mozilla to Private directory"
date: 2008-11-15
forum: General Help
---

### Post by IanB2 on 2008-11-15
I hope you can help. I have configured the EncryptedPrivateDirectory as per instructions for 8.10 and the Private directory seems to be working just fine.

I've been following the instructions (below) and trying to move .mozilla to the private directory. 
Symlink is in place and everything looks OK however every time I launch firefox, the files in the private directory are ignored and firefox creates new directories in the ~/.mozilla location rather than using ~/Private/.mozilla

It will be something simple but I can't figure it out.

---------------------------------------------------------------
Storing Your Keys, Email and other Data in ~/Private

It can be a good idea to move the content of your .evolution/, .ssh/ and .gpg/ in ~/Private and replacing them with a symlink.

   1. Make sure that the application whose data you want to protect (e.g. Firefox or Evolution) is not running

       ps -ef | grep evolution 
   2. Move the application's data directory (e.g. ~/.mozilla or ~/.evolution) into your ~/Private directory

       mv ~/.evolution ~/Private 
   3. Establish a symbolic link from the old location to new location

       ln -s ~/Private/.evolution ~/.evolution

---

### Post by IanB2 on 2008-12-28
I've tried this again on another installation and all seems to be working correctly.
All I can assume was that the application was still running in the background (or something like that)

---

