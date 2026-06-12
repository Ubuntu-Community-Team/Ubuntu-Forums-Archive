---
title: "Is it possible to speed up boot times?"
date: 2008-08-15
forum: General Help
---

### Post by Suilenroc on 2008-08-15
Hey all, relatively new Ubuntu user here. I'm currently searching for ways to increase the boot-up times on my Ubuntu install. It's on a laptop, with a Athlon X2 2.2ghz CPU, and 2 gigs of RAM. I've googled some guides, but I don't know enough about linux yet to determine whether or not they're viable, and the fear of crippling my system is stopping me from just trying them out.


Thanks in advance!

-Suilenroc

---

### Post by jackTL2 on 2008-08-15
Hello, 

This might be helpful: [http://its-about-amoena.blogspot.com/2007/12/how-to-make-ubuntu-to-start-faster.html](http://its-about-amoena.blogspot.com/2007/12/how-to-make-ubuntu-to-start-faster.html)

If you're new to linux you can't let the fear of crippling your system scare you from learning. :)

---

### Post by Suilenroc on 2008-08-15
Hey, thanks. That managed to shave 3 seconds off of my boot times. 30S to 27S. Now I just need to figure out how to make it overall more responsive. (I'm trying to convince a friend to get Ubuntu. We have identical laptops, his is with vista, mine with Ubuntu. Every second I can shave off of app launch times, etc, counts.)

---

### Post by sdennie on 2008-08-15
For a laptop, you can get your "boot" times down to about 5 seconds.  Just never shut the machine down and always use suspend.  ;)

---

### Post by Suilenroc on 2008-08-15
Eheh, true, true. I need to get used to using that, it's not something that I ever used on Windows.

---

### Post by sdennie on 2008-08-15
> **Suilenroc said:**
> Eheh, true, true. I need to get used to using that, it's not something that I ever used on Windows.

You can set your laptop to suspend when the lid is closed (very useful) by going to System->Preferences->Power Management and setting the lid close action to Suspend (make sure to do it in both tabs).

As for startup times, you should keep this in mind: If you spend 1 hour optimizing your boot time and it makes your machine boot 10 seconds faster, it will take you 360 boots to recuperate the time you spent optimizing the boot.

---

### Post by Suilenroc on 2008-08-15
> **vor said:**
> You can set your laptop to suspend when the lid is closed (very useful) by going to System->Preferences->Power Management and setting the lid close action to Suspend (make sure to do it in both tabs).

As for startup times, you should keep this in mind: If you spend 1 hour optimizing your boot time and it makes your machine boot 10 seconds faster, it will take you 360 boots to recuperate the time you spent optimizing the boot.

Thanks, that will be useful. And I'm well aware of the problem of time put in vs. time given back when it comes to computers. For me, when it comes down to it, it's not about what really comes out (although that's useful), but about the feeling of knowing that I made it better than it was. In simpler terms: E-peen.

I'm an overclocker, that should tell you everything you need to know. :P

---

### Post by ds[de] on 2008-08-15
This could also help you :o)

[http://blogs.techrepublic.com.com/10things/?p=387](http://blogs.techrepublic.com.com/10things/?p=387)

Regards,
ds[de]

---

### Post by PCessna on 2008-08-15
> **'ds[de] said:**
> This could also help you :o)

[http://blogs.techrepublic.com.com/10things/?p=387](http://blogs.techrepublic.com.com/10things/?p=387)

Regards,
ds[de]
Very interesting, I'm a bit confused on the 'boot to level 3' although I wish to try it, this will not create any problems switching to the regular graphics interface that we use when using ubuntu after done loading, right?

---

### Post by picpak on 2008-08-15
You can install sysv-rc-conf

```
sudo apt-get install sysv-rc-conf
```

and then run

```
sudo sysv-rc-conf
```

to disable whatever services you don't need. You may need to do some Googling to find out if you need it or not, though. I got my boot down to about 40 seconds with this. :)

---

