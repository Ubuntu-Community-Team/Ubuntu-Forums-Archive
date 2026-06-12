---
title: "mp3 players"
date: 2006-02-10
forum: Installation &amp; Upgrades
---

### Post by penquin on 2006-02-10
I have a zen micro mp3 player.  does anyone know how to get it to be recognized and sync with it?

---

### Post by jpkotta on 2006-02-11
I don't have a zen, but if the zen has the budda nature, it acts like an external usb hard drive.  It should just pop up on the desktop like a USB drive then.  For synchronization, I use unison-gtk (in the repos).  But usually, I just want to copy new files from my computer to the DAP.  In that case I use rsync:
```
rsync -av --ignore-existing $HOME/music/ /media/removable/music/
```
I have my DAP mounted at /media/removable, and the way mine works is that it wants all the music files in the music/ directory.

---

### Post by penquin on 2006-02-14
It doesn't get found as an external hard drive or usb drive.  It doesn't get recognized at all.

---

### Post by Connollyir on 2006-02-14
Have you tried checking out the Ipod Howtos? To my understanding the Ipod and Zen should function exactly the same - as external hard drives (or flash memory in the case of the Zen). Also which window manager are you using? If you are using KDM then you already have a lovely media player called Amarok which just so happens to have built in support for the Ipod, easily configurable to take on the Zen (or so I would think). I also have a Zen Micro and my next project is going to be getting it to work with KDE and Amarok, in which case I will be sure to let you know how it goes.

Search the wiki and it will give you a bunch of results for the Ipod which will undoubtedly help you out.

[https://wiki.ubuntu.com//FrontPage](https://wiki.ubuntu.com//FrontPage)

Good Luck

-Ian

---

### Post by Connollyir on 2006-02-14
Also definitely check this out: [http://ubuntuforums.org/showthread.php?t=126490&highlight=zen+micro](http://ubuntuforums.org/showthread.php?t=126490&highlight=zen+micro)

It applies directly to our problems.

-Ian

---

### Post by Connollyir on 2006-02-14
Ok heres the deal:

I just got my Zen working with a program called Gnomad2...... you can find it using adept or synaptic or whatever you prefer, just make sure you have all your repositories enabled. Install it and make sure you also install the libnjb-hotplug hotplug scripts or the program won't be able to see your zen. Install everything and plug your Zen in before you start Gnomad2 and it should come right up with an interface similar to many FTP clients. If you run into issues shut down Gnomad2, unplug the Zen, Plug it back in and restart Gnomad in that order.

Post back if something goes wrong.

-Ian

---

### Post by penquin on 2006-02-15
could you explain how to do that again in non-linuxhttp://ubuntuforums.org/images/smilies/icon_confused.gif
:???:.  I am a linux neophite.  I know alot about windows but virtually nil about linux.[http://ubuntuforums.org/images/smilies/icon_cry.gif](http://ubuntuforums.org/images/smilies/icon_cry.gif)
:cry:

---

### Post by Connollyir on 2006-02-15
[QUOTE=penquin]could you explain how to do that again in non-linuxhttp://ubuntuforums.org/images/smilies/icon_confused.gif
:???:.  I am a linux neophite.  I know alot about windows but virtually nil about linux.[http://ubuntuforums.org/images/smilies/icon_cry.gif](http://ubuntuforums.org/images/smilies/icon_cry.gif)
:cry:[/QUOTE]

Its pretty simple, you will catch on really fast so don't worry.

Synaptic and Adept are front-ends for the apt-get install command at the command line. This means that they install what you want in a graphical, user friendly way. The repositories I was talking about are the lists of servers apt-get is going to look at when searching for applications to install, Ubuntu only comes with a few of these enabled by default and you have to enable the rest yourself (you are going to need to do that in order to get this program). Enabling them is as simple as going under "options" in your selected installation suite (adept/synaptic/whatever.... theres a few of them and it all goes under different names..... look around and you will find it) and adding the missing repositories in - there are howtos on the subject.

Whichever manager you choose, you need to install the Gnomad2 package and the libnjb-hotplug scripts in order for Gnomad2 to work. Just search for it and you will find it - if you don't, you spelled it wrong or you don't have all your repositories enabled.

After everything is installed and kosher, plug in the Zen, start Gnomad, and everything should work. 

if it doesn't shut down Gnomad FIRST, then unplug the Zen....... if you don't follow that order bad things will happen.

If you have problems let me know.

-Ian

---

### Post by penquin on 2006-02-16
Thank you it worked on the liveCD now I might be ready to join the ubuntu community full time, but do you know if kodak has an app so I can download from my camera?  If it can do everything winxp can I will make the change permiment.

---

### Post by Connollyir on 2006-02-16
[QUOTE=penquin]Thank you it worked on the liveCD now I might be ready to join the ubuntu community full time, but do you know if kodak has an app so I can download from my camera?  If it can do everything winxp can I will make the change permiment.[/QUOTE]

I haven't found anything that I wanted to use which was unsupported....... and I've used a WIDE range of devices. Ubuntu is pretty good about stuff like that. There are some random issues like certain pci modems are *generally* not supported (or so I hear) and I just learned that there is a problem with the ndiswrapper program in the 64 bit kernel, but these are few and far between. 

It has been my experience that Linux (I used Gentoo before this and now I use Kubuntu) has the ability to do just about everything windows can do, and in some cases do it better. You do have to understand though, that most drivers written for Linux are made by independant programmers, although some manufacturers (like Nvidia, for example) make commercial drivers. What this means to you is that often newer devices may not have drivers out for them or the drivers are a little flaky, and sometimes drivers and programs may not be as stable as their windows counterparts. Most of the time you can make them work anyway, and as I said earlier, Ubuntu will do almost everything Windows will do and sometimes do it better.

You will also really have to work at it if you want to get games to run as well on Linux - there are older games that work but if you want to play Quake 4, good luck. I don't know much about it beyond that, I haven't tried it, its not what I'm here for.

I like Ubuntu and I'm very glad I switched. I keep a Windows disk in my box in case I want to do some gaming or something but I use Linux for everything else. I have found it to be WAY WAY WAY more configurable, secure (no spyware and few viruses), and definitely more fun than Windows. In response to your question, I'm sure you could find something that will work with your camera, though nothing comes to my mind immediately (I don't have a digital camera though). Use the resources and search around. I mean you could even write your own program for it if you had experience with python or some other language - the options are just about endless.

Its a long winded response but I think it should give you a good Idea of what you are getting yourself into.


-Ian

---

