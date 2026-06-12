---
title: "Need root for cedega."
date: 2008-08-31
forum: General Help
---

### Post by parakeets11 on 2008-08-31
I have downloaded the free CVS version of Cedega and when I need to configure a profile it prompts
```

List of profiles (b to go back):

0 ) cvscedega_head
1 ) winex330
Enter choice:
0


Running Profile : cvscedega_head
Enter root Password: 
su: Authentication failure
daniel@daniel-laptop:~/Desktop$ 
```
For the root password I tried using my password but, of course, it didn't work.  I know that when you put ```
sudo -i
``` it gives you a root shell.  But how I figure out my root password?

---

### Post by Tim Sharitt on 2008-08-31
First, for your original problem, have you tried to run the configuration with sudo?
As for the root password, it is not set by default. A root password is not supposed to be necessary, but it is possible to set it. Enter the following in a terminal and type in the new password and confirm it when prompted.
```
sudo passwd
```

For more information on using sudo in Ubuntu see the [documention page.]("https://help.ubuntu.com/community/RootSudo")

---

### Post by parakeets11 on 2008-08-31
Hey, thanks. Yeah I have been wondering how to do that.  I hear about all the things that they say about it being not safe and all but I had to do it for this. Thanks again.

---

