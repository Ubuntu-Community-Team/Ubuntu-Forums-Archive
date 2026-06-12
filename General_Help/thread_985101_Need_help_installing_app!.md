---
title: "Need help installing app!"
date: 2008-11-17
forum: General Help
---

### Post by _Craig_ on 2008-11-17
I dowloaded "likewise" from their website, and copied it to the desktop.
I right clicked the filed and gave permissions to execute, when i try run it, it says I need to become a super user.

Please help,

Craig

---

### Post by silverglade00 on 2008-11-17
Open up Terminal and type cd Desktop. Then type sudo sh Likewise-the-rest-of-the-filename.sh and enjoy. It works VERY well.

---

### Post by _Craig_ on 2008-11-18
Im not so good at this.
Ok, to make it even easier i renamed the file to "1".

I typed "sudo sh 1.sh" and it says "cant open 1.sh"

Do I need to type the file extension too?

---

### Post by Yellow Pasque on 2008-11-18
If you just renamed the file to '1', then you would type:
```
sudo sh 1
```

---

### Post by easoukenka on 2008-11-18
drop to terminal and here is your copy and paste

cd ~/Desktop
mv 1 1.sh  (not sure if it needs the extension)
sudo chmod +x 1.sh
./1.sh

---

### Post by _Craig_ on 2008-11-18
Now it says "unable to resolve host 'my pc name'"!

LOL freakin LOL, all im trying to do is install a program and no success, 
imagine trying to write a app for Linux, there are some smart people in this world.

---

### Post by _Craig_ on 2008-11-18
Easoukenka, that didnt work. Thanks for trying man, i dont know anymore!

Maybe I should try loggin in as a super user, or change my profile to have root privilages?
How would I do that?

---

### Post by easoukenka on 2008-11-18
For some reason we have encountered a relatively serious problem I think you are going to want to fix or you will run into problems down the road and may be what is causing this problem.  Here is an article you should run through

[http://www.linuxabove.com/index.php?option=com_content&task=view&id=387&Itemid=1](http://www.linuxabove.com/index.php?option=com_content&task=view&id=387&Itemid=1)

When you are done you will only need to run ~/Desktop/1.sh  and possibly your origonal way of trying to install it may work.

---

### Post by _Craig_ on 2008-11-20
Thanks so much, will keep you posted.

---

