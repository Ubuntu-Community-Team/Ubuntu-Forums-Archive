---
title: "File dependency problem?"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by holadebob on 2009-10-27
Hello everyone,

I am new to Ubuntu Jaunty and just downloaded and installed 9.0.4, 5 days ago.

I decided to transfer my fotos to Jaunty and looked up the foto manager that was on the Application list under the Graphics heading, and got it figured out and was about to load my 3000 fotos the next day. Well that was when I decided to update  the system, which I did to the tune of some 250 or so files.  

After the update, the foto manager that I was going to use disappeared with the update. 

So then I decided to install F-spot...

With the Gnome Add/Remove Applications, I tried to install f-spot and got ...

Cannot Install 'f-spot' This application conflicts with other installed software. To install 'f-spot' this conflicting software must be removed first. Switch to Synaptic Package Manager to resolve this conflict.

Then with Synaptic I got this error...

f-spot:
 Depends: libflickrnet2.1.5-cil but it is not going to be installed
 Depends: libmono-system-web2.0-cil but it is not going to be installed

The two file packages above are not installed, and I can't install them, either. I even downloaded the most up to date ones from Ubuntu site and couldn't get them loaded it. Obviously I don't comprehend what is happening. How can I delete those files if they aren't installed, and how can I install them if the system won't let me, and why (I wonder) are they on the list of available programs if I can't use them?

I am a electronics tech and have taken a few programming courses, and loved it, so please bear with me if I'm a bit slow. I really like this new Ubuntu. It is so fast and smooth - and so small (efficient?)  

My wife has put the pressure on with the fotos. She is really starting to like Jaunty, so I gotta figure this thing out. 

Thank you

---

### Post by zvacet on 2009-10-28
Go to the system>admin>software sources and check all under ubuntu software (except source) anf first two under updates tab.Reload.Try again to install desired program.Do you see in synaptic under properties witch is conflicting package?

---

### Post by wojox on 2009-10-28
Want a good photo manager download Picasa: [http://picasa.google.com/linux/](http://picasa.google.com/linux/)

---

### Post by holadebob on 2009-10-28
Thanks for checking this out - both files listed are included in the properties window. They aren't installed and I can't install them. I downloaded from ubuntu both files and tried to install them.  When I try to install libflickrnet2.1.5-cil I get Error: Cannot install 'libmono-system-web2.0-cil'  and when I try to install libmono-system-web2.0-cil I get Error: Cannot install 'libmono2.0-cil'

---

### Post by holadebob on 2009-10-28
Thanks. I will try out Picasa and compare with f-spot, but first need to resolve this dependency problem. I also tried to install another foto management application (forgot it's name) and also got same errors as I did for f-spot

---

### Post by holadebob on 2009-10-28
I decided to just remove mono and get on with my life. I intalled pthumb and it seems good for us, wish it had more features, but that's cool. Mono in español is monkey, so,  no tengo no mas monos en mi espalda, no more monkey's on my back. :) Solved - thanks for the ideas, will get back to you whenever I can help or vice versa.
Chou from Panama :)  SOLVED

---

### Post by directhex on 2009-10-28
My gut is telling me you installed "mononono", or pinned some silly things via /etc/apt/preferences, and caused your own problem.

libmono2.0 is a very simple package, containing only a few Linux-specific libraries like translation support - the only time I've ever seen anyone care about it is the "mononono" package thinks it's so terribly offensive that it inserts a package-manager-level conflict with it to prevent its installation. F-spot installs FINE on both Jaunty and Karmic (after all, it's installed by default so it *must* be fine), and the only thing which could spit out an error like yours is an intentional broken conflict

---

### Post by holadebob on 2009-10-29
Directhex, it would be much more helpful and more in the spirit of help (if that is your intention) to eliminate your gut feelings and do some research on the problem before you do your attack on my  ignorance. 
Never heard of mononomono, never saw it. Had a working system until after upgrade, didn't work after the upgrade, saw the dependency problem, asked questions. Got some help, read much on the net, learned that mono wasn't necessary to anything other than fspot and the memo pad I can't remember the name of. 
I am trying to make a go of Ubuntu because it is being so reported around the web that it is user friendly and that folks like me can use with little fuss. 
Maybe I stepped across the elitist (programmer's) line and should have stayed where ignorant folks like me are safe?

---

