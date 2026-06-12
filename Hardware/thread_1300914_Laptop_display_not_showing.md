---
title: "Laptop display not showing"
date: 2009-10-25
forum: Hardware
---

### Post by c0mput3r_n3rD on 2009-10-25
Hello all,

  I changed my display rotation and now nothing shows up on the screen (the screen isn't even lit) after ubuntu finishes loading at boot up.  It's an IBM R40 running Ubuntu 9.04.  I could sign in, open a terminal and run a command w/o  the display, or boot up via live cd and do the changes from there.

Any help what so ever would be greatly appreciated,
Thanks

---

### Post by c0mput3r_n3rD on 2009-10-25
Sorry to bump this but it's kind of important because I have notes on that computer for a class I'm having a test in this week, so if any body knows a command that will work , or a configuration file I can edit from a live cd please let me know.

---

### Post by ajgreeny on 2009-10-25
I've been looking, but can't find it unless it has become part of your /etc/X11/xorg.conf file.  See if there is anything in that which appears to relate to the display rotation, and if so back up the file and edit it out, then try a login again.

Failing that as a temporary measure it may be possible to rename the ~/,gconf folder as ~/.gconfbak and then logout and in again.  That will remove most of your display configuration, but I am not sure about the rotation effect.

As a last resort you can always get to your files using the live CD, and work on them as well, if you need to, though it will of course be rather slower than you are used to.

---

### Post by c0mput3r_n3rD on 2009-10-25
Thank you very much for the suggestions, I'm going to check out those files mentioned and see what I can find.

---

### Post by c0mput3r_n3rD on 2009-10-26
Unfortunately I've tried editing those files, and renaming from a livecd, but to no avail.  Any other suggestions as to where a file that handles screen rotation may be located?

---

### Post by ajgreeny on 2009-10-26
I found this when having a look around [here]("http://brainstorm.ubuntu.com/idea/1873/") and it may help (or it may not!)

[ToyKeeper]("http://brainstorm.ubuntu.com/contributor/ToyKeeper/")     wrote on the 29 Feb 08 at 22:43      
         I don't know what hardware you're using, but rotation does "actually work" on my gutsy desktop...  sort of. 

If I run this, the screen rotates to display correctly while my monitor is rotated: 

xrandr --output DVI --rotate left 

However, it has some limitations. The screen updates rather slowly, because my system doesn't seem to support rotation in hardware. And, if I try to use a video overlay while rotated, the system seems to lock up. 

So, the intel video driver needs some work, but the functionality does at least exist.    
                    [dan.fernandez]("http://brainstorm.ubuntu.com/contributor/dan.fernandez/")     wrote on the 1 Mar 08 at 01:13      
         ToyKeeper, 
yes, it works, as long as you have: 

      Option "RandRRotation"              "on"  
      Option      "Rotate" "CW"  
      Option      "Rotate" "CCW"  

In your xorg.conf (not by default, or it's lost on screen resolution change). After that is in the file, a simple xrandr --rotate left / right / normal turns the screen. Would be nice to check when that options are lost and fix that.

Also see:-
[https://answers.launchpad.net/ubuntu/+question/15918](https://answers.launchpad.net/ubuntu/+question/15918)
[http://www.ubuntuts.com/screen-rotation-quick-and-useful-trick/](http://www.ubuntuts.com/screen-rotation-quick-and-useful-trick/)

---

