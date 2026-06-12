---
title: "[SOLVED] ssh help"
date: 2008-10-07
forum: General Help
---

### Post by theevilhamster on 2008-10-07
I'm not too sure where to post this, so sorry if this is a bad place; it's my first post :).
I've been using linux for ages now and use terminal/console very often. This has been bugging me for a while; if i have have a command running (for example "wget http://www.google.com" (bad example, but still)) and then I log in through ssh, is there a way i can see how far the download is, or will I need to run the command through the ssh connection to begin with?

Thanks a lot!

---

### Post by christianvaldes on 2008-10-07
I take it your logging in remotely using ssh.
I think you would have to log in with a seprate ssh console
then find where you ran the wget in the ssh...find the directory that is
then I would just run a 
ls on the file that is being downloaded
let me know if this helps..

---

### Post by mbeach on 2008-10-07
you may want to look into the 'screen' command.

for a detailed explanation
man screen

for a friendlier explanation (but maybe not fully applicable)
[http://www.rackaid.com/resources/linux-tutorials/general-tutorials/using-screen/](http://www.rackaid.com/resources/linux-tutorials/general-tutorials/using-screen/)
see the 'screen tips' at the bottom.

---

### Post by jerome1232 on 2008-10-07
> **theevilhamster said:**
> I'm not too sure where to post this, so sorry if this is a bad place; it's my first post :).
I've been using linux for ages now and use terminal/console very often. This has been bugging me for a while; if i have have a command running (for example "wget http://www.google.com" (bad example, but still)) and then I log in through ssh, is there a way i can see how far the download is, or will I need to run the command through the ssh connection to begin with?

Thanks a lot!

If you are running the example command on the local computer and then sshing into another computer than you need to either open a new terminal window before sshing, or pop over to another tty (ctrl+alt+F1-6)

If you are running the example command on the remote computer and want to run multiple commands on the remote machine then you will need either open serveral ssh sessions (one for each task) or use screen, a great program! It will even keep programs running after the ssh session ends.

---

### Post by schauerlich on 2008-10-07
You could use screen. Add screen to the beginning of whatever command you're running, then ssh in and reattach the screen.

```
$ screen wget http://google.com
$ ssh user@host
$ screen -r

```

---

### Post by theevilhamster on 2008-10-08
thanks guys :) you made a geek very happy :) screen worked fine. Anything I can do If I forget to run screen?

---

