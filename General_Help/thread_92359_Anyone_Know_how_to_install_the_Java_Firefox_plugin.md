---
title: "Anyone Know how to install the Java Firefox plugin for Breezy."
date: 2005-11-19
forum: General Help
---

### Post by rlong26 on 2005-11-19
I am able to down load the self up packing package from sun but after I "./" it Firefox still asks to the plugin.  Any body know how to get this to work? I really need the Java runtime environment for work.(*,)

---

### Post by cstudent on 2005-11-19
If you are running a x86 pc I would highly recommend using a script called Automatix. It will make the job a whole lot easier.

You can find it here:

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

Bill

---

### Post by gapplewagen on 2005-11-19
I used the default Breezy repositories to install it and it works just fine with Firefox with no work on my end.  

System --> Administration --> Add Applications

Just search for java and install "Java Web Start 1.4"

---

### Post by cstudent on 2005-11-19
[QUOTE=gapplewagen]I used the default Breezy repositories to install it and it works just fine with Firefox with no work on my end.  

System --> Administration --> Add Applications

Just search for java and install "Java Web Start 1.4"[/QUOTE]


That won't be the Sun version.

---

### Post by Trab on 2005-11-19
[QUOTE=cstudent]That won't be the Sun version.[/QUOTE]
you dont need the sun version.
its really just easier to get the blackhawk 1.4 version, the only thing that doesnt work well with it (or at all, at least for me) is Azureus.... but other programs like limewire, and any online java programs ive come across work fine with it.

good luck!

---

### Post by gapplewagen on 2005-11-19
[QUOTE=Trab]you dont need the sun version.
its really just easier to get the blackhawk 1.4 version, the only thing that doesnt work well with it (or at all, at least for me) is Azureus.... but other programs like limewire, and any online java programs ive come across work fine with it.
[/QUOTE]

I have had the same results.  Nothing could be easier.

---

### Post by Sebby on 2005-11-19
Try this:

[http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre)

---

### Post by Trab on 2005-11-19
[QUOTE=Sebby]Try this:

[http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre)[/QUOTE]
no, dont, its outdated, sorry...
trust me, i tried that before... man did i have some serious java issues for a while there...
just use the blackhawk version, their is almost no excuse not to :-P

---

### Post by Sebby on 2005-11-19
[QUOTE=Trab]no, dont, its outdated, sorry...
trust me, i tried that before... man did i have some serious java issues for a while there...
just use the blackhawk version, their is almost no excuse not to :-P[/QUOTE]
Woops. :???: 

In what way is it outdated?

---

### Post by cstudent on 2005-11-19
[QUOTE=Trab]you dont need the sun version.
its really just easier to get the blackhawk 1.4 version, the only thing that doesnt work well with it (or at all, at least for me) is Azureus.... but other programs like limewire, and any online java programs ive come across work fine with it.

good luck![/QUOTE]

The original poster stated they were trying to install the Sun version. There are some software that will work better with the Sun version. Eclipse is a good example. Running Automatix is no harder than installing from Synaptic and once ran, all software will be updated through Synaptic.

I'm not trying to start a flame war. I just think that the poster would be happier in the long run going with Automatix and the Sun version.

Bill

---

### Post by Trab on 2005-11-19
[QUOTE=cstudent] Running Automatix is no harder than installing from Synaptic and once ran, all software will be updated through Synaptic.

I'm not trying to start a flame war. I just think that the poster would be happier in the long run going with Automatix and the Sun version.
[/QUOTE]
ah, sorry i didnt realize he WANTED the sun version, not many know its not the only option...
automatix did work for me eventually, but it had alot of loose ends...im much happier with the blackhawk version thats fully supported...
ubuntuguide.org was writen 6 months ago for Hoary, and while most things still work, the java does not. the file is no longer funtional...
if he wants the sun version, then automatix is the way to go.
if he doesnt care and just wants almost funtional java (for anything ive needed it for) i would suggest the blackhawk version.

i think rlong26 gets the idea:
either get automatix for the sun version (found here 
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563))
or
```

sudo apt-get update
sudo apt-get install j2re1.4
sudo apt-get install j2re.14-mozilla-pluggin

```

cheers and good luck!

---

### Post by cstudent on 2005-11-19
[QUOTE=Trab]ah, sorry i didnt realize he WANTED the sun version, not many know its not the only option...
automatix did work for me eventually, but it had alot of loose ends...im much happier with the blackhawk version thats fully supported...
ubuntuguide.org was writen 6 months ago for Hoary, and while most things still work, the java does not. the file is no longer funtional...
if he wants the sun version, then automatix is the way to go.
if he doesnt care and just wants almost funtional java (for anything ive needed it for) i would suggest the blackhawk version.

cheers and good luck![/QUOTE]

Agreed. Arnie was going through some rough spots with some repositories for Automatix, but I think he has things ironed out now. I'm quite happy with his lastest version.

Later!

---

### Post by StratosL on 2005-11-19
I tried the guide for restricted formats (search by title in wiki)

[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29)

and it worked beautifully for sun-java 1.5.0_05

---

