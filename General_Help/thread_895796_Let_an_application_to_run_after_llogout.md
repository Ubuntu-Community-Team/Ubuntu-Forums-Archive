---
title: "Let an application to run after llogout"
date: 2008-08-20
forum: General Help
---

### Post by Spyros_Gre on 2008-08-20
Hello! I was wondering if there is a way to let an application run, even after I logout of my box. Assume that I am running VMWARE Workstation 6 and I need to logout. How can I let it run even after I logout? I think it might involve running Vmware or any other app as a daemon? Thank you!

---

### Post by amo-ej1 on 2008-08-20
Well that depends, there are various means for this, but it's not doable with graphical applications, since logging out would destroy your x-session and thus the contest they're running on.

One way to periodically start a command would be by using the cron deamon, this is used if you want a task to be run hourly, or every monday at 5 am.

Another option is when you simply want one application to stay active if you log out, or close your x-terminal. Then you can prefix the application with nohup. Try the following for example:

Open three x-terminals, on one type 'yes' (you will see lots of y's echoed to the termianl) and close the terminal, on another terminal type ps aux | grep yes and observe yes is no longer an active process.
On another terminal type 'nohup yes &' and close the terminal When you repeat the ps aux | grep yes you will see that 'yes' is still running and you will see output is being appended to nohup.out, kill yes by issuing killall yes. 

Another option could be to use 'screen', screen is a text based application which allows you to create sessions, detach those sessions and reattach them on a later time (in the old days these were often used to keep text-based irc connections active on shell servers).

hope this helps

---

### Post by amitkher on 2008-08-20
For graphical applications, you need to keep running an X server even after logout. I am describing a way to do this. But you may argue that this way you are not really logging out. You decide.

1. Install vncserver and vncviewer.

2. create directory ~/.vnc/
```

mkdir ~/.vnc

```

3. in file ~/.vnc/xstartup, write the following. Replace vmware by the command that runs vmware for you.
```

#!/bin/sh
vmware

```

4. Give it execute permissions
```

chmod +x ~/.vnc/xstartup

```

5. Start vnc server at screen number 10
```

vncserver :10

```
This might ask you for the password needed to connect to the vnc screen. This has already started your vmware. You will not be able to see the window.

6. Connect to this vnc screen number 10 as follows
```

vncviewer localhost:10

```
Enter the same password that you entered in step 5. You can control the vmware window from here.

---

### Post by Spyros_Gre on 2008-08-20
Thank you both! I think I will try to use the cron daemon. The vnc workaround works but is not the way for me. (actually I am experimenting with it !! ;-) ) 
Thank you!

---

