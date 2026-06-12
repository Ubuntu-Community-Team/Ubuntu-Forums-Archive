---
title: "/etc/init.d doesn't run on startup"
date: 2008-11-22
forum: General Help
---

### Post by endeavormac on 2008-11-22
I have a script in /etc/init.d, /etc/init.d/hpasm to be specific, and everytime the machine comes on I have to
sudo /etc/init.d/hpasm start
Why is this, and how can I have /etc/init.d/hpasm start automated on boot? Isn't that the point of the init scripts?

---

### Post by gombadi on 2008-11-23
Quick and dirty way - In a terminal type 

```

who -r

```

It will give output like this -

```

         run-level 2  2008-11-23 14:02                   last=

```

Change to the /etc/rc2.d directory as I am using run-level 2

Make a sym-link to the init.d file. The filename needs to start with S and be followed by a number. Scripts are run in numerical order.

```

sudo ln -s ../init.d/hpasm S99hpasm

```

This will mean your script will be one of the last to be started in the bootup process. Change the number to suit.

Reboot your machine and the script should be run.

After you have it running you should have a look at the correct way of setting up init.d scripts.

```

man update-rc.d

```

---

### Post by endeavormac on 2008-11-23
Alright, thank you :)

---

