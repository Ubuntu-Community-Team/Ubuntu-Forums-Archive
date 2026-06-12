---
title: "powernowd not starting on boot in edgy"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by Absolute Nirvana on 2006-10-31
Hello All,

I seem to be having trouble getting the powernowd daemon to properly start upon boot despite everything for powernowd seeming to be in place.  This problem is happening on my Dell Latitude D620 laptop.  Before I was running Dapper and powernowd worked fine and started properly on boot.  Now I recently did a clean install of Edgy and powernowd does not start on boot.

When I boot into Edgy the powernowd process is not running and I verified this using the command:
```
ps -e | grep powernowd
```
and i didn't get anything back.  By default my cpu runs the OnDemand govener upon boot.

 I can start powernowd manually after start by typing the command:
```
sudo powernowd
```
And my cpu successfully switches from OnDemand to Userspace govener and the powernowd daemon shows up under the ps command. So I know that powernowd does work for me under Edgy.

Also, the proper init scripts for powernowd to start on boot all seem to exist:
```

./etc/init.d/powernowd.early
./etc/init.d/powernowd
./etc/rc2.d/S10powernowd.early
./etc/rc2.d/S20powernowd
./etc/rc3.d/S20powernowd
./etc/rc4.d/S20powernowd
./etc/rc5.d/S20powernowd
./etc/rc1.d/K20powernowd

```

Powernowd is also marked under **System > Administration > Services** as active.

And, according to the boot log the powernowd daemon is being started successfully:
```

cat /var/log/boot | grep powernow
Oct 31 19:32:43 rc2:  * Starting powernowd...                            [ ok ] 

```

So I am having a hard time figuring out why powernowd is not showing up on boot.  I even tried adding powernowd as a startup program in my Gnome Session, but that didn't work either.  I tried searching into problems with powernowd and Edgy but I have not come across this one yet.  Can anyone help out with this situation?  Any comments would be greatly appreciated. Thank you.

---

### Post by Absolute Nirvana on 2006-11-01
bump. Anyone have any ideas of things i can check about powernowd?

---

### Post by edantes on 2006-11-13
Funny.  I found this thread because I wanted to get rid of powernowd.

It doesn't  make my Dell Inspiron happy.  I keep getting lost  mouse synchronization messages and sound applications stutter frequently.

Anyway, I can start it with 

sudo /etc/init.d/powernowd start

and excluded it  from boot by unselecting it in  the services manager gui (System-> Administration->Services).

---

### Post by Absolute Nirvana on 2006-11-15
> **edantes said:**
> Funny.  I found this thread because I wanted to get rid of powernowd.

It doesn't  make my Dell Inspiron happy.  I keep getting lost  mouse synchronization messages and sound applications stutter frequently.

Anyway, I can start it with 

sudo /etc/init.d/powernowd start

and excluded it  from boot by unselecting it in  the services manager gui (System-> Administration->Services).

Which Dell Inspiron model do you have if you don't mind me asking?

---

### Post by 325damien on 2007-03-01
I had this problem on edgy as well, with the powernowd script not activating at boot time. It was funny because when I had dapper installed the powernowd script worked just fine at startup.

So I solved the problem by simply replacing the edgy powernowd script in /etc/init.d with the dapper powernowd script. Works just fine now.

Hope this helps someone out in the same situation.

---

