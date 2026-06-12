---
title: "This is really annoyying!"
date: 2008-10-05
forum: General Help
---

### Post by IDK312 on 2008-10-05
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This is really annoyying! I cant type a command in the terminal because all i get is this popping up 'dpkg --configure -a'. I type that it says i need superuser previlege! When i am the only user?

---

### Post by MaxIBoy on 2008-10-05
In Linux, you're NEVER the only user. There will always be the "root" user, which you NEVER want to use as your main account.

Add "sudo" to the beginning of the command, then type in your password (you won't see any dots on the screen as you type it. That's normal; it's to prevent people from seeing how many letters your password is.)

---

### Post by Idefix82 on 2008-10-05
Please type in
```
sudo dpkg --configure -a
```

Explanation: when you type sudo you tell the terminal that you want to execute the command as super user. It will then ask you for your password. This is to make sure that a virus can't do any damage to your system. To change anything important it would need to "type in" your password, which a virus clearly can't know.

---

### Post by IDK312 on 2008-10-05
Ah i see!

Thanks for the help guys and girls!

---

### Post by taladan on 2008-10-05
To expand upon what the others have already stated here, a good rule of thumb to remember:

At the command line (or even in the GUI), if you're going to do something that is going to 'touch' the rest of the system or any part of the system above your home directory including installing software & reconfiguring packages/software/config files, you need to do it as 'root'.  Ubuntu saves potential security risks and headaches caused by inadvertently using a root command line interface by securing the system down to using 'sudo'.  

So if you're going to do something to the system that affects more that your user, use 'sudo' ;)

Got Root?

Tal

---

