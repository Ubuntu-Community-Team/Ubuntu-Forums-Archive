---
title: "Terminal won't launch a shell"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by awacs on 2009-04-26
After a Jaunty upgrade, terminal launches but errors:

"There was an error creating the child process for this terminal"

There's this in the logs (not the same time as the errors):

"Apr 20 22:54:38 laptop x-session-manager[5196]: WARNING: Could not launch application 'gnome-volume-manager.desktop': Unable to start application: Failed to execute child process "/usr/lib/gnome-volume-manager/gnome-volume-manager" (No such file or directory) "

and the folder /usr/lib/gnome-volume-manager does not exist.

I'm able to execute sh, /bin/sh, and bash from the console.

can anyone help me with my problems?

thanks.

---

### Post by dm6257 on 2009-04-26
I also experienced this problem. Also the tracker index problem that many have reported on.  And cannot run Synaptic package manager.  Get error -- failed to fork pty.

Should I submit a bug ticket?

Thanks,
DM6257

---

### Post by awacs on 2009-04-26
Ah! I have that prob, too - and solving it lets terminal work. You have to rename Sxxmountdevsubfs.sh. See:

[https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927](https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927)

---

### Post by ka1axy on 2009-04-27
I had this problem (both the terminal not creating a child process and the Synaptic pty error, as well as errors trying to automatically index my file system) after upgrading from Hardy->Intrepid->Jaunty.

From a a CTRL-ALT-F1 terminal session, I did this:

```
sudo cp /etc/init.d/mountdevsubfs.sh.dpkg-dist /etc/init.d/mountdevsubfs.sh

```

and rebooted.  Problem solved.  

The bug ([https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927](https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927)) mentions VirtualBox, which I do have installed (the non-free version).

Regards,
Peter

---

### Post by nspur on 2009-05-07
> **ka1axy said:**
> I had this problem (both the terminal not creating a child process and the Synaptic pty error, as well as errors trying to automatically index my file system) after upgrading from Hardy->Intrepid->Jaunty.

From a a CTRL-ALT-F1 terminal session, I did this:

```
sudo cp /etc/init.d/mountdevsubfs.sh.dpkg-dist /etc/init.d/mountdevsubfs.sh

```

and rebooted.  Problem solved.  

The bug ([https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927](https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927)) mentions VirtualBox, which I do have installed (the non-free version).

Regards,
Peter

Thank you very much for that solution. It was driving me mad.

regards

Nick

---

### Post by Undvargr on 2009-05-09
> **ka1axy said:**
> I had this problem (both the terminal not creating a child process and the Synaptic pty error, as well as errors trying to automatically index my file system) after upgrading from Hardy->Intrepid->Jaunty.

From a a CTRL-ALT-F1 terminal session, I did this:

```
sudo cp /etc/init.d/mountdevsubfs.sh.dpkg-dist /etc/init.d/mountdevsubfs.sh

```

and rebooted.  Problem solved.  

The bug ([https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927](https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927)) mentions VirtualBox, which I do have installed (the non-free version).

Regards,
Peter
I, too had this problem, which your solution fixed. Many thanks.

Patrick

---

