---
title: "Cairo not showing 3d"
date: 2008-10-27
forum: General Help
---

### Post by Caen on 2008-10-27
I'm not sure what I'm doing wrong, but Cairo won't show up as anything but 2d.  Compiz is running.

---

### Post by Caen on 2008-10-27
I take it by the lack of response I must be missing something real simple.  I've searched the forums, but I must be searching for the wrong thing.

Basically, I'm trying to achieve the table top look with my icons.  Any ideas?

---

### Post by Caen on 2008-10-27
Please help. :(

---

### Post by LouisZepher on 2008-10-28
Have you selected "3D Plane View" (Config > Views)?  If so, what do you have set for "Height of the Vanishing point" options?  The "table-top" look&feel requires the tweaking of several options through-out Cairo's option to get the right look&feel.

Hope that helps.

---

### Post by Caen on 2008-10-28
I don't have the "3D Plane View" option available.  All I have is "default" option and it's 2D.  How do I get the "3D Plane View" option?

---

### Post by LouisZepher on 2008-10-29
If there isn't already a list of other view options in the configuration applet, then I'm not sure how to help.  Maybe try reinstalling?

---

### Post by Caen on 2008-10-29
I've reinstalled multiple times.  I've even tried different versions.  Does have a 64bit installation matter?

---

### Post by LouisZepher on 2008-10-29
Weird.  Now I have the same problem, too.  One second I had my personal settings, then cairo flashed and half of my icons disappeared and I lost all but the "Default" view option.  I wasn't even doing anything with cairo when it happened.

Very odd.

---

### Post by mzkapoo on 2008-10-29
I solved it with my manual solution.

1. sudo apt-get remove cairo-dock
2. rm -R /home/<your_username>/.cairo-dock
3. sudo apt-get install cairo-dock cairo-dock-plug-ins

It will be fine.

PS. Whenever you configure it failed, let do this again.

---

### Post by doubad on 2008-10-30
I have the same problem as above.
removing cairo-dock and the .cairo-dock folder worked for about 5 seconds then it went back to the same problem.  I haven't been able to fix it since.

---

### Post by fabounet on 2008-10-30
which version are you using ?
did you activate the rendering applet ?

---

### Post by loomsen on 2008-10-30
> **mzkapoo said:**
> I solved it with my manual solution.

1. sudo apt-get remove cairo-dock
DON'T DO THIS: 2. rm -R /home/<your_username>/.cairo-dock


Files in your home directory are only configuration files. These don't affect binaries/applications files at all.

If you want to clean this place by all means, just rename the folder to .cairo-dock_bak for instance.
Otherwise it's like one step forward, two steps back.

Instead running:
```

locate cairo-dock | grep -v home | grep -v png | grep -v sng

```
will show files which DO affect how clean your environment really is. So if you purged the install, and this command still lists some files, remove them manually.

Look, the point is, UNIX is a modular multiuser OS. For instance, you share your PC with your sister. And both of you enjoy using compiz, cairo-dock and conky, but you're maybe more interested in conky showing some System Output, while your sister just wants to have some basic weather information.
--> You'd install compiz, cairo-dock and conky as SuperUser. Everything the superuser does affects any other user. So you'd both have access to compiz, cairo-dock and conky. Obv no use for multiple installations. And why? because of our beloved tilda ~, which provides the possibility for your sister and you to share ressources. 
But, pretty obv, if configurations themselves would anyhow affect the ressources of a programm, it wouldn't be a multiuser OS...
You could compare it to a car you share with your sister. The Car remains the same, no matter who actually drives it. But the way it is driven most likely differes - in speed, aggression, avg consumption etc.
Same car --> different drivers --> different outcome --> still same car.
If it wasn't like that the car would actually drive you, your sister, whoever the same way.
Or, the application would (ab)use you as its required input. 
"TerminAItor 2008 - the binary takeover" ^^


Btw, fabou, I tried and forced myself to give cairo yet another try just yesterday. But there's this one little, barely noticeable glitch, which drives me mad after one hour or two.

Let's say I have my dock located at the bottom right of my screen--- ever since, when hovering the dock, it kind of "snaps off" from which invisible border for like 5 pixels or so before initiating the actual zoom. Leaving the dock same thing. Zoom animation finishes, and as soon as the dock reaches its static position again, it snaps this 5 pixels back. This is that annoying, actually this issue prevented me from using cairo for more than 1 day.

And I'm forcing myself again and again, but I was unable to fix this ever since.
I made up it could have sth to do with the backgrounds behaviour, as I assume the background is used to specify the docks placement, right?
May I untie the icons/icons crest from the background somehow? 

I hope you get my point.

---

### Post by LouisZepher on 2008-10-30
For about a week now, I've had problems with compositing.  One week ago, I had all but the blur effects working with Compiz, and Cairo-Dock worked fine.  Over the past week, things in that vein have been failing like crazy.  Programs still run, no freezes, no crashes, nothing aside from compositing.  I know my hardware supports it, as I did have it working prior.  I can boot from my Hardy LiveCD, and compositing works.  But upon installing (including Intrepid, which I'm running now), and applying updates, the problems begin.  One of the system updates since last Monday (10/20/08) is breaking compositing.  I can't think of anything other than that which could cause these issues.

