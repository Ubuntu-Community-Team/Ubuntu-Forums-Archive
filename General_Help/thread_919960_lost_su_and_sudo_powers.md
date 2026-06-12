---
title: "lost su and sudo powers"
date: 2008-09-14
forum: General Help
---

### Post by rmvg on 2008-09-14
Apon reboot i have seemed to have lost my su or sudo powers 

In the beginning i did this sudo passwd root and everything was great i could sudo or su. I did a reboot and now everytime i try to run anything as sudo i get this

$ sudo ifconfig
bash: /usr/bin/sudo: cannot execute binary file

or 

$ su
Password: 
su: Module is unknown

here is the stuff from my auth.log

Sep 14 17:55:56 bao su[6783]: PAM (su) empty module type
Sep 14 17:55:56 bao su[6783]: PAM (su) no control flag supplied
Sep 14 17:55:56 bao su[6783]: PAM (su) no module name supplied
Sep 14 17:55:56 bao su[6783]: PAM unable to dlopen(<*unknown module path*>)
Sep 14 17:55:56 bao su[6783]: PAM [error: <*unknown module path*>: cannot open shared object file: No such file or directory]
Sep 14 17:55:56 bao su[6783]: PAM adding faulty module: <*unknown module path*>
Sep 14 17:55:56 bao su[6783]: PAM (other) empty module type
Sep 14 17:55:56 bao su[6783]: PAM (other) no control flag supplied
Sep 14 17:55:56 bao su[6783]: PAM (other) no module name supplied
Sep 14 17:56:04 bao su[6783]: pam_authenticate: Module is unknown
Sep 14 17:56:04 bao su[6783]: FAILED su for root by c0mputerking
Sep 14 17:56:04 bao su[6783]: - pts/1 c0mputerking:root

I have checked and the sudo file seems to be there

:/usr/bin$ ls -l sudo
-rwsr-xr-x 2 root root 107872 2008-09-10 12:05 sudo


PLEASE HELP 

As a hint these are some things that i did before the reboot. could either of these caused me this problem?? oh and added some ram

chmod 4755 /usr/bin/zmfix

and this 

gksudo 'python /usr/share/EasyCam2/core.py --gtk'

---

### Post by Pro-reason on 2008-09-14
You added new hardware?  Remove it and see if the system works properly.

You might also want to try doing the “memtest” at start-up.

Remember to pull the plug (or turn off at the power supply if it has a switch) when adding or removing hardware.  Don't just shutdown.

You might also want to check your /etc/hosts file, as errors in it can cause sudo problems.

---

### Post by oliver69 on 2010-11-21
Although this thread is old, perhaps this helps other googlers. Here is what worked for me after seeing the error above. Execute in a Terminal:
  $ sudo passwd
(without the "$" of course - it's part of the prompt)

---

### Post by Joeb454 on 2010-11-21
Aside from thread necromancy, the OP hasn't visited the site in over a year. Thread Closed.

---

