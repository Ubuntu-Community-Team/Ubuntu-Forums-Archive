---
title: "[SOLVED] problems with update and termanal"
date: 2008-07-21
forum: General Help
---

### Post by gogadan on 2008-07-21
every time i try to update or add something into the terminal eg desktop effects i get this message

dan@dan-desktop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for dan: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
dan@dan-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
dan@dan-desktop:~$ 


what do i do please help !!

---

### Post by avtolle on 2008-07-21
From the command line (terminal)```
sudo dpkg --configure -a
```

---

### Post by drs305 on 2008-07-21
Run the following command:
```
sudo dpkg --configure -a
```

It will ask for your password. Type it but you won't see it being entered. Hit ENTER once you have typed it and the command will run.

---

### Post by gogadan on 2008-07-21
thank you that helped i have to renember that thank soooo mutch im defanateley glad i finally switched from windows :)

---

### Post by drs305 on 2008-07-21
gogadan,

It would be helpful when your problem is solved to go to the "Thread Tools" link at the upper right of the original post and mark the thread SOLVED.

Also, if you would like to thank avtolle for providing the answer to your question you would do so by clicking the gold star at the lower right of his post.

Welcome to ubuntu! :)

---

