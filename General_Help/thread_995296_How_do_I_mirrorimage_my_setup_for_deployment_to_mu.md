---
title: "How do I mirror/image my setup for deployment to multiple computers?"
date: 2008-11-27
forum: General Help
---

### Post by ibuclaw on 2008-11-27
Hi there,

I have finished configuring a dummy Ubuntu setup (8.04 with a mixture of OpenBox, LXPanel and PCManFS to give a lighter Gnome look).

Can anyone think of any suggestions towards imaging the setup I've made (configuration files and installed software) to be compressed/written to a CD/DVD, ready to be deployed to multiple machines with the exact same setup/settings?

Regards
Iain

---

### Post by meazz1 on 2008-11-27
Take look at the following site.
I am sure remastersys can do what you are looking for.

[http://www.remastersys.klikit-linux.com/]("http://www.remastersys.klikit-linux.com/")

---

### Post by ajgreeny on 2008-11-27
But surely, only if all the machines are exactly the same hardware; if not a lot of configuration will be wrong and you may not even be able to boot the system.

---

### Post by scouser73 on 2008-11-28
What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

---

### Post by Skripka on 2008-11-28
> **ajgreeny said:**
> But surely, only if all the machines are exactly the same hardware; if not a lot of configuration will be wrong and you may not even be able to boot the system.

That would be the fly in the ointment...and it is a big one.

---

### Post by Mip5 on 2010-02-24
Not sure if you're still looking for a solution to this, but we've found a Ghost Like system for imaging machines. It runs on Linux, and is a great application for cloning windows and linux boxes. It's called FOG, [http://www.fogproject.org/](http://www.fogproject.org/)

hth,

M

---

