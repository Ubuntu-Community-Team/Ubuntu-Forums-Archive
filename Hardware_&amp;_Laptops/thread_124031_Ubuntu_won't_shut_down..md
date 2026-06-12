---
title: "Ubuntu won't shut down."
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by catalina on 2006-01-31
Newby here.  Been impressed and happy with how ubuntu functions on ibm t21 laptop.  Have recently exprerience a problem of laptop not shutting down fully.  I know there is probably an easy answere but if someone can spare some time and help me out I would really appreciate it.

Dean.

---

### Post by PaganHippie on 2006-01-31
What exactly do you mean by, 'not shutting down fully'? What happens when you issue the shutdown comand?  The computer should power down at the end of the shutdown cycle, unless you've specified 'reboot'.

In an emergency, you can open a shell (or even <ctrl>-<alt>-<F2> to a new tty & log in), and type 
```
sudo shutdown now
```  and that should do the trick.  I've had to do this a couple of times, myself.

---

### Post by catalina on 2006-02-01
When I select the "shutdown" selection it cycles out and starts to close all of the operations and then it gets hung up at a certain point.  I end up having to pull the plug and battery out in order to get it off completely.  I would not be concerned about it but I shut it down, left the room the laptop was in, came back the next day and the laptop was stuck closing the applications.  I could get lcd burn on the screen.

I tried the "sudo shutdown now" command and it got hung up at "sending processes the Term signal" then back to the prompt for logging in or out.

I did notice that it failed to stop the hardware abstraction layer and stopping the deferred execution schedule.  The last process that it attempted it would "enter into single user mode" then "go to single user" and then "sending processes to the Term signal"

Thank you for your suggestion.

---

### Post by NikoC on 2006-02-02
Perhaps this thread might help you ...
[http://www.ubuntuforums.org/showthread.php?t=75314]("http://www.ubuntuforums.org/showthread.php?t=75314")

---

