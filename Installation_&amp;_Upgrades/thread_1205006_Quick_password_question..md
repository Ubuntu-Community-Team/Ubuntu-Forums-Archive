---
title: "Quick password question."
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by Vrekk on 2009-07-05
Hey im trying to change my Password for my account, but when i got to System -> Admin -> Users and Groups, my name isnt there :mad:, so can someone tell me how to change it from command line, I can figure it out.

---

### Post by mhgsys on 2009-07-05
If you already have the correct password
```


sudo passwd username

```
will do.


to recover or change password without having to use the old one, in case you forgot it...
bootup in recovery modes/

then
```


 cd /home/

```

```

ls -a

```
You'll find your username there.
then

```


passwd username

```
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully

reboot, log in with your username and passwd.

---

### Post by Vrekk on 2009-07-05
You guys never fail me, i know my (now old) password im just updating it, any idea on why im not in the Users and Groups GUI though?

---

### Post by Vrekk on 2009-07-05
Ok i got my login pass changed, but now when i login the Network Manager wants to unlock its keyring, which is still on my old password.  Where do i change that?

---

### Post by mhgsys on 2009-07-05
Have a look here;

[http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html](http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html)

**In case link go's down***
```

sudo apt-get install seahorse

```

Once installed open it, go to Edit -> Preferences menu. Select GNOME Keyring

---

### Post by Vrekk on 2009-07-05
Thanks problem sloved :D

---

### Post by mhgsys on 2009-07-06
nice~,

Your welcome.

---

### Post by Vrekk on 2009-07-06
Ok i lied my problem is not sloved (Didnt notice this one), when every i log in i have to manually mount my /Private directory and type in my old password. How can i change that?

---

### Post by mhgsys on 2009-07-06
To be honest; 

I don't know anything about encrypted Private Directory's.
However; 
After some research I found this;

To change your passphrase, use ecryptfs-wrap-passphrase
```


ecryptfs-wrap-passphrase ~/.ecryptfs/wrapped-passphrase

```


Hope this helps for you.

Also; 
Automount will fail when autologin is used.


Found it all on this wonderfull page from bodhi.zazen.
[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)


ps; I've never seen a sloved thread, only solved ones.;)

---

### Post by Vrekk on 2009-07-06
Wow that worked perfectly!  It automounts the way it should now.  Thanks for all the help.
Thanks problem solved (spelled it right this time)

---

### Post by mhgsys on 2009-07-06
you did!~


Nice to see it's working !

And again;

;) Your welcome.

---

