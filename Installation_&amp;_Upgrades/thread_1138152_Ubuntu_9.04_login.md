---
title: "Ubuntu 9.04 login"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by abes on 2009-04-26
After upgrading from 8.10 to 9.04 an account login appears on startup, although I never had the account login function setup in 8.10. I did have an account administrator password for allowing changes to the system. I have tried all variations of what I believed my account name would have been, as well as variations of passwords used, all to no avail.
How can I get into the system to remove this account, or change to another account name (which I would have to create) as the only option I have is to reboot etc or login.

---

### Post by talsemgeest on 2009-04-26
Try going into recovery mode, going to the root shell, and using the passwd utility. ```
passwd <username> <newpassword>
``` Also, I haven't used the passwd utility for a while so, I'm not 100% sure on whether that command will work. Give it a try and see what happens. Also, don't forget to replace <username> and <newpassword> with what you want them to be.

---

### Post by abes on 2009-04-26
The problem is that I have no idea what the username is, as well as the passwords. Have tried all variants of what I would have expected them to be but no success :confused:

---

### Post by talsemgeest on 2009-04-26
> **abes said:**
> The problem is that I have no idea what the username is, as well as the passwords. Have tried all variants of what I would have expected them to be but no success :confused:
In that case, you should probably create a new user and go from there. Take a look at [this.](http://www.cyberciti.biz/faq/howto-linux-add-user-use-adduser-command/)

---

### Post by abes on 2009-04-26
Please bear with me as I am new to all this.
I boot the machine which loads the menu for either 5 options of 9.04 ( 9.04 kernel 2.6.28-11-generic or recovery mode, and 9.04 kernel 2.6.27-11-generic or recovery mode, 9.04 memtest86+ and the other operating system (Windows7 beta). It also has the options for 'e' to edit the command line before booting and 'c' for a command line.
Pressing 'c' sends me to screen with _grub>_ however adduser or useradd result in Error 27 - unrecognized command.
Pressing TAB shows the possible commands however useradd or adduser are not one of them. There appears commands such as background, blocklist, boot ......................... uuid, vdeprobe, viewport.

Abes

---

### Post by hzrunner on 2009-04-26
As for your user name, that's the first name you used when you first installed ubuntu, for John Smith it would be john (no capital letters, if I'm not mistaken. It is also the name that shows up on the top right bar of the window (which, of course, only helps if you ever noticed it). I'm not sure how you can get to your password.

Good luck.

---

### Post by abes on 2009-04-27
Got it. Finally one of the combinations worked.
Thanks for the help

Abes

---

### Post by talsemgeest on 2009-04-27
> **abes said:**
> Please bear with me as I am new to all this.
I boot the machine which loads the menu for either 5 options of 9.04 ( 9.04 kernel 2.6.28-11-generic or recovery mode, and 9.04 kernel 2.6.27-11-generic or recovery mode, 9.04 memtest86+ and the other operating system (Windows7 beta). It also has the options for 'e' to edit the command line before booting and 'c' for a command line.
Pressing 'c' sends me to screen with _grub>_ however adduser or useradd result in Error 27 - unrecognized command.
Pressing TAB shows the possible commands however useradd or adduser are not one of them. There appears commands such as background, blocklist, boot ......................... uuid, vdeprobe, viewport.

Abes
You should go into recovery mode, then go to the root prompt. From there, run the commands outlined on that site.

---

### Post by talsemgeest on 2009-04-27
> **abes said:**
> Got it. Finally one of the combinations worked.
Thanks for the help

Abes
Ah, just missed your post. Glad you got it working. :)

---

