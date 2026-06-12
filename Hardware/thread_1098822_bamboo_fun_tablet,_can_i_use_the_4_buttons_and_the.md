---
title: "bamboo fun tablet, can i use the 4 buttons and the touch wheel?"
date: 2009-03-17
forum: Hardware
---

### Post by Hyper Tails on 2009-03-17
hi i have vista and intrepid and yesturday i bought a bamboo fun pen tablet and i want to be able to use the 4 button and the touch senivive wheel and i need a driver for it and i installed the wacom tools in the synampic package manager and it's npt listed anywhere.
any help will be thanked.

---

### Post by Hyper Tails on 2009-03-17
......................

---

### Post by Favux on 2009-03-17
Hi Hyper Tails,

Did you check to see if Express Keys now supports the Bamboo?

---

### Post by Hyper Tails on 2009-03-17
no, not yet

---

### Post by Hyper Tails on 2009-03-19
help?

---

### Post by Favux on 2009-03-19
Hi Hyper Tails,

I can not tell from your (lack of) response whether or not you tried Wacom ExpressKeys.  This would/could be the button driver you are asking for.  Look here:

[http://freshmeat.net/projects/wacomexpresskeys/]("http://freshmeat.net/projects/wacomexpresskeys/")

---

### Post by Gemnoc on 2009-04-03
Hi Hyper Trails and Favux,

The wacomexpresskeys project Favux refers to has not been updated since June 2008, and does not mention the Bamboo Fun as supported.

But, I've been able to activate **everything** on my new Bamboo Fun small pen tablet (model #CTE-450) in Ubuntu 8.10, using a tutorial I found on Ubuntu-fr.org.

First step was the same as option B listed in the Community Wiki.

Second step was to create a script to enable the ExpressKeys:
(I'm pasting the code and translated instructions from [http://doc.ubuntu-fr.org/wacom_bamboo#pour_intrepid_ibex](http://doc.ubuntu-fr.org/wacom_bamboo#pour_intrepid_ibex))
```
gksudo gedit wacomexpresskeys
```
(shouldn't that have been **gk**sudo? anyway) [COLOR="Red"]*Edit 04-15-2009: as per Favux comment in #10, changed sudo command to gksudo[/COLOR]

Paste the following code into the newly created file:
(for a list of possible keys, enter 'xsetwacom list mod' in terminal)
```
 #!/bin/sh

case "$1" in
  start|"")
	xsetwacom set pad AbsWUp "core key -"    			# sending page up event when moving anti-clockwise 
	xsetwacom set pad AbsWDn "core key +"   			# sending  page down event when moving clockwise
	xsetwacom set pad button1 "core key CONTROL z"  	        # button <
	xsetwacom set pad button2 "core key Esc"  			# button FN1
	xsetwacom set pad button3 "core key CONTROL y"        		# button >
	xsetwacom set pad button4 "core key Enter"              	# button FN2

        ;;

  stop)
        ;;
  *)
        echo "Usage: wacomexpresskeys [start|stop]" >&2
        exit 3
        ;;
esac

```
Then copy the file and change permissions in terminal:
```
sudo cp wacomexpresskeys /etc/init.d/
cd /etc/init.d/
sudo chmod +x /etc/init.d/wacomexpresskeys
```
Afterwards, the script can be included in the boot sequence by going to System-->Preferences-->Sessions, add new program
name: Wacom Express Keys
command: /etc/init.d/wacomexpresskeys

Then reboot, and that did the trick for me. Of course, I had to configure Gimp to enable the added functions.

The eraser works, the mouse, the pad buttons, and best of all, the round "ipod clickwheel-like" trackpad acts as zoom in/zoom out in Gimp. I get all the functions the tablet has in Win XP when you install Wacom's driver. Totally cool! :)

---

### Post by higashi on 2009-04-04
Thanks so much, Gemnoc!
I have one problem though. I did all these steps, everything worked fine, but after restarting my computer, the buttons werent working again (yes, i did add Wacom Express Keys to my startup programs).
How can i fix that?

---

### Post by Gemnoc on 2009-04-05
Hi higashi,

Unfortunately, I don't know much, I just recopied here a tutorial I saw elsewhere.

Sorry I can't help you... :(

---

### Post by Favux on 2009-04-05
Hi higashi,

Check your log on start up and see if there were any problems with ExpressKeys.  Maybe a permissions problem?  Because Gemnoc is right.  I should be gksudo gedit not sudo gedit.  That can inadvertently change some permissions.

---

### Post by DuckDodgers on 2009-04-06
I'm having an interesting problem.  After I redid everyting with gk sudo everytime I press a button on my tablet my computer restarts.  Anybody have any idea why this is happening?

---

### Post by Favux on 2009-04-06
Hi DuckDodgers,

You use gksudo when using a gui program from the command line like gedit.  Otherwise it should be sudo if it is a CLI (command line interface) command like cp.  So you should not have used gksudo for every root command.

---

### Post by DuckDodgers on 2009-04-06
I'm sorry, my prevous post was missing an important comma.  What I ment was that after I redid everything with gk sudo (with the gedit command), every time I press a button on my tablet my computer restarts. I've also since discoverd that my computer restarts everytimge I use the wheel, which worked before I redid the lines in gedit.  Any Ideas?

---

### Post by Favux on 2009-04-06
Hi DuckDodgers,

Just to be sure we're on the same page you are using gksudo not gk sudo, correct?

I guess the first thing you should do is check the file wacomexpresskeys that you created.  Make very sure that the script is the same as the one posted.  If it is then in a terminal go back into the init.d directory and run the chmod command again using sudo.

Good luck!

---

### Post by Daniel Rentzsch on 2009-04-12
Hi all,

after some attempts the keys are running now.

But the pad between the extra keys still don't do anything.
I have a usual Bamboo, the black one.

I also tried it to run the commands without the script, like:

```
xsetwacom set pad AbsWUp "core key -"

```

I executed this line also with other keys.

Anyone an idea?


Thanks

---

### Post by Guruji on 2009-04-26
now that hotplug is working on jaunty, is there a way to tell it to start this script when you plug in the tablet? for now i have to start the script manually each time i plug in the tablet if i want it to work.
(btw I changed pad by "Wacom BambooFun 6x8 pad" in the script to get it to work on jaunty)

---

### Post by e.m.fields on 2009-05-31
Hey guys! 
I got my Wacom Bamboo working (with all the buttons) with Jaunty. I'm so happy!

Very easy!  

Forget the wacomexpresskeys, editing Xorg.conf, etc. unless that's easier for you. 
I did it with wacomtools - there was just a bug with using this with jaunty because the key names have been changed. 

1. Dowload wacomtools from the main repository
2. Type xinput --list.  This will give you a list of the names of the various "device names". 
3. Note the names: Look for something like "wacom bamboo pad", "wacom bamboo stylus", etc. 
4. Use xsetwacom to change device mappings. See tutorial [here.]("http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom")

You'll be basically typing something like ```
xsetwacom set pad Button2 "core key control c"

```
for example, to change the "FN1" button to "control c" (ie "Copy"). 


Should work immediately. 

Happy?

- Fields

---

### Post by Gemnoc on 2009-05-31
Hi Fields,

can you confirm that the circular touch wheel works in both directions?

I've read a lot of people say that "all buttons are working" but many people also say that the circular touch wheel works on one direction only, or not at all.

(see [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=967147&page=22"))

Thanks!

---

### Post by e.m.fields on 2009-05-31
> **Gemnoc said:**
> Hi Fields,

can you confirm that the circular touch wheel works in both directions?

I've read a lot of people say that "all buttons are working" but many people also say that the circular touch wheel works on one direction only, or not at all.

(see [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=967147&page=22"))

Thanks!
Hi - Yes, confirmed, touch-wheel scrolling works both directions. 

I am running Jaunty on AMD64, using the standard installed wacom drivers.

---

### Post by Gemnoc on 2009-05-31
Thanks!

I was waiting to install 9.04 64-Bit (right now I'm running 8.10 32-Bit). Looks like I might give it a shot!:D

---

### Post by Favux on 2009-05-31
Hi e.m.fields and Gemnoc.

If you're in Jaunty or considering Jaunty you might want to consider looking at post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

And on the next page in post #188 shatterblast shows how he configured his Bamboo.

Hope this helps.

---

### Post by Gemnoc on 2009-05-31
Thanks Favux,

I've been closely monitoring that thread as well, it's just that I've read a few people not having success and haven't built the courage yet to attempt the upgrade to 9.04. :)

---

### Post by Favux on 2009-05-31
Hi Gemnoc,

I don't blame you.  If things are working right in Intrepid why upgrade to Jaunty?  Unless there is something specific you want.  Jaunty as you can see has it's own set of problems.

As far as I know, aside from some set up problems, it has worked for everyone who's tried it so far.  And it avoids renaming things.  So when they fix the .fdi you wouldn't have to go back and rename everything.

A guy who's using Kharmic alpha 1 showed me that they do have a new wacom.fdi with a new usb subsection and they're using linuxwacom 0.8.3-2.  But he has a serial tablet pc so he doesn't know if the usb part parses things correctly.

---

### Post by Gemnoc on 2009-05-31
Hi Favux,

> I don't blame you. If things are working right in Intrepid why upgrade to Jaunty? Unless there is something specific you want.

Well for one thing I'm a sucker for novelty. :mrgreen:

I'm also thinking about upgrading my system to 4GB of RAM. The logical road would be 64-bit (even if I've read it's possible to access >3GB on 32-bit Linux). I'm trying to see if I can use Windows CAD apps in VirtualBox (as I work occasionally from home) and so far the virtualization means a big performance hit. I've discovered those apps don't support OpenGL but rather DirectX. :( Wondering if giving 2GB of RAM instead of 768MB to the WinXP VM would speed up things a bit... I would very much like to get rid of the dual-boot.

But that is way off topic. ;)

---

### Post by Favux on 2009-05-31
Hi Gemnoc,

True it's off topic but it sounds like a fun adventure that may help productivity.

As I get it the 32-bit Server version does have some memory patch that lets it use large memory like 64-bit.  And you can install the standard gnome desktop on it so that, to you the user, it's as if your in vanilla Ubuntu.

---

### Post by Gemnoc on 2009-05-31
Yeah, but I've read that you can activate that memory patch on a desktop version too. I don't remember the thread where I read this though. Even then, since my processor is an Athlon64 X2 and 64-bit systems and apps seem more mature now, I figure I might as well go for it, even if the performance gain ends up being negligible.

---

### Post by ranch hand on 2009-06-01
I don't have a wacom (yet) but I can tell you that on this box (see sig) Jaunty-64 runs like a striped ape and I haven't realy had any troubles (clean install).

I really like ext4 too.

Jump on this  sucker you will love it.

---

