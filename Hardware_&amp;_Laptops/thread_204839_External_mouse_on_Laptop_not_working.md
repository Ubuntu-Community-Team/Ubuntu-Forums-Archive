---
title: "External mouse on Laptop not working"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by Dr. Feelgood on 2006-06-27
I can't seem to get an external mouse working on my laptop.  It's a Compaq Presario 700 running Dapper.  My built in touchpad works fine but when I hook up the external mouse nothing happens.  Every now and then when I keep moving the mouse around the pointer will move erratically for a second so it's getting some kind of input.  Any ideas on what I can do?  It's just a regular old mouse.... not USB.  I've tried 2 different mice too so its not a bad mouse.

---

### Post by Dr. Feelgood on 2006-06-29
For future reference here's the solution to the problem

open a terminal

```
sudo gedit /etc/rc.local
```

then type in

modprobe -r psmouse
modprobe psmouse proto=imps

I placed this before the exit 0 line

save and restart

---

### Post by Buddy Gurt on 2006-08-04
I seem to have the exact same problem, on exact the same machine. However, I'm using Ubuntu 5.10 instead of 6.0.6, but I don't think that will be a problem. Do you happen to remember where you've found this solution? Do you have a webaddress with the information?

---

### Post by Dr. Feelgood on 2006-08-05
I did some serious searching on the web boards.  I can't remember where they were but I know it's out there.

---

### Post by Buddy Gurt on 2006-08-07
Doesn´t matter. I finally fixed the problem this weekend.
I was able to solve the problem in Ubuntu 5.10 quite easily by changing "psmouse" in "psmouse proto=imps" in **/etc/modules**. However, after upgrading to 6.0.6 that didn't work anymore. Furthermore I found out that /etc/rc.local didn't exist, and even if I created it and put in the lines you mentioned, it did not help: still no response from the external mouse. However, some searching on the web gave me the solution: I added your two lines
```
modprobe psmouse -r
modprobe psmouse proto=imps
``` in the bootfile **/etc/init.d/bootmisc.sh**, right before the exit 0 line. And it worked! So now I'm finally running Ubuntu with a proper functioning PS/2 mouse (including scroll wheel)!

---

