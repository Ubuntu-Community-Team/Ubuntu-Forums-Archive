---
title: "run commands durring boot"
date: 2008-11-26
forum: General Help
---

### Post by Darth_tater on 2008-11-26
I have just finished with the majority of work on my home server and now as a last step, I need to get several programs starting during boot.  The programs that must be started from within a GUI I have already taken care of&#8230; I am asking about how to launch programs during boot, before I get to a GUI / GDM launches.
One of the programs I need to get working is media tomb&#8230; I did find in the MediaTomb documentation how to set the media tomb daemon work but these directions will not work with ubuntu.  See here [http://mediatomb.cc/dokuwiki/faq:faq](http://mediatomb.cc/dokuwiki/faq:faq)
How can I get mediatomb to work&#8230; and how can I get other programs that do not have daemons to work?

edit:

oh, and for what ever reason, the mediatomb FAQ is incorrect... i have started my MediaTomb installation via the daemon method and it works flawlessly!

---

### Post by binbash on 2008-11-26
i am writing them to etc/rc.local but i dont know about daemons.

---

### Post by Darth_tater on 2008-11-26
not sure what you mean...

$ cd /etc/rc
rc0.d/ rc1.d/ rc2.d/ rc3.d/ rc4.d/ rc5.d/ rc6.d/ rcS.d/


so, which should i use for pre GUI, post network?

---

### Post by nzadLithium on 2008-11-26
i'm not sure exactly, but to find out you would have to look in the /etc folder for the file that defines runlevels, then you can find out what happens at each run level and determine where you want it started XD

---

### Post by sedawk on 2008-11-26
I'm not sure which is the default runlevel (Ubuntu has no /etc/inittab - that is what I'm used to find out about the default runlevel).
But let's assume its runlevel 5.
In runlevel 5 there is /etc/rc5.d/S99rc.local (which points to /etc/init.d/rc.local).
So one of the last things done when starting (in runlevel 5) is to execute
/etc/init.d/rc.local which will execute /etc/rc.local.

If you think that "S99" is too late you have to change something, e.g. change
"S99rc.local" to "S29rc.local" so rc.local is executed earlier.
(That solution might not be recommended. May be you can mimic the whole rc.local
 stuff with copies called "rc.local.early" to achieve the same).

---

### Post by reality1011 on 2008-11-26
Make sure you have the startup script in /etc/init.d

then use the following command:
sudo update-rc.d <script which is in /etc/init.d> defaults

---

### Post by lswb on 2008-11-26
I would advise against intalling anything in one of the /etc/rcx.d directories unless unless they are for basic system services or hardware initialization of some kind that must be done at a certain point in the boot sequence.

For most needs just put the commands in the file /etc/rc.local or create a separate script that is called from /etc/rc.local. Be sure to put your commands before the "exit" line in rc.local or they will not be run!

---

### Post by Darth_tater on 2008-11-26
> **lswb said:**
> I would advise against intalling anything in one of the /etc/rcx.d directories unless unless they are for basic system services or hardware initialization of some kind that must be done at a certain point in the boot sequence.

For most needs just put the commands in the file /etc/rc.local or create a separate script that is called from /etc/rc.local. Be sure to put your commands before the "exit" line in rc.local or they will not be run!


thankyou!  that's what i needed - a simple place for me to run a simple command so that my server programs can be started up w/o having to login!  thankyou!!!!


i just tested (needed to reboot anyways) and my funambol server was working and i didnt even have to login!  :KS

thanks!

---

