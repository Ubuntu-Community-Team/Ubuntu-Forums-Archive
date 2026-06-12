---
title: "How To : Install Kiba-Dock"
date: 2008-08-05
forum: General Help
---

### Post by mattgaunt on 2008-08-05
Hey everyone

I've loaded my how-to to a permanent link on my site so please visit [http://blog.gauntface.co.uk/?p=59](http://blog.gauntface.co.uk/?p=59) to view the how-to and post your problems here

Many Thanks

Gaunt

---

### Post by merlinLV on 2008-08-08
Although I'm not totally new to Linux, I'm new to Ubuntu and kiba-dock. One of the issue I had was that I was only able to launch it as root. The error I was gettting was "error reading config".

I was able to fix this by deleting a folder named "config" in /home/username/.kiba-dock and copying over the file "config" from /root/.kiba-dock to /home/username/.kiba-dock. Change the ownership of the file to the username and now I can launch kiba-dock as user.

Hope this help.

---

### Post by blendstylez on 2008-08-11
My first post, just to say >thank you< for this great "how-to"! :KS

it helped me a lot ;)
I'm kind of new to linux, and had a lot of problems running kiba-dock in Kubuntu with KDE4

now i have Gnome running, and kiba-dock finaly runs without sudo command..
but the physics don't :/
i get no error msges..any idea?

thx in advance

Peace blendstylez

---

### Post by mattgaunt on 2008-08-11
hi blendstylez, glad you liked the how-to and hope you enjoy linux, just keep at it and youu'll get the benefit. 

Good news is you didn't do anything wrong, you got the newest version of kiba-dock working.

Bad news, unfortunately the physics is no longer included in kiba-dock.

I'm unaware as to whether the kiba-dock developer(s) intend to re-introduce this or not.

How-ever if you look at my original post and read the replies there is someone who posted a way to get an older version of kiba-dock with physics, although I think there may be some problems that might of been corrected in the newer version.

Gaunt

---

### Post by blendstylez on 2008-08-12
:)
 hm...
i reinstalled the physics thang, than installed each folder again too...
after deleting the "config" folder in /home/user/.kiba-dock,finaly the dock started correctly with physics! :)

I installed the kiba-dock on a different system too, and also got no problems!
[kiba-dock version 9999]

Great how-to!Thanks a lot!

btw: 
- what means "Revision 602"?
- and what can i do against this,that opened programs come as white boxes into my dock, when i have physics enabled? my workaround is, disable & enable physics then the new icon is displayed correctly...seems like a refresh problem

*(Ubuntu 8.04 Hardy Heron - Gnome GUI)*
Peace blendstylez

---

### Post by mattgaunt on 2008-08-12
Im sorry I dont know what revision 602 means, if it is something that comes up during the program when run it might be something the developer(s) put in the program to remind him of a possible bug in the program.

Unfortunately I don't know what it means or how-to correct sorry.

Gaunt

---

### Post by blendstylez on 2008-08-12
np,
yey revision 602 comes, when trying to install physics..
don't mind, it works anyway :))

u know what i meant with the white boxes instead of the running-programm.icon? (just when physics are enabled)

thx anyway 4 four assistence buddy ;)

---

### Post by Crafty Kisses on 2008-08-12
> **mattgaunt said:**
> Hey everyone

My previous guide on installing kiba-dock was stored here so please ask any questions here regarding the installation of kiba-dock since my previous thread is now only read-only

[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

Note : If there is an administrator who can confirm it is ok to duplicate the previous threads instructions to this thread please let me know

Gaunt

I could just never get it to work this way, I'll post the errors next time I try, but dang, I wish Kiba-Dock worked natively with Hardy.

---

### Post by Grishka on 2008-08-12
for kiba-dock with physics enabled, you can try an old deb I've posted some time ago here: [http://ubuntuforums.org/showthread.php?t=820941&page=2](http://ubuntuforums.org/showthread.php?t=820941&page=2). it's pretty basic, mind you, no plugins, no stacks, no clock, just the dock and the bouncing icons, but it comes with a nice systray icon, working akamaru engine and nice configuration utility.

---

