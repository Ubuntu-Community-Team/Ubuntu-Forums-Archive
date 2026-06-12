---
title: "idle3 - python IDE - cannot install via Synaptic"
date: 2008-11-14
forum: General Help
---

### Post by jimmy the saint on 2008-11-14
I have decided to learn python.  Since python is advancing to version 3, it was recommended that I learn that standard.  Unfortunately, the Gedit python console will only use python 2.5, so I want to install idle3.  When I attempt to install idle3 I get the following error

```
 Depends: python3-tk (>=2.4.3-3) but it is not installable 
```

when I try to install an alternate package, idle-python3.0, I get this error

```
idle-python3.0:
 Depends: python-tk but it is not going to be installed
 Depends: python3.0-tk  but it is not installable 
```

I am sure someone else has got all this straightened out.  What do I need to do?  I can't find these packages anywhere.

Also, if I have both versions installed, how do ensure that my code is run against python3 rather than 2.5?  If anyone has any other tips, I would be grateful.  

Thanks

JTS

---

### Post by jimmy the saint on 2008-11-14
So in the package details for intrepid, it lists python3-tk (>= 2.4.3-3) as not available.  Why is there a package available in the repositories that clearly does not have its dependencies met?  I thought that was the whole point of the repositories???

WTF??

JTS

---

### Post by daradib on 2008-11-15
Same problem here. Bug report [here]("https://bugs.launchpad.net/ubuntu/+source/python3.0/+bug/298206").

---

### Post by jimmy the saint on 2008-11-16
Yeah, I filed that bug, but I doubbt it will be much of a priority.  I posted a question about it to the programming section and got a lot of great overall advice that really made me realize that it wasn't that important anyway.  That said, I still think its pretty bad form to put a package in the repos with missing dependecies.  If I wanted to play with missing dependencies I wouldn't bother with a package manager!! :)

---

### Post by stucky on 2009-02-23
...and even worse when it hasn't been fixed 3 months later.

---

### Post by daradib on 2009-02-24
> **stucky said:**
> ...and even worse when it hasn't been fixed 3 months later.

In Ubuntu Jaunty, I have successfully installed and run idle3 without any dependency problems. However, idle-python3.0 still gives dependency problems.

```
Depends: python-tk (>=2.6~a3) but 2.5.4-0ubuntu2 is to be installed
```

---

### Post by go_beep_yourself on 2009-03-12
I got it working! Idle too. Just go to python.org, grab the latest 3 release and start compiling. :popcorn:

[PHP]chris@ubuntu:~/Desktop$ python3.0
Python 3.0.1 (r301:69556, Mar 12 2009, 14:34:52) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 0b1101001 # my binary literal :D
105
>>> from sys import version
>>> version
'3.0.1 (r301:69556, Mar 12 2009, 14:34:52) \n[GCC 4.3.2]'
>>>[/PHP]

---

### Post by David C. on 2009-04-26
> **go_beep_yourself said:**
> I got it working! Idle too. Just go to python.org, grab the latest 3 release and start compiling. :popcorn:

[PHP]chris@ubuntu:~/Desktop$ python3.0
Python 3.0.1 (r301:69556, Mar 12 2009, 14:34:52) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 0b1101001 # my binary literal :D
105
>>> from sys import version
>>> version
'3.0.1 (r301:69556, Mar 12 2009, 14:34:52) \n[GCC 4.3.2]'
>>>[/PHP]

I did the above, but still getting the error:

*Depends: python-tk (>=2.6~a3) but 2.5.2-1ubuntu1 is to be installed*

when trying to install from the synaptic. I can use the terminal console by entering python3.0 for now, but now I can't get it to import the tkinter module, but it's listed in the modules section when I run "help" then "modules". I'm getting the error:

```
> import tkinter
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python3.0/tkinter/__init__.py", line 39, in <module>
    import _tkinter # If this fails your Python may not be configured for Tk
ImportError: No module named _tkinter
>>> import _tkinter
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named _tkinter

```

Looked at the line it mention in the .py file. says the same thing and I am not familiar enough with python to do a correct fix. 

I'm getting frustrated with this. No dependencies are inlcuded for IDLE 3.0 and with 2.5 I couldn't get it to list all the modules available. What's up here? I'm trying to learn this program, but in one version  help doesn't list modules at all, and the 3.0 IDLE and the tkinter module aren't recognized.

---

### Post by daradib on 2009-04-26
The bug has been fixed in Ubuntu 9.04 for a while now, so you can try installing the idle-python3.0 package from the Ubuntu 9.04 repository or upgrade to Ubuntu 9.04.

---

### Post by David C. on 2009-04-28
> **daradib said:**
> The bug has been fixed in Ubuntu 9.04 for a while now, so you can try installing the idle-python3.0 package from the Ubuntu 9.04 repository or upgrade to Ubuntu 9.04.

I upgraded to 9.04 and the IDE for 2.6 and 3.0 work great. Now, if I could get my graphics card to work properly.

---

### Post by daradib on 2009-04-28
> **David C. said:**
> I upgraded to 9.04 and the IDE for 2.6 and 3.0 work great. Now, if I could get my graphics card to work properly.

Hooray! What graphics card do you have? Paste the appropriate line(s) about display or VGA controller if you run the command lspci in terminal.

---

