---
title: "Hangs at startup."
date: 2008-11-04
forum: General Help
---

### Post by CalvinMorrison on 2008-11-04
hi,

After i updated to intrepid, and restarted my machine, it won't startup. It loads all the way up and then goes to some text saying 

*checking battery state [ok]
* running local boot scripts (/etc/rc.local/) [ok]
and then it  stops there.

I can get into it in recovery mode and it loads fine into the command line,

any help? no idea how to fix it.

Calvin

---

### Post by CalvinMorrison on 2008-11-04
bump

---

### Post by jimmy-james on 2009-02-07
I have the same issue.
I am trying to install Nvidia drivers and in order to do so, need to stop the GUI.
After typing sudo /etc/init.d/gdm stop in a terminal, the screen goes black and I see several lines including battery check and the last one says the same as above ... *running local boot scripts...OK thewre is a flashing cursor under that.
No login, nothing. I can type stuff in but nothing happens.
The only way out of that is CTL-ALT-DEL to restart the system

Also, no CTL-ALT-F(X) do anything whether in or out of the GUI.
I am running a newly installed 8.04 HH

Actually, I was able to get to a terminal in recovery mode start up. Now I have to figure out what run level 1 vs. 3 means

Ok, last edit, I swear.
I got it to bypass the *running local boot scripts hang up.
In the main X-server login screen, login to a terminal under options there. In THAT terminal, run sudo /etc/init.d/gdm stop
For me, it put me into the shell login as it was supposed to.
I am sorry that this does not probably solve the OP's problem but at least it is a bump in the thread.

---

