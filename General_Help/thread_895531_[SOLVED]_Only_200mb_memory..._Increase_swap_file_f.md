---
title: "[SOLVED] Only 200mb memory... Increase swap file for better performance?"
date: 2008-08-20
forum: General Help
---

### Post by Jamina1 on 2008-08-20
Hi!

Recently I installed Ubuntu 8.04 server on an old windows machine. It worked pretty great. But I really needed the desktop environment and so I re-installed with this.

Unfortunately, this particular computer only has 200 some MB of memory. It worked well enough as a server, but is bogging down considerably with the desktop environment.

Short of purchasing more memory for the machine, is there any way I can increase performance? 

Possibly by upping the swap file size? The CPU isn't doing much, it hangs at about 18% when idling. The memory is almost constantly 70% full though.

---

### Post by snowpine on 2008-08-20
> **Jamina1 said:**
> Hi!

Recently I installed Ubuntu 8.04 server on an old windows machine. It worked pretty great. But I really needed the desktop environment and so I re-installed with this.

Unfortunately, this particular computer only has 200 some MB of memory. It worked well enough as a server, but is bogging down considerably with the desktop environment.

Short of purchasing more memory for the machine, is there any way I can increase performance? 

Possibly by upping the swap file size? The CPU isn't doing much, it hangs at about 18% when idling. The memory is almost constantly 70% full though.

Hi Jamina, I would recommend the Xubuntu desktop, which uses Xfce and is a lot lighter on resources than Ubuntu/Gnome. The recommended minimum ram for Ubuntu is 256mb, and in my experience, 512mb or more is desirable.

---

### Post by Elfy on 2008-08-20
Maybe use a different version, with a lighter desktop - xubuntu would be a better choice with the memory available.

You could install it from the command line, but I'm not sure whether you would be better of with a clean install, anyway to install xubuntu from  a terminal do

```
sudo aptitude install xubuntu-desktop
```

---

### Post by falcon61102 on 2008-08-20
And to answer your original question about the SWAP file.  While it is possible to expand the size of your SWAP file/partition, there comes a point where it no longer improves performance because the system can only use so much.  That limit is approximately 1.5 times the amount of RAM your have which is why most people suggest a SWAP to be twice the size of your RAM.  Another thing about your SWAP is that because it's using HD space, it is much, much slower than your RAM.  

Just FYI.

---

### Post by snowpine on 2008-08-20
At a certain point, the computer is "just plain old" and upgrading a single component (more swap, ram, hard drive, video, etc) isn't going to magically transform it into a modern computer. :)

---

### Post by falcon61102 on 2008-08-20
Well, I was trying to say it nicely... :)

---

### Post by snowpine on 2008-08-20
Sorry! :)

---

### Post by Jamina1 on 2008-08-21
> **snowpine said:**
> At a certain point, the computer is "just plain old" and upgrading a single component (more swap, ram, hard drive, video, etc) isn't going to magically transform it into a modern computer. :)

Yeah, it isn't *my* computer per-se. Its a work computer box (I have NO IDEA how they ran XP on this thing, but they did....) and I was re-purposing it and having difficulties even running plain ubuntu desktop. The processor is good and the hard drive is more than generous, its just the memory that sucks. For a word processing machine, though, it'd be alright, which is all we ever really need here anyway.

I figured out how to start up certain programs (firefox, etc) using a VNC server, since the command line alone was much more repsonsive and I only really need a web browser now and again, everything else can be done in command line.

I've heard PLD Titanium is SUPER FAST. If I can figure out how to install stuff on it, I might give it a shot.

---

