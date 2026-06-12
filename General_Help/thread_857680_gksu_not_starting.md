---
title: "gksu not starting"
date: 2008-07-12
forum: General Help
---

### Post by jdarias on 2008-07-12
I've started having issues with the administrative tasks. They are not running.
For example, i start synaptic form the applications menu, and all i get is the cursor working on 2nd plane, then nothing. I try again and nothing happens.
Then i discovered in system monitor two gksu processes, they both appear sleeping. I kill them both and try again. Most of the times it doesn't work.
So now i have to start the administrative apps from the console via sudo. gksu just doesn't work.

---

### Post by jdarias on 2008-07-14
Please help. This is really annoying. I tried downgrading from hardy-updates to hardy, but the issue continues. I recently installed a d-link switch to share my internet connection to a laptop. May this be related?

---

### Post by VMC on 2008-07-14
What exactly is your process. From Applications menu there is "Add/Remove...". That doesn't work? From "System > Administration > Synaptic Package Manager". That doesn't work either?

Have you tried "sudo apt-get clean" and "sudo apt-get autoremove"?

---

### Post by jdarias on 2008-07-15
Yea, those ones you mention don't work. I've noticed these entries use gksu for root authentication. So when i start one of these, the password prompt never appears (therefore the app never starts), and if i go to the system monitor, i'll see the gksu proccess in there, in sleep mode. So i kill it, and try it again.
It may work a second or third time, but using sudo in the console does not lag as much as gksu does.
I've noticed this problem since i installed a switch to share files and internet between this pc and a laptop.
Forgot to mention, i'm using xubuntu, not GNOME.

I'm going to check if clean or autoremove changes anythig, but at the moment the cache is clean.

---

### Post by schmidtbag on 2008-07-16
i'm getting this exact same problem, except lately more and more programs are starting up slower and i use regular ubuntu.  my ram and cpu usage is fine.  i noticed that only mandatory programs that come with gnome seem to do this.  for example, when i click on "quit", it takes about a full minute before anything shows up and i can't click on anything until it shows up.  this problem is driving me crazy

---

### Post by schmidtbag on 2008-07-16
as an update, I found that all of my administrative programs start up perfectly fine, as long as my computer is the only one on in the network.  otherwise it takes forever.

if you do file sharing often, i suppose you should just log yourself into a different workgroup, i'm assuming that'll get rid of the loading problem, at least it should half the waiting time.

samba is what connects you to windows computers.  this computer i'm typing on now is the only one running linux in my house, so i'm guessing that may be the cause of something.  i'm sure the devs of ubuntu have more than just 1 computer running the os in their house, and i doubt they wouldn't have noticed ubuntu lagging when running their own utilities, so its probably a windows network problem.

hope that helps somewhat, or at least guides you in the right direction

---

### Post by iaculallad on 2008-07-16
> **jdarias said:**
> Yea, those ones you mention don't work. I've noticed these entries use gksu for root authentication. So when i start one of these, the password prompt never appears (therefore the app never starts), and if i go to the system monitor, i'll see the gksu proccess in there, in sleep mode. So i kill it, and try it again.
It may work a second or third time, but using sudo in the console does not lag as much as gksu does.
I've noticed this problem since i installed a switch to share files and internet between this pc and a laptop.
Forgot to mention, i'm using xubuntu, not GNOME.

I'm going to check if clean or autoremove changes anythig, but at the moment the cache is clean.

Post whatever displays when you issue the command below on your terminal:

```
cat /etc/hosts
```

---

