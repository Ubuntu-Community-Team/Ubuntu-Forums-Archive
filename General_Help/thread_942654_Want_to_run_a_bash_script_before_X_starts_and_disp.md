---
title: "Want to run a bash script before X starts and display to the screen"
date: 2008-10-09
forum: General Help
---

### Post by AddictiveStew on 2008-10-09
Hey everyone... I'm a n00b to the forums and I need your help.  Hopefully someone can point me in the right direction because I've exhausted all searches trying to find the right answer.  I'm creating an Ubuntu live CD for my company that will allow us to format machines using the shred command, then report the status back to our FTP server to confirm the machine has indeed been formatted.  The bash script works when I run it from a terminal session, it works in rc.local, however X puts it in the background and starts the GUI interface.  What I need is to display the messages to the screen and not even start X (but I still need all other services started) without user interference.  My script echos it's status thru each step and again it works perfectly fine when called via the command line.  Hopefully I'm making sense and someone can help me out.  Thanks!

---

### Post by bodhi.zazen on 2008-10-09
call your script from /etc/rc.local

---

### Post by carolinason on 2008-10-09
Not sure if this helps, but perhaps it will spark something. Disable X, gdm or kdm and put the command to run X in your script. So, if the condition is true on the device, then startx or gdm or kdm.??

---

### Post by AddictiveStew on 2008-10-09
I do call the script from rc.local, but it still insists on throwing it into the background and starting X.  When the script runs from the command line it halts and waits until shred finishes to continue.  Once X is up I can run top and see shred running.....and I can kill the process and the final portion runs as well (in the background) and sends my notification.  I need the user to be able to view the status the entire time, and I really don't care if X ever starts to be honest....

---

### Post by AddictiveStew on 2008-10-09
I am creating a live cd to do this, so is there an appropriate entry I could put somewhere to stop gdm from loading?  I still need all drives mounted and network connectivity though....

---

### Post by carolinason on 2008-10-09
Have you reviewed this thread. It is about removing gdm in ubuntu. 

[http://ubuntuforums.org/showthread.php?t=72333](http://ubuntuforums.org/showthread.php?t=72333)

---

### Post by carolinason on 2008-10-09
Default runlevel is 2 so /etc/rc2.d/Sxxgdm

change the S to K and it will not run

---

### Post by carolinason on 2008-10-09
Another way perhaps would be to boot the device in single mode and run all utilities, 

{
if the condition is true or all task ran and completed, 

then
reboot into a standard runlevel.
}
just an idea.

you might need to automate a login prompt in single mode. 

I don't script --yet--, so if I'm off then sorry.

---

### Post by AddictiveStew on 2008-10-09
I believe you are onto something with your previous idea.  Looks like GDM is called BEFORE rc.local.  rc.local is called before logon.  I've removed the symbolic link to gdm and I'll report back the results in about 45 minutes (gotta create and burn the iso).  EXCELLENT SUGGESTION (fingers crossed!)

---

### Post by AddictiveStew on 2008-10-09
I now see the script running!  I want to keep this thread open until tomorrow (shred will take overnight) just to verify the connectivity requirements were still met.  This is exactly what I was looking for!  Thanks carolinason!

---

### Post by AddictiveStew on 2008-10-10
Everything is working correctly and as expected.  Thanks again for the help!

---