---

### Post by Caen on 2008-10-30
So how do I remove these manually?  I don't have a root password?

I'm new to linux, so please be aware of where I'm coming from.  Thanks.> **loomsen said:**
> Files in your home directory are only configuration files. These don't affect binaries/applications files at all.

If you want to clean this place by all means, just rename the folder to .cairo-dock_bak for instance.
Otherwise it's like one step forward, two steps back.

Instead running:
```

locate cairo-dock | grep -v home | grep -v png | grep -v sng

```
will show files which DO affect how clean your environment really is. So if you purged the install, and this command still lists some files, remove them manually.

Look, the point is, UNIX is a modular multiuser OS. For instance, you share your PC with your sister. And both of you enjoy using compiz, cairo-dock and conky, but you're maybe more interested in conky showing some System Output, while your sister just wants to have some basic weather information.
--> You'd install compiz, cairo-dock and conky as SuperUser. Everything the superuser does affects any other user. So you'd both have access to compiz, cairo-dock and conky. Obv no use for multiple installations. And why? because of our beloved tilda ~, which provides the possibility for your sister and you to share ressources. 
But, pretty obv, if configurations themselves would anyhow affect the ressources of a programm, it wouldn't be a multiuser OS...
You could compare it to a car you share with your sister. The Car remains the same, no matter who actually drives it. But the way it is driven most likely differes - in speed, aggression, avg consumption etc.
Same car --> different drivers --> different outcome --> still same car.
If it wasn't like that the car would actually drive you, your sister, whoever the same way.
Or, the application would (ab)use you as its required input. 
"TerminAItor 2008 - the binary takeover" ^^


Btw, fabou, I tried and forced myself to give cairo yet another try just yesterday. But there's this one little, barely noticeable glitch, which drives me mad after one hour or two.

Let's say I have my dock located at the bottom right of my screen--- ever since, when hovering the dock, it kind of "snaps off" from which invisible border for like 5 pixels or so before initiating the actual zoom. Leaving the dock same thing. Zoom animation finishes, and as soon as the dock reaches its static position again, it snaps this 5 pixels back. This is that annoying, actually this issue prevented me from using cairo for more than 1 day.

And I'm forcing myself again and again, but I was unable to fix this ever since.
I made up it could have sth to do with the backgrounds behaviour, as I assume the background is used to specify the docks placement, right?
May I untie the icons/icons crest from the background somehow? 

I hope you get my point.

---

### Post by mzkapoo on 2008-10-31
This is my howto setup ubuntu.

1. I install Ubuntu by separating 2 partitions: '/' and '/home'.
2. Whenever I feel my ubuntu failed, I always format '/' partion.
3. By the most problem, cairo-dock is not certainly stable.
4. As soon as I have already formated and installed, I would remove /home/<user>/.cairo-dock before install cairo-dock and cairo-dock-plug-ins.
5. I observe something - I don't know why it fails every time when I configured compiz and I think I should change cairo theme 1 time only. If I changed it more, it would be failed again. :confused:

@loomsen - Thank you for your advice. I understood.
@Caen - As soon as you would like to be root, you had better use 'sudo' before command.

---

### Post by Caen on 2008-10-31
Hmmm...maybe Linux just isn't for me.  I don't understand half of what is being said in this thread. :(

---

