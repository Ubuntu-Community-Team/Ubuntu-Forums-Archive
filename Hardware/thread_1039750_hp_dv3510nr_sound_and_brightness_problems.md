---
title: "hp dv3510nr sound and brightness problems"
date: 2009-01-14
forum: Hardware
---

### Post by daniel.jimenez on 2009-01-14
I've installed Ubuntu 8.10 recently in my HP dv3510nr and almost everything worked out of the box. I'm dual booting with Windows Vista home premium.

When I first installed sound worked just fine. However, and I'm not really sure when this started happening (though maybe a kernel upgrade had something to do with it).

What happens is that the computer emits strange clacking noises instead of the sounds it's supposed to play.

I think it could have something to do with the media controls, since using the vol up or vol down basically crashes X, ctrl-alt-backspace works, but the menus and keyboard input don't.

Pressing the fn-f7 or fn-f8 triggers the brightness up-down actions, and while the screen shows an (apple-esque) icon indicating that's its being recognized, the actual brightness stays the same (very, very bright). Using nvclock I'm able to control it, so it's not a very big problem. Though it would be nice to have the keyboard combo work.

As I said, everything else works just fine and snappy.

Any help is appreciated. Sorry, but English is not my mother language, so I have a hard time explaining myself sometimes.

Edit: It appears as though booting in the past kernel doen't fix it. Any reasons why it worked and now it doesn't?

---

### Post by daniel.jimenez on 2009-01-14
i kind of figured that the kernel could be the problem.

any way I can tell for sure?

thx in advance

---

### Post by rolandixor on 2009-01-15
similar sound issue on dv7

---

### Post by esoterikest on 2009-02-10
Any progress on getting ubuntu linux, or any distribution for that matter, working perfectly on the hp dv3510nr ?  Anyone?

---

### Post by adi92 on 2009-02-22
i followed the tutorial at
[http://multidisciplinary.wordpress.com/2009/01/21/control-display-brightness-backlight-in-linux-with-nvclock/](http://multidisciplinary.wordpress.com/2009/01/21/control-display-brightness-backlight-in-linux-with-nvclock/)
to get commandline support for changing actual LCD brightness..

Edit: that tutorial helped me install two applications- nvclock and smartdimmer which let me change brightness from a console. Does anyone know how we can make ubuntu use one of them when we change the brightness using the fn keys or the brightness applet

---

### Post by leobotelho on 2009-08-27
Pretty different than Daniel, the audio in my DV3510nr does not work at all. And after I read his comments I tested the bright control, and it does not work also.
I'm giving my best to fix at least the audio issue, because it is not really nice to use without audio at all.
I have the dual boot, and everything seem work fine. 
I searched in many different forums, and I already screwed up my Linux, because I tried to use a HP dv7 solution for audio, and it changed my screen format.
I'm not a highend user of Linux, but I'm not a complete dumb. 
Could anybody help me with this problem?

---

### Post by f93mustanggt50 on 2009-10-03
Im copying this from another forum link. Did this on my DV3510nr and it works great for the sound.

[http://ubuntuforums.org/showthread.php?t=1140477&highlight=hp+laptop+no+sound]("http://ubuntuforums.org/showthread.php?t=1140477&highlight=hp+laptop+no+sound")


Ok, i had the same Problem, I'm using the same Notebook.
Everything else works fine...

Here's the solution. Maybe you have to repeat it after a kernel update or so, so make sure you bookmark this Page or save it elsewhere

Open the alsa config-file

Code:

sudo gedit /etc/modprobe.d/alsa-base.conf

Add the following line towards the end of the file. You will see other "options" entries. 

Code:

options snd-hda-intel model=hp-m4 enable_msi=1

Reboot and have fun!

---

### Post by f93mustanggt50 on 2009-10-03
Note: I'm using Ubuntu 9.04

Also for the screen brightness, I installed smartdimmer.

sudo apt-get install smartdimmer

If you run a Terminal, you can type smartdimmer -help to see your available commands.

To make a keyboard shortcut you will want to create 2 scripts first

Open a new text editor (applications, accessories, Text Editor)

Paste this to make a brightness decrease script 

#!/bin/sh
smartdimmer -d

save it as, brightdown.sh

Next, open a new Text Editor and paste this

#!/bin/sh
smartdimmer -i

save as, brightup.sh

Put both these files in your home folder

now go to System, Preferences, Keyboard Shortcuts

Click Add at the bottom

Name the first, brightdown
command= /home/USER/brightdown.sh

For the second

name = brightup
command= /home/USER/brightup.sh
 
now at the bottom of the keyboard shortcuts, you will see Custom Shortcuts

You will see the name of your new commands

click where it says Disabled and enter your keyboard combination

I made mine, CTRL and the Up arrow key for bright, and CTRL down arrow key for dimmer

Goodluck.

Also, I wanted to use my original HP brightness keys but I cant figure out how to remove their original useless function so I can use smartdimmer.

T

---

