---
title: "Remote X Server login"
date: 2008-07-13
forum: General Help
---

### Post by Ocxic on 2008-07-13
I have another computer i would like to be able to log into remotely. I would like to login and run an xserver session, in other words I want to login and control the computer remotely and have a seperate window. like VNC but i don't want to use VNC/remote desktop i'd rather use ssh or something else. i know i can ssh in and be able to run programs with ssh's -X flag but i want the whole desktop to be there. possible with xnest??

---

### Post by boblemur on 2008-07-13
first... get ssh
```

sudo apt-get install openssh-server
```

then 
```

ssh -X username@host
```

and then say:

gedit and look in open... and you will see that its actualy on the remote computer...

or you can forward the entire x11 session ( the exact thing you need to run im not sure but google it...)

i didnt need to change any of my configs to make it work either...

---

### Post by Yuki_Nagato on 2008-07-13
```
sudo apt-get install openssh-client
```

If you want a GUI client.

---

### Post by boblemur on 2008-07-13
but dont you need openssh-server in order to receive ssh connections??

or does -client do the same thing as server just with the gui...

---

### Post by Ocxic on 2008-07-13
i want to foward the entire x sessions i want a background picture, menus, the whole shebang

---

### Post by boblemur on 2008-07-13
[http://www.linux-tip.net/cms/content/view/302/26/](http://www.linux-tip.net/cms/content/view/302/26/)

read that...

i couldnt get it to work... but i dont really know what some of the things in the tutorial are...

---

