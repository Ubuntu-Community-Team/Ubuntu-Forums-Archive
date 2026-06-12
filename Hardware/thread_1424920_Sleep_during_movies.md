---
title: "Sleep during movies"
date: 2010-03-08
forum: Hardware
---

### Post by deez on 2010-03-08
Hello.  First off, I want to say thanks to everyone who makes the Ubuntu project possible.  It's my distribution of choice at the moment--I find it pleasurable most of the time.  And now onto the debugging...

I'm runing 9.10 64 on a Toshiba Satellite 64.  Everything worked out of the box save for the battery icon.  As a workaround, I unloaded gnome-power-manager and use kpowersave instead.  It's only a minor hiccup most of the time.  Invariably though, my screen will black out during times of perceived dormacy, during movies.  I've turned off known options for putting the monitor to sleep in kpowersave, yet she sleeps during movies.  Any ideas what's going on?  Any fix on getting gnome-power-manager running smoothly? 

Merci

Deez

---

### Post by chaanakya_chiraag on 2010-03-08
What exactly happens with gnome-power-manager?  Does it not show you the battery icon?  I would suggest you use another system monitor like conky to monitor battery usage.  That way, gnome-power-manager will manage the screen dimming and such (which, from your post, seems to work fine??) and you will also know how much battery life you have left.

---

### Post by deez on 2010-03-09
Gnome power manager always registers the computer plugged in and charging.  I"ll have a look at 'conky'.  Any other ideas?

---

### Post by Fafler on 2010-03-09
Theres a applet for gnome called Inhibit Applet. Just click it and the computer wont go into power saving for any reason. Click it again and it's back to normal. Have you tried that?

---

### Post by deez on 2010-03-09
No, I haven't tried that, I'll check it out.  Also about gnome power manager, it goes beyond always registering plugged into AC power.  IN the power manager, there's no tab for 'battery' options.  I can change the options for when its under AC power, but not when it's under batter power.  That tab does not exist.

---

### Post by chaanakya_chiraag on 2010-03-09
Hmmm...it looks like gnome-power-manager isn't registering the existence of your battery!!  Btw, for conky, you will need to configure it to show your battery remaining.  I'll post my conky config later so that you can see if it's just a gnome-power-manager issue or something more than that.  Also, I am assuming kpowersave *does* show your battery remaining?

---

### Post by deez on 2010-03-09
Yeah, it does show my battery remaining.  I think this is a known issue with gnome power manager

Cheers

DZ

---

### Post by deez on 2010-03-09
So i loaded conky and it conks my computer out.  That's an exaggeration, but I do have to run a terminal command to get it up and running and then that's it.  Clicking on it, right clickin on it, none of these does anything, no options, no configurations, nada!

---

### Post by chaanakya_chiraag on 2010-03-09
Yes, Conky does not interact with the mouse. You have to configure it with a text file called .conkyrc

---

### Post by deez on 2010-03-10
OK, where do i find this file?  Is conky always visible on the desktop?

Cheers

DEEZ

---

### Post by Fafler on 2010-03-10
Configuration files starting with . are almost always placed in your home directory. Just open a terminal and ```
nano .conkyrc
``` Google for a template if the file isn't present already.

---

### Post by Objekt on 2010-03-10
I had a similar problem on my desktop machine.  When we watched movies, the screensaver would kick in, as no one was moving the mouse or using the keyboard.

There's a handy little app called Caffeine, designed specifically to solve this problem.  Here's the project homepage: [https://launchpad.net/caffeine]("https://launchpad.net/caffeine")

Caffeine loads when you log in, and will prevent your screensaver and powersaving modes from activating while a designated program is running.  For example, I have Caffeine active any time I have VLC Media Player open, as I use VLC to watch movies.

You can add the ppa to your software sources, according to the instructions on that page, & then install it from the command line (sudo apt-get install caffeine).  Or, you can download the .tar.gz archive, unpack it, and install from the .deb file (possibly easier, less command line stuff to do).

---

### Post by Kendustin on 2010-05-08
I was having the similar issue and when I clicked on the desktop my conky disappeared from the genome but then I came to know that my conky was minimized .To solve this problem I changed window type normal to window type override and then  everything was working fine.

---

