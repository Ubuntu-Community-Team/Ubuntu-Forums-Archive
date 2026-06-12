---
title: "Error beep in ubuntu..."
date: 2008-11-19
forum: Hardware
---

### Post by warsong on 2008-11-19
Hey all.

I just installed 8.10 and my sound seems to be working fine except for one thing. I believe its the error sound.
 
Example: when you press backspace in pidgeon in your convo box and there's no characters to delete or in Firefox when your doing a search and you type a string of characters that it doesn't find. 

Instead of playing on my computer speakers, it just triggers my internal speaker beep loudly. Is this normal ubuntu behavior? If it is, is there a way to disable it or change it to a sound that comes out of my actual speakers. Reason being that its very loud and cannot be controlled by volume.

---

### Post by warsong on 2008-11-19
Bump. Any ideas anyone?

---

### Post by Mostly Harmless Eccentric on 2008-11-19
I'm interested in this too. It's kind of a grating sound, and I use Pidgin daily. It's a real pain.

---

### Post by warsong on 2008-11-21
I found this on the net just before...
```

To disable it temporarily:

   1. In Terminal (or the console), enter: “sudo rmmod pcspkr”
   2. You should not hear the system beep until your next system reboot.

To disable it permanently:

   1. In Terminal (or the console), enter: “sudo nano /etc/modprobe.d/blacklist”
   2. At the end of the file, enter a new line “blacklist pcspkr”
   3. Type Ctrl+O (to save the file), then Ctrl+X (to exit nano)
   4. After your next system reboot, you should no longer here the system beep.

```

I haven't tried it yet because I don't have my laptop with me at the current moment. Also not sure if this is the best solution...

---

### Post by rexless on 2009-04-10
Thanks!!!

Whomever builds/manages the sound mixer's would do us all a huge favour by adding an option to enable/disable the pc speaker to that tool.

---

