---
title: "Ubuntu won't log me in"
date: 2008-08-05
forum: General Help
---

### Post by Dpaulson on 2008-08-05
At the login screen, after I enter my username and password, nothing happens. I still can control my mouse cursor and control other functions like selecting language and restart/shutdown/etc. but it does not log in. I am inexperienced with ubuntu so i really have no idea what to do.

i can log in through terminal, but i get this response:

Last login: Wed Aug  6 14:39:53 PDT 2008 on console
Linux devon 2.6.24-19-386 #1 Fri Jul 11 22:45:14 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
2 failures since last login.
Last was Wed 06 Aug 2008 02:52:03 PM PDT on pts/0.
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
-bash: /dev/null: Permission denied
the above bash response repeats many times.

---

### Post by llama320 on 2008-08-05
i don't know what your problem is, but i can try to help troubleshoot it.

1) Did you test the liveCD for errors? there's an option to test it in the menu after you select your language

2) Does the liveCD run as expected when you put it in and select the "test out ubuntu without installing" (<< something like that)?

3) If you press Ctrl+Alt+F1, does it go to a virtual terminal with a prompt to login? If it does, try typing your user name and password in there, and see if it logs you in

---

### Post by Dpaulson on 2008-08-05
I have tested my live cd several times before and it works fine.

As for ctrl+alt+f1, all that does is take me to a terminal command listing. I left it alone for about 5 mins and still nothing happened.

---

### Post by Dpaulson on 2008-08-06
Any help? Ive been looking through other topics as well but nothing seems to work.

---

### Post by p_quarles on 2008-08-06
Try logging into that terminal (same username and password). Success or failure there might point to the problem.

---

### Post by fuzzyk.k on 2008-08-06
if that doesn't work try using the fail safe boot option and create a new user

---

### Post by Dpaulson on 2008-08-06
terminal works fine. although when it initially asks for my user and pass, immediatly after i enter them i get a long string of "permission denied" messages. everything after that works though. like i said, im really inexpierienced so even though terminal works i have no idea what to do. and ive tried fail safe boot, same thing. the login screen just doesnt do anything. i can still (as before) select language, boot, and shutdown options but it doesnt log in or do anything.

---

### Post by p_quarles on 2008-08-06
> **Dpaulson said:**
> terminal works fine. although when it initially asks for my user and pass, immediatly after i enter them i get a long string of "permission denied" messages. everything after that works though. like i said, im really inexpierienced so even though terminal works i have no idea what to do. and ive tried fail safe boot, same thing. the login screen just doesnt do anything. i can still (as before) select language, boot, and shutdown options but it doesnt log in or do anything.
Okay, let's see if this is an X server (the graphical display) configuration problem. Once you've logged into the terminal, run the following commands:
```
sudo /etc/init.d/gdm stop
echo "gnome-session" > .xinitrc
startx
```
The third command will attempt to start Gnome. Tell us what happens.

---

### Post by Dpaulson on 2008-08-06
"/etc/init.d/gdm is not a command"
should i try the other 2 commands anyway?

---

### Post by p_quarles on 2008-08-06
> **Dpaulson said:**
> "/etc/init.d/gdm is not a command"
should i try the other 2 commands anyway?
Um, seriously? That's weird. No, the others won't work yet as far as I can tell.

Can you post the results of this command?:
```
ls -l /etc/init.d
```

---

### Post by Dpaulson on 2008-08-06
that command gives me a long list of responses but the problem is i dont know how to scroll up so i can copy it down lol. its gonna take me a long time to copy down the whole thing. oh and i misspoke when i said that /etc/ was not a command, it actually said command not found so i assume i just dont have that package installed or something.

---

### Post by p_quarles on 2008-08-06
You can make the output into a text file:
```
ls -l /etc/init.d/ > init.d.txt
```
And then send that file (init.d.txt) to a different computer. 

In any case, "command not found" is definitely different. What does the following command say?:
```
apt-cache policy gdm
```

---

### Post by Dpaulson on 2008-08-06
no idea how to send it to another computer.

but heres the output of that other command:

gdm:
   Installed: 2.20.7-0ubuntu1.1
   Candidate: 2.20.7-0ubuntu1.1
   Version Table
 ***2.20.7-0ubuntu1.1 0
          500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-update/main Packages
          100 /var/lib/dpkg/status
    2.20.5-0ubuntu3 0
          500 http:archive.ubuntu.com hardy/main Packages

---

### Post by Dpaulson on 2008-08-06
i somehow managed to log in as root and everything works fine. im gonna check if my regular account works after i finish getting my files to another computer. i read on a lot of threads like this that the solution is never clear, but im not quite sure why what i did worked. i logged in as root in terminal and typed "startx" and the thing booted. weird.

---

### Post by Dpaulson on 2008-08-06
update: i tried logging in as a regular user, no luck. im beginning to think that it has something to do with the fact that i recently installed compiz, as other people with problems similar to mine did as well.

---

