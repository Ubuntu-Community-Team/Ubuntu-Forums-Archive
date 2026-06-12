---
title: "Cairo Dock, Nautilus not launching"
date: 2008-11-02
forum: General Help
---

### Post by wallenpb on 2008-11-02
I have installed Cairo Dock on Intrepid.  Everything works fine, but I cannot get the Nautilus launcher to work from the dock.  I have even tried creating a new Nautilus launcher on the desktop, which works fine, but does not work once dragged to the dock.  When clicked, it acts as if it is trying to do something, but Nautilus never opens up.  What should I be looking at on this problem to fix it?

---

### Post by wallenpb on 2008-11-03
Updated information.  I have uninstalled and reinstalled Cairo Dock and found that upon reinstallation Nautilus works.  However, it is after the next reboot of the system that it quits working.  Thought this might be significant.  Acts like there might be a file lock or something.  Any ideas?

---

### Post by wallenpb on 2008-11-03
> **wallenpb said:**
> Updated information.  I have uninstalled and reinstalled Cairo Dock and found that upon reinstallation Nautilus works.  However, it is after the next reboot of the system that it quits working.  Thought this might be significant.  Acts like there might be a file lock or something.  Any ideas?


I have also found that just removing .nautilus from my home directory produced the same results as uninstalling and reinstalling Cairo Dock.  However, under all circumstances, launching nautilus from anywhere other than Cairo Dock works perfectly every time.

---

### Post by wallenpb on 2008-11-03
> **wallenpb said:**
> I have also found that just removing .nautilus from my home directory produced the same results as uninstalling and reinstalling Cairo Dock.  However, under all circumstances, launching nautilus from anywhere other than Cairo Dock works perfectly every time.

Ok, I have discovered why it is behaving this way.  I had added Cairo Dock to my Startup Programs.  As long as I do not start Cairo Dock in this way, everything works normally, including Nautilus.  Does anyone know why putting Cairo Dock in the Startup Programs causes this problem or if there is a fix?  It would be nice to have Cairo Dock start automatically when the desktop launches.

---

### Post by santran.cedric on 2008-11-03
just add a dot at the end of the command solve the problem:
/usr/bin/nautilus --no-desktop --browser .

---

### Post by wallenpb on 2008-11-03
> **santran.cedric said:**
> just add a dot at the end of the command solve the problem:
/usr/bin/nautilus --no-desktop --browser .

Wonderful!  That worked.  Why did it work?  The dot . normally means "from this location", but what location is it running from?

Thanks very much for the assist.

---

### Post by tuwe on 2008-11-04
> **wallenpb said:**
> Wonderful!  That worked.  Why did it work?  The dot . normally means "from this location", but what location is it running from?

Thanks very much for the assist.

It is run from your home folder. You can verify this by creating a folder called test inside your home folder, then enter ```
/usr/bin/nautilus --no-desktop --browser test
``` as command to launch on click. It will open a nautilus window showing your test folder.

edit: i still wonder why it doesn't work without the dot? it should do. :confused:

---

### Post by wiljen on 2008-11-07
the dot doesn't work for me:(

---

### Post by -=Nomad=- on 2008-11-20
nautilus --no-desktop --browser .

This command did just the trick.  Funny thing how I got to this error though.  I had setup my X-Server to run two X's (one on my computer screen and one for my Sony Wega LCD tv). Although the settings used did display two signals I did not like the function so I reverted back.  Upon a normal restart (after I resolved the X settings) my launcher for nautilus in cairo was not working.  Hmmph.  

Anyways this worked for me at least.

-=Nomad=-

---

### Post by shripad_nayak on 2009-01-03
> **santran.cedric said:**
> just add a dot at the end of the command solve the problem:
/usr/bin/nautilus --no-desktop --browser .
nautilus --no-desktop --browser .

Worked for me. Thanks mate.

---

### Post by bigo72 on 2009-01-14
Fantastic! Thanks!
sudo apt-get install big-hug && sudo kiss --EveryBody

---

### Post by saultpastor on 2009-01-17
> **-=Nomad=- said:**
> nautilus --no-desktop --browser .

This command did just the trick.  Funny thing how I got to this error though.  I had setup my X-Server to run two X's (one on my computer screen and one for my Sony Wega LCD tv). Although the settings used did display two signals I did not like the function so I reverted back.  Upon a normal restart (after I resolved the X settings) my launcher for nautilus in cairo was not working.  Hmmph.  

