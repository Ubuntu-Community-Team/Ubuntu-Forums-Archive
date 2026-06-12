---
title: "Lacie d2 problems"
date: 2008-08-22
forum: General Help
---

### Post by 321.george on 2008-08-22
Hey i was given a Lacie d2 mini 300gb external hard drive as the owner had no use for it because the nic didnt work on it.
However I am having some problems getting it working, when I run

```
./EDmini_LogOn
```

I get

```
Fontconfig warning: "/etc/fonts/conf.d/80-delicious.conf", line 17: invalid match target "scan"
Fontconfig warning: line 73: unknown element "cachedir"
Fontconfig warning: line 74: unknown element "cachedir"

```

Any ideas?

Edit: In /media there are two folders one titled EDMINILOGON and the other EDMINILOGON-1 there only appears to be files in the latter.

---

### Post by 321.george on 2008-08-22
Ok using DDD as suggested in this guide [http://randommatt.wordpress.com/2007/08/21/lacie-ethernet-disk-mini-linux-ubuntu-edmini_logon/](http://randommatt.wordpress.com/2007/08/21/lacie-ethernet-disk-mini-linux-ubuntu-edmini_logon/) gets me to a usable login form, however when I attempt to login I get an error message that says "Error while identifying Drive".
So my next plan of action is to take the drive out and connect to to the computer internally any thoughts on that?

---

### Post by randomas on 2008-08-25
Glad to see those guides are of some use! :p

Did you run the comands as root (or with sudo), if you don't they won't work. 

you can use gdb from the command line as well if you prefer, from the directory where you saved the executable:

```
sudo gdb EDmini_LogOn 
```

and from inside GDB type "run" then "continue" untill the logon interface appears. 
To exit gdb type quit.

---

### Post by jesperj5 on 2008-11-08
I have a Lacie drive with a similar log-on feature.

I get the exact same error message as the one described by 321.george. I have tried to run it as root but still get the same message; "Error while identifying Drive". I have tried this Lacie drive on previous Ubuntu versions (currently running 8.04) but have not had any luck so far.

It is a real pity since it is one of the last things that keeps me dual booting. 

I am sorry that I am not able to contribute towards a solution to this problem, but I would like to keep this thread alive.

---

