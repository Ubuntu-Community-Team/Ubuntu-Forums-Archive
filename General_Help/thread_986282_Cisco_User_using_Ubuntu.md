---
title: "Cisco User using Ubuntu"
date: 2008-11-18
forum: General Help
---

### Post by dtester on 2008-11-18
I am new to Ubuntu but I now have my laptop setup and ready to go with Ubuntu 8.10.  I realy to love this OS and it is easier that I thought.  My question is this.  I use tera term pro to console into tons of Cisco equipment.  Does any one know if tera term will work with Ubuntu?  if not is there any suggestions on what I could use?

Thanks for the help
David Tester:)

---

### Post by cariboo on 2008-11-18
Ubuntu comes with gnome terminal by default you should be able to do most of what you did with Tera Term Pro. You may want to give **aterm** a try.

Go to System-->Administration-->Synaptic Package Manager, click the search button and type terminal. This will show you a listing of terminals available, including aterm.

Jim

---

### Post by dtester on 2008-11-18
Thanks Jim for the quick response.  I will give it a try.

Thanks also for the how to instructions.:KS

---

### Post by deadowl on 2008-11-18
What do you use TeraTerm for?

---

### Post by dtester on 2008-11-19
it is alot like hyper terminal but on steriods.  I use it to console into Cisco equipment to modify the config files

---

### Post by timcredible on 2008-11-19
i've been using kermit (package name 'ckermit' in the repos) for 14 years (yes, 14 years) to access console ports.  to use after installing via synaptic: ```

open terminal (applications -> accesories -> terminal)
kermit
set line /dev/ttyS0 (this is equal to COM1 in windows)
set carrier-watch off
connect

```

---

### Post by iponeverything on 2008-11-19
I use minicom for cisco configuration.

---

