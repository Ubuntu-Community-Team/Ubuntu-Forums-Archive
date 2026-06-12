---
title: "Autostart applications as root without root password dialog"
date: 2008-07-29
forum: General Help
---

### Post by gaiterin on 2008-07-29
Hi!

I am developing Gufw - [http://gufw.tuxfamily.org/](http://gufw.tuxfamily.org/)

I need run the application as root in the start of session.
If I create a file in ./config/autostart, when the system is starting a root password dialog appear. I don't like this dialog.

I was reading a solution: Modify /etc/sudoers, but I think is more dangerius.

Can be other possibility of run a root application in the start without password dialog?

Thanks a lot!!!
Marcos.

---

### Post by Dr Small on 2008-07-29
Could you please provide the full path to the autostart script?

---

### Post by gaiterin on 2008-07-29
I need run the program as:
gksudo --preserve-env "/usr/share/gufw/gufw.py --quiet"

I don't use a script. It's a python program :O
Maybe can be created a script...

---

### Post by gaiterin on 2008-07-29
And run for the user session :O (If he mark the autostart in Gufw) :O

---

### Post by caljohnsmith on 2008-07-29
Instead of modifying sudoers, if you set the "s" sticky bit on the program's permissions, then you can run that program as root without a password. But not all programs will allow you to run them as root that way. For instance, if that program is all ready owned by root, just do:
```
sudo chmod u+s /usr/share/gufw/gufw.py
```
See if that works, otherwise I would just add an entry for that program in sudoers as it is really not a big deal to do so. If you need details let me know.

---

### Post by gaiterin on 2008-07-30
Not works :(
Some other solution?
Thanks a lot!

---

### Post by justleen on 2008-07-30
try chmod a+x instead of u+s

---

### Post by gaiterin on 2008-07-30
Nothing :(
Thanks for the suggestion ;)

---

### Post by hyper_ch on 2008-07-30
what does that program do? Can you just simply add it, like a daemon, to the according run levels?

---

### Post by gaiterin on 2008-07-30
It's loaded as root for run ufw (know status, rules...) as root.

It's a executable python program, executable with gksudo /path/gufw.py

---

### Post by caljohnsmith on 2008-07-30
If you don't mind the program being run at startup, you can put it in /etc/rc.local and it will be run as root (no need to put gksudo in front of it). I'm really not sure what that program is, so I'm not sure if that strategy will work for you.

Or how about just modifying your /etc/sudoers? Try this:
```
export EDITOR=nano && sudo -E visudo
```
That will allow you to edit the sudoers file with nano, and then add the following line at the bottom of that file:
```
<username> ALL = NOPASSWD: /usr/share/gufw/gufw.py
```
That should allow <username> to run the program without a password.

---

### Post by Vadi on 2008-07-31
The above option isn't viable as this (auto-start) should be a preference in gufw, not done by the user manually.

---

### Post by loboc on 2008-07-31
> **Vadi said:**
> The above option isn't viable as this (auto-start) should be a preference in gufw, not done by the user manually.

If you make it a autostarted application using rc and a script in /etc/init.d it will show up in Ubuntu's Services preferences and the user can turn it off there, 

anyway I suggest reading this as a start

[http://www.linux.com/feature/46892](http://www.linux.com/feature/46892)

---

### Post by gaiterin on 2008-08-01
But then it will autostart for all users, isn't it?

---

### Post by nightfrost on 2008-08-10
I just found gufw, and it seems to be very neat little frontend to ufw. In fact, I had been thinking of coding something similar in python in order to learn python (I can't code, but would really like to learn when/if I find the time). The only thing I don't like about gufw is that it has to be run as root, which also gives you the problem you're asking help for in this thread. Have you considered these two possibilities:
1) Have a daemon run as root during startup, and the actual gui as a non-root application. The gui and the daemon could then communicate through dbus if, for example, the user who starts the gui is part a member of the 'firewall' group. This is similar to how NetworkManager and nm-applet work.

2) Use consolekit/policykit.

Keep up the good work! Like, I said, lovely little app!

Regards.

---

### Post by gaiterin on 2008-08-16
Hi!
Thanks for the idea.
It's the plan for the futures versions, but it's complicate for me...
I'm thinking in it ;)
Best regards

---

### Post by Drizzel on 2008-08-24
Bump. I am interested in getting gufw to autostart as well.. I added it to "sessions" with "gksudo --preserve-env /usr/share/gufw/gufw.py --quiet" as the command. It doesnt work. I would love to find a way to get it to autostart. I like gufw a lot. Hopefully an autostart option will be added to the next release.

---

### Post by gaiterin on 2008-08-24
Thanks!
Yes! Gufw will has an option for autostart in version 0.1.0 :) (next version), but will ask by root password :(
We're working about this point...
We're thinking the alternative is a dbus implementation... but it's complicate for me :(
Best regards.
Marcos Alvarez

---

### Post by Biku on 2009-01-20
Hy there ubuntu fans nice to meet you all :D.

I'm new in linux and i all so have a question.

I've install Firestarter 1.0.3 for Gnome i put it to the autostart applications and startup it said i dont have permission cu access.
OK i try modifying your answers according to my needs but no luck.

CAN ANY ONE HELP ME !!!!


the file i try to put in autostart is in /usr/sbin/firestarter.


i need this program because i'm getting hit after hit on my network :(

---

### Post by Biku on 2009-01-20
Never mind  i manage to do it .

here is the link whit more details about changing permission file/owner/group

 [http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)

  [http://www.linuxforums.org/security/file_permissions.html]("http://www.linuxforums.org/security/file_permissions.html")

---

