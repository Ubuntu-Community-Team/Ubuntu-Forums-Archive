---
title: "Keyring password - what is it ???"
date: 2008-11-04
forum: General Help
---

### Post by wpshooter on 2008-11-04
What is the keyring password that I keep getting prompted for in Evolution e-mail program under the Intrepid version of Ubuntu ?

This does not appear to be the same as the password for my e-mail account as established with my DSL service provider, because that password does not seem to satisfy this keyring prompt.  Is the keyring password just another prompting for my Ubuntu login password ?  And if so, why is this necessary ?

Thanks.

---

### Post by LowSky on 2008-11-04
keyring is some stupid program that wants to save all your password under one master password, very dumb I think

heres the work around if you cant get past it

go to /home file and hit Ctrl+h to show hidden files, delete keyring folder.

then go to mail, when the keyring prompt comes up just hit enter and it will not see it ever again

---

### Post by wpshooter on 2008-11-04
If that is what this is, then would you think that some type of explanation should be given when this pops up ???  Or at least some option be given for NOT using this and/or disabling it.  

HAVE ENOUGH PASSWORDS ALREADY, DON'T NEED ANYMORE.

Thanks.

---

### Post by LowSky on 2008-11-04
Oh Im completely with you, Keyring is for people who can't remember passwords, fortunately the only time it ever seems to come up is for Evolution and Wireless internet connection requiring passwords. Alot of people dont pay any attention and just enter their Sudo account password.

---

### Post by _sAm_ on 2008-11-04
I hate seahorse to, trying to use ssh, sshfs, press the calendar at top right and so on and seahorse pops up. All programs stops working, and the only thing that helps is pressing deny 3 to 4 times.

Edit
I went to ~/.gnome2/keyrings directory and deleted the default keyring file. Next time I tried to use ssh it asked me for a new password and I just leaved it blank. Now the crap is gone.

---

