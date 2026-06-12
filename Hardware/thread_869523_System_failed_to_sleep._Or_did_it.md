---
title: "System failed to sleep. Or did it?"
date: 2008-07-24
forum: Hardware
---

### Post by wizardfait on 2008-07-24
I just woke my computer from a sleep today, and I am greeted with a message saying that it failed to sleep, however, for the past 12+ hours, it was sleeping, fully lowered into a low power state (Or at least enough that without using a multimeter, it's impossible to tell) and had no problem doing it.

I will say though, that as my laptop goes to sleep, it turns on the Numlock, Capslock, and ScrollLock lights of my computer, then turns them off, the speakers pop, due to the speakers being unloaded, but just after, the harddrive goes solid then finally goes to sleep... 

Is this something to be concerned about? Or should I just act like it never happened? Nothing's wrong with it, like even now, it's completely stable...

---

### Post by wizardfait on 2008-07-25
Sorry to double post, but I'm simply bumping, because I'm assuming that noone saw this... =\

---

### Post by wizardfait on 2008-07-27
Bump.

---

### Post by sdennie on 2008-07-27
No, this isn't really something to worry about.  Depending on your laptop vendor, suspend/resume is spotty.  There should be a button on the, "You failed to suspend" dialog that says, "Don't show me this again" but, if not, hit Alt-F2, type gconf-editor and go to /apps/gnome-power-manager/notify and uncheck sleep_failed.

---

### Post by wizardfait on 2008-07-27
Yes, there is, I just didn't want to hit it if it was something I was wanting to worry about. :)

One last question... Kind of on topic. Idk if it's ubuntu related, because I never ran windows on here long enough to find out... But sometimes if it's plugged in, and the cover's closed, and I unplug it, it'll turn off... If I open the screen before I unplug it, it'll never do that... Is that at all possibly an ubuntu problem? Like, possibly changing power states in a way that is "unexpected" by my machine makes the kernel freak or something? (Wouldn't be the first time my machine's done something that Ubuntu didn't like... First 3 minutes of using live cd were waiting for the Floppy drive that doesn't exist... Then I ended up having to reboot at least 4 times to get it installed, because my cpu kept sending and unexpected command or something... But those I cleared up...)

---

### Post by prostar on 2008-09-10
I'm sure you've solved it by now.  But the unplugging with the lid closed thing is probably your settings for what it should do when on battery power and you close the lid.  Check your power settings under System -> Preferences -> Screen Saver [Power Management].  It probably does what you told it to do ;) ...

---

