---
title: "[SOLVED] Ubuntu reboots computer on gnome-games"
date: 2008-08-10
forum: General Help
---

### Post by fkabir on 2008-08-10
Hello

Would someone kind enough walk me through the solution of the problem below?

When updating ubuntu 8.04 with the regular application/system through the update manager ubuntu gets stuck up on the gnome-games update and then automatically reboots the computer. I have tried uninstalling gnome-games through the package manager and it reboots  the computer too. I have tried installing a game and adept manager from add or remove programs and it still brings up the gnome-games and then reboots the computer.

Can someone please help me resolve this problem?

Thanks

---

### Post by Ryadt on 2008-08-10
Try updating in terminal
```
sudo apt-get update
``````
sudo apt-get upgrade
```

---

### Post by fkabir on 2008-08-10
Thanks for your reply, i just ran it and it returned the following:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a to correct the problem.

I ran the command it suggested with sudo and then i reran the command you suggested. 

I went back to the update manager and hit check and the same thing happened the computer rebooted.

---

### Post by Ryadt on 2008-08-10
Type in terminal```
sudo dpkg --configure -a
```

---

### Post by fkabir on 2008-08-10
i entered that command before and i did it again. but it doesnt make a difference. i still have the same problem.

btw thanks for continuously helping

---

### Post by Ryadt on 2008-08-10
Try ```
sudo apt-get f install
```
then```
sudo apt-get upgrade
```
Try it a few times to see if solves the prob...

---

### Post by fkabir on 2008-08-10
looks like it worked but all my games disappeared. is that suppose to happen?

Thanks for all your help.

---

### Post by fkabir on 2008-08-10
would you happen to know why my firefox runs very slow and even at times it uses 100% cpu usage.

I went through the threads and searched ways to make firefox faster it has been faster but its still slow.

Any ideas?

---

### Post by Ryadt on 2008-08-10
You probably uninstalled them. If they are the gnome-games, you will find them in the package manager.
Glad to help.;)

---

### Post by Ryadt on 2008-08-10
> **fkabir said:**
> would you happen to know why my firefox runs very slow and even at times it uses 100% cpu usage.

I went through the threads and searched ways to make firefox faster it has been faster but its still slow.

Any ideas?

Open a new thread. Post the output of[HTML]top[/HTML]
while firefox is running.

---

### Post by fkabir on 2008-08-10
i was using another computer for the ubuntu forum so i opened my firefox on my ubuntu computer hit post new thread and now what?

---

### Post by Ryadt on 2008-08-10
> **fkabir said:**
> i was using another computer for the ubuntu forum so i opened my firefox on my ubuntu computer hit post new thread and now what?

Type in terminal ```
top
``` and post the output in the new thread.

---

### Post by fkabir on 2008-08-10
i went ahead and started a new thread in the same general category

---

### Post by Ryadt on 2008-08-10
Thx..can you also please mark this thread as solved.:popcorn:

---

