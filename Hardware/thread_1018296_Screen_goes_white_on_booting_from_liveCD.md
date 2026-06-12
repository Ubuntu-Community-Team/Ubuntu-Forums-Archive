---
title: "Screen goes white on booting from liveCD"
date: 2008-12-21
forum: Hardware
---

### Post by madHatterCutsTheChatter on 2008-12-21
hi!

i have a sonyFW series laptop with 16/9 resolution. I tried installing 8.04 on my computer but after restarting & booting into the live-CD image the screen went completely blank. The same happens with 8.10. i cant even proceed with the installation as i cant see anything.

Any clues?

---

### Post by prshah on 2008-12-22
> **madHatterCutsTheChatter said:**
> the screen went completely blank. 


If you're getting a full white screen (as in your title) then probably you're running into problems with advanced desktop effects. You can turn it off by blind-typing the following command:

a) Press Alt+F2
b) Type in ```
metacity --replace
```

If your screen doesn't recover, 

a) either you've typed the command wrongly; press esc a couple of times and try again

b) or desktop effects is not the issue; in that case, post back for further troubleshooting.

---

### Post by madHatterCutsTheChatter on 2008-12-22
I tried alt+f2, nothing happened, but ctrl+alt+f2, i went to the command line. 
I tried it there & it said "can't open display."

---

### Post by prshah on 2008-12-22
> **madHatterCutsTheChatter said:**
> I tried alt+f2, nothing happened, but ctrl+alt+f2, i went to the command line. 
I tried it there & it said "can't open display."

Did you try blind typing "metacity --replace" after pressign Alt+F2?

From the virtual console (Ctrl_Alt_F2) you cannot use the metacity command because the Window Manager is running on another "display"; if you want to do from Ctrl+Alt+F2, try this command instead```
#either
DISPLAY=:0 metacity --replace
#or
metacity --display=:0 --replace
```

Then switch back to GUI with Ctrl+Alt+F7 (in some cases may also be F9 or F10).

Did either of the above three work?

---

### Post by madHatterCutsTheChatter on 2008-12-23
Tried all of them, the commands on the other display never complete, they keep running. 
i also tried ctrl,alt,bksp after each of them, separately.
the screen remains white.

I think it may have to do with the display adapter for intel 4500 gfx card. Am i really stuck with vista till they release any new drivers?

---

### Post by prshah on 2008-12-23
> **madHatterCutsTheChatter said:**
> the commands on the other display never complete, they keep running. 

They are not supposed to "complete"; they are supposed to keep running. To "complete" them (return to command prompt after executing command) add a space and an ampersand ("&") after the command; eg```

metacity --display=:0 --replace[color=red] &[/color]
```

Did you give the command and switch back with Ctrl+Alt+F7? 

Here's something additional you can try. In the virtual console (Ctrl+Alt+F2), give the command ```
sudo killall compiz.real
``` and switch back; is the screen still white? Or do you have borderless windows now?

Yet another thing to try```

sudo /etc/init.d/gdm stop
sudo killall compiz.real
sudo chmod a-x /usr/bin/compiz
sudo chmod a-x /usr/bin/compiz.real
sudo /etc/init.d/gdm start
```

...And then switch back with Ctrl+Alt+F7.

If none of these suggestions work then I very much suspect you are right when you say it is a driver issue.

---

### Post by madHatterCutsTheChatter on 2009-01-03
i think it was a driver issue 'coz the above suggestions didnt work either. 

I found the following link useful(basically recompiling the intel driver). 
Any1 having similar issues can go here:

[http://ubuntuforums.org/showthread.php?t=1023801](http://ubuntuforums.org/showthread.php?t=1023801)

Thanks for ur help!

linux finally works on this comp.!!

---

