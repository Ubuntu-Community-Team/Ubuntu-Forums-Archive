---
title: "[SOLVED] samba passwords"
date: 2008-08-21
forum: General Help
---

### Post by wolfen69 on 2008-08-21
OK. after 18 hours of fiddling with trying to get my desktop and laptop networked, they finally see each other no problem. i can see the shared folders from both machines. but it asks for a password from either machine when i try to access the folders. i have not set a password. i would prefer to set it to run without password, but i'll take anything at this point. :sad: can someone tell me the proper way to set a password on both machines? thanks for any help, i'm ready to give this up. (networking) it seems like the impossible dream.

---

### Post by WRDN on 2008-08-21
> **wolfen69 said:**
> OK. after 18 hours of fiddling with trying to get my desktop and laptop networked, they finally see each other no problem. i can see the shared folders from both machines. but it asks for a password from either machine when i try to access the folders. i have not set a password. i would prefer to set it to run without password, but i'll take anything at this point. :sad: can someone tell me the proper way to set a password on both machines? thanks for any help, i'm ready to give this up. (networking) it seems like the impossible dream.

The password used should be the password used on the host machine. For example, if I shared the /home/John/test_share folder, I would login on samba with the username John and the password that corresponds to that account.

You may find the information [here]("https://help.ubuntu.com/community/SettingUpSamba") useful. Note that, when you access the samba share on the Ubuntu share (through Places > Connect to Server > Windows Share), you can select "Always remember" after entering the password, so you do not have to enter the password multiple times.

---

### Post by wolfen69 on 2008-08-21
thanks for the reply. i can now access the laptop shared folders (from the desktop) with the hosts password. but when trying to access the desktop's shared folders, (from the laptop) i enter the password and the password prompt keeps coming back and wont let me in. why?

i have gotten this far before, but can never get to access the desktop's folders. nothing works as far as password.

---

### Post by WRDN on 2008-08-21
When accessing the shared folders, I usually enter the following information:

- IP Address
- Share
- Username

. . . then the password at the prompt. The only reason the password prompt would come back is if you entered the password incorrectly. Try changing the password on the Desktop, and try connecting again. You could also try adding the user to the "samba" group in Users and Groups (under System > Administration), and you may want to restart the samba service using the command:

```
sudo /etc/init.d/samba restart
```

. . . in the Terminal.

---

### Post by Nepherte on 2008-08-21
You could set the permission in smb.conf to user:
```
security = user
```

Afterwards you simply add users from your system to samba and enable them:
```
sudo smbpasswd -a <username>
sudo smbpasswd -e <username>
```

Those users can then access your shares with the given password (this does not have to be the password required to login). I just create new users, without any rights to login to my system:
```
sudo useradd -s /bin/false username
```
and use them for samba.

Don't forget to restart samba:
```
sudo /etc/init.d/samba restart
```

---

### Post by wolfen69 on 2008-08-21
i finally got it! many thanks to everyone. you're the best.

---

