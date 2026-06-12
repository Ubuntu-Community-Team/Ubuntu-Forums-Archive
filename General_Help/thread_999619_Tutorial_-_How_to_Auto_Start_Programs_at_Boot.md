---
title: "Tutorial - How to Auto Start Programs at Boot ?"
date: 2008-12-02
forum: General Help
---

### Post by ismailkimyacioglu on 2008-12-02
Hello Linux Lovers,

In case we want some software start automatically at the boot, follow up the instructions below.

We first go to System/Preferences/Sessions.
This gives the list of the software of programs, that should be started automatically at the boot.

In the attached file (Screeshot-1.jpg), you will see the list of software in my computer.

Here is the part, that we should play with.  In my case, I wanted Gmail Notifier and Pidgin to start automatically at the boot.  So, I clicked Add button on the popped up window.  And, another window popped up as shown in the attached file; Screenshot-2.jpg.

In the name section, I just typed Pidgin Internet Messenger (as it is written in the GNOME menu).  But what about "COMMAND" ???

As you know, we can see the running applications in the background in Linux. (Please refer to attached file; Screenshot-3.jpg)

First, we go to System/Administration/System Monitor. Then, we click on "Processes" tab.  Here, we see the full list.  Search for the software or program name (Pidgin in my case).  As you find it, type what you see exactly to the Command line in "Add Startup Program" window.  I have also shown this in the attached file; Screenshot-4.jpg.

Then, click Add and Close.  You are done.  Now, Pidgin will start automatically at the boot.

Have fun with Linux :-)

---

### Post by Diabolis on 2008-12-02
This is too long for a tutorial. I had to read a bunch of stuff that is not needed for the accomplishment of the task.

---

### Post by albandy on 2008-12-02
type in the console the command whereis and the application name. For example:

**system$** whereis pidgin
**pidgin: /usr/bin/pidgin /usr/lib/pidgin /usr/share/man/man1/pidgin.1.gz**

then if you get a multiple response select the one wich includes the bin directory.

---

### Post by ismailkimyacioglu on 2008-12-02
Thanks a lot for the feedback.  I have just edited and tried to shorten the entire text.  Could you please check it again and let me know what you think ?

---

### Post by drs305 on 2008-12-02
The 'whereis' command is good for finding out where an app's files are stored, but for finding the run command a better command would be the 'which' command, which supplies the actual run command.
```
which gimp
```
/usr/bin/gimp

---

### Post by tattrat on 2008-12-02
Is there a way of starting apps like pidgin and skype which normally just reside in the task bar, so that they go straight to that state, I don't have to close the windows manually? (if you get what I mean)

---

### Post by ismailkimyacioglu on 2008-12-02
Can you please explain it in more detail ?

---

### Post by tattrat on 2008-12-02
> **ismailkimyacioglu said:**
> Can you please explain it in more detail ?

Ok, I tohught my question might not be easy to understand, so I'll give it another go.

So for instant messaging clients, and skype, after you start them, you don't actually need the window with the list of buddies to be present on the desktop, because the little icon in the bar at the top of the screen tells you everything you need to know. So for these apps, I want them to start, but I don't need the buddy/contact list to be or remain open. 

MSN messenger and skype start in this way on windows - straight to the tray.

Hope this makes sense!

---

### Post by drs305 on 2008-12-02
Here is a link to a thread that discusses the pidgin issue. You will probably want to start at post #6 and read through all the rest of the posts. There are several different suggestions, so read through them all and decide which one you want to try first:
[http://ubuntuforums.org/showthread.php?t=822795]("http://ubuntuforums.org/showthread.php?t=822795")

---

### Post by ismailkimyacioglu on 2008-12-02
Ok.  I got you now.  Well, I don't how, but mine starts in the system tray.  I will check in the properties and let you know if I find something.

---

### Post by theozzlives on 2008-12-02
> **tattrat said:**
> Is there a way of starting apps like pidgin and skype which normally just reside in the task bar, so that they go straight to that state, I don't have to close the windows manually? (if you get what I mean)

Pidgin starts in whatever state it was closed in

---

### Post by tattrat on 2008-12-02
> **theozzlives said:**
> Pidgin starts in whatever state it was closed in

It may do for you, or maybe it is supposed to, but it doesn't for me and (it now appears) for many others.

I really wouldn't ask the question unless there was a problem to be solved.

---