Anyways this worked for me at least.

-=Nomad=-

Hmm, I don't know if it will help anyone but, When I switched back from two monitors to one.  Nautilus quit launching.  Adding the dot fixed it. :confused:

---

### Post by detroit/zero on 2009-01-23
I have the same problem in the Shortcuts applet. It opens fine with all my current Nautilus bookmarks, but when I try to open anything (Videos, Music, Documents, or any of the others) it opens an instance of VLC. If I open the videos or music folders, it starts playing everything in the folder from a playlist. Any other folder that doesn't have any media in it, just a blank VLC opens and sits on my desktop.

I don't see any entries in config-editor for cairo-dock. I'm not sure where you guys are talking about changing a command for Nautilus, but I don't see any option like that anywhere in cairo-dock prefences, either on simple or advanced mode.

---

### Post by fabounet on 2009-01-24
it's not a cairo-dock problem, but a Gnome one
in nautilus, right click on a folder, property, say to open them with nautilus.

---

### Post by nowhere@cox.net on 2009-02-06
Wiljen: Just a guess but make sure there is a space before the dot...

---

### Post by coolhandluke on 2009-03-08
wallenpb seeems happy that their question was answered with the command line, but I'm still stuck. Maybe someone could dumb-it-down for me?  I can see that entering the command in the terminal opens a browser, but am I supposed to be able to edit the, say, nautilus.exe file and make a similar change there?

I'm still stuck with clicking Nautilis in Cairo-dock, the icon wobbling a bit, and no browser window opening...

Cheers for any help.

---

### Post by mwadd1 on 2009-05-04
I think you are misunderstanding what he is saying. He's not telling you to type that in the command line, he's telling you to right click on the launcher, select 'Modify this launcher' and type that command in the input box next to 'Command to launch on click:'. The current command will probably be almost the same as the one being suggested - just missing the ' .' 

Mine wasn't working either, but once I modified the settings like this it has been fine since.

---

### Post by dronkit on 2009-05-08
The dot at the end worked for me as well.  Thanks :)

---

### Post by dadodadodado on 2009-05-13
great!!!! thanks!! the dot make me happy!

---

### Post by sebadov on 2010-02-18
the dot works for me to. Thanks
I wonder why this is still a problem, after a year (a simple dot!!)

---

### Post by karatedog on 2010-03-20
Internet and two years old forums rock!
The "dot" has just solved my problem.

However until recently I encountered this problem, I restarted Cairo-Dock which always solved the problem.

---

### Post by GedWarren on 2010-06-15
Thanks for the tip!

---

### Post by ubun2warrior on 2010-06-16
You can try docky. I find it much better

---

### Post by fabounet on 2010-06-16
what a useless comment ...
it would have been more relevant to say that adding the dot to the nautilus command is useful for any dock.

---

### Post by AlanR8 on 2010-06-16
Had the same issue as the OP a while ago and it did my head in for a while! Came up with this as the launch command:

> nautilus /home/username

Simples and works a treat

---

### Post by polyrhythmic on 2011-03-26
Now into 2011... and this thread is still useful!  Thanks for the solution, this has been driving me crazy -- why can't Nautilus launch itself without arguments like any other decent app?

---

### Post by sysghost on 2011-04-28
Some of you asked about why nautilus behaves like this, and I might have an explanation:

Some of you might know how Windows explorer.exe behaves:
It has a multi purpose function and works as a Desktop as well as a file manager. 



It's the same with nautilus:
It stands in both as a desktop as well as a file manager for Gnome.

Nautilus are launched, this happens:

Step 1:
> Nautilus checks if there is a previous nautilus process in "desktop mode". 
If there are no "nautilus in destop mode" found, it activates "desktop mode" and opens up the Gnome desktop.

if given the option "--no-desktop" nautilus will skip this step.

Step 2:
> If no path has been given, nautilus will now quit...
However, if the "--browser" option has been given, or a path was given:
Then it will open up in "Browser" mode. (We know it as the "Nautilus File Manager" or simply "File Manager" in Gnome)



It seems nautilus have some strange bug and won't open in browser mode, even if the "--browser" option has been given is some rare conditions. (Such as being launched from various docks and other programs)
Lucky enough, giving nautilus a path works for the time being.

More information about nautilus:
[http://linux.about.com/library/gnome/blgnome6n1.htm](http://linux.about.com/library/gnome/blgnome6n1.htm)

Also, read the "man" page:
```
man nautilus
```

---

