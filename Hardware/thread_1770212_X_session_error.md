---
title: "X session error"
date: 2011-05-28
forum: Hardware
---

### Post by ciscoboy on 2011-05-28
To anyone who knows anything about Ubuntu and lubuntu,
 
I have an error at startup that says:
 
"Xsession:unable to launch "/usr/bin/startlubuntu" X session ---
"/usr/bin/startlubuntu" not found; falling back to default session."
 
in the small window in which this message appears, is also a button that says "okay".
 
and when I click it, it shows a black screen with the cursor, without showing any signs
that it would change. If this is in the wrong category, I apologise, as I am also new to 
posts and forums; I figured that it would be a good place to post the thread, as the 
computer in question is a laptop.
 
Also, if it could be of any use or consequence, I downloaded a program (can't remember the name of the program, but I remember that it was to track satelites-under amateur radio in synaptic), and I did a complete removal. I figured that it could have been the leading cause, as the computer failed to start shortly after.
 
Thank you in advance to anyone who responds
 
Ciscoboy

---

### Post by cavalier911 on 2011-05-29
```
rj@lubuntu:~$ dpkg -S startlubuntu
lubuntu-default-settings: /usr/bin/startlubuntu
lubuntu-default-settings: /usr/bin/startlubuntu-netbook
```

Verify with File Manager you have no /usr/bin/startlubuntu

Boot into the live cd you installed from and copy /usr/bin/startlubuntu over to your install with the file manager.

Normally I would suggest you reinstall the package providing the missing file. 
But download/reinstall of lubuntu-default-settings fails on my system.

```
rj@lubuntu:~$ sudo apt-get install lubuntu-default-settings --reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of lubuntu-default-settings is not possible, it cannot be downloaded.
```

---

### Post by ciscoboy on 2011-08-04
sorry for being so long before getting back to you, but I had a hard time downloading a lubuntu ISO, because it's a computer that was loaned to me, and i didn't have the original live disc. 


Now, I did everything that you said I should do.

I first started with:

Code:
rj@lubuntu:~$ dpkg -S startlubuntu

And I got this:

lubuntu-default-settings: /usr/bin/startlubuntu
lubuntu-default-settings: /usr/bin/startlubuntu-netbook


Then, I did the second set of codes:

rj@lubuntu:~$ sudo apt-get install lubuntu-default-settings --reinstall

And I got this as well

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of lubuntu-default-settings is not possible, it cannot be downloaded.

I also tried to copy the file using file manager as you suggested, but it said permission denied. I also tried it as administator, but it still didn't work. 

What should I do next?

---

### Post by ciscoboy on 2012-06-21
For anyone who has, had or will have this problem, I wanted to let know that I reinstalled Linux on my computer. If you have problems with the installation using the live USB, try the Live CD instead.

---

