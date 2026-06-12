---
title: "Quick question.."
date: 2008-08-21
forum: General Help
---

### Post by Phases on 2008-08-21
Ubuntu 8.04 is telling me I have two gigs of ram in my system, when I only have one. 

I assume this is because it's counting swap space?

---

### Post by caljohnsmith on 2008-08-21
Where is Ubuntu telling you that you have 2 GB RAM? Try doing the following command:
```
free
```

---

### Post by finer recliner on 2008-08-21
swap != RAM

---

### Post by Phases on 2008-08-21
Thanks for the replies. 

Well, I'm at work and new to Ubunutu so, I don't remember exactly where in the GUI I saw it but googling around it was a screen that looked like this:

[http://tbn0.google.com/images?q=tbn:2qBcGrkriTW3pM:http://debasyslog.googlepages.com/ubuntu_system_monitor_tweaked.png](http://tbn0.google.com/images?q=tbn:2qBcGrkriTW3pM:http://debasyslog.googlepages.com/ubuntu_system_monitor_tweaked.png)

Sorry it's so small, all I could find. 

When I ssh in and type free:

            total       used       free     shared    buffers     cached
Mem:       2075688     310680    1765008          0      30160     185916
-/+ buffers/cache:      94604    1981084
Swap:      2996080          0    2996080

Or, free -m

             total       used       free     shared    buffers     cached
Mem:          2027        308       1718          0         29        185
-/+ buffers/cache:         92       1934
Swap:         2925          0       2925

(I know swap != ram, but 1gb != 2gb, so that was just all I could think of as an answer)

---

### Post by finer recliner on 2008-08-21
how much RAM does your BIOS recognize?

---

### Post by Phases on 2008-08-21
I'm not sure, I'll check that when I get home. But now that you mention it... When I finally fired my comp back up (been off a couple months) to wipe it and put Ubuntu on it - I discovered one of my sticks of ram was bad. (2 X 1g).

(My system had notified me by voice that I had bad ram)

The weird thing, with memtest, the one good stick does fine obviously, but bad stick... memtest won't even load up with it. just flashes and stays on a black screen.  I used to it loading up and scanning and finding errors. 

Both sticks of ram in system = voice telling me bad ram, memtest won't load.

Both sticks in, swapped slots = same.

stick 1 in alone = system runs fine, memtest does fine - this is how I'm set up now.

stick 2 in alone = voice telling me bad ram, memtest won't load.

I just found it strange memtest wouldn't even load. 

So maybe it's something with that?

---

