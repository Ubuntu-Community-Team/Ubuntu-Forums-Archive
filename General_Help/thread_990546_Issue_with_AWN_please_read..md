---
title: "Issue with AWN please read."
date: 2008-11-22
forum: General Help
---

### Post by gqstatus05 on 2008-11-22
ok I'm a first time Ubuntu user and I must say this is sweeeeeet! I own a Dell Inspiron 1501 laptop.

I'm dual booting it with Vista Home Premium.

I figured out the wireless issue which took a lot of reading. 

My new issue is that I figured out how to install AWN but I get two docks right on top of each other. I went into the settings of AWN and couldn't find anything. 

Here's a screenshot: 

[IMG]http://img.photobucket.com/albums/v687/BadBoyDiddy/Screenshot-1.png[/IMG]
If you look at it you can see another Mozilla icon underneath. 

What am I missing?

---

### Post by adult swim on 2008-11-22
its possible to have more than one instance of awn running at a time.  go to a terminal and type in ```
killall -9 avant-window-navigator
```  then press alt+f2 and run ```
avant-window-navigator
```

---

### Post by seeker5528 on 2008-11-22
I was getting a similar issue, not 100% sure, but I believe what cured it was going to 'System --> Preferences --> Sessions' and disabling the option to remember applications when logging out.

Later, Seeker

---

### Post by gqstatus05 on 2008-11-22
that option is already unchecked. 

I searched for that message on google and found a fix which helped me see the dock before the laptop was rebooted. What am I missing?

I like this operating system but why isn't there an easier way to install apps (like double clicking on an exe)?  

I'll keep playing with it, afterwards I'll see if I could find info on how to tether my iPhone to Ubuntu. Thanks for your help guys. 

Thanks.

---

### Post by gqstatus05 on 2008-11-26
Ok I figured out the issue. Now I got it to work just fine and even boot up when I turn on my laptop. Before I had to manually go in and open it. 

In case anyone else is having problems with AWN not appearing after boot up, add it to Sessions.

---

