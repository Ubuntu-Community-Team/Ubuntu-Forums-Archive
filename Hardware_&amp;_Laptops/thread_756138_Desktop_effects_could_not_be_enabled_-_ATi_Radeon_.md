---
title: "Desktop effects could not be enabled - ATi Radeon Xpress 1100 - Compiz"
date: 2008-04-15
forum: Hardware &amp; Laptops
---

### Post by ithinkthereforeiam on 2008-04-15
Fresh Install of Ubuntu 7.10 and all updates on ext3 file system. Then I followed this url .. 

//news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml"]

to install Compiz Fusion.

When it came to using it, I got the 'Desktop effects could not be enabled' msg. 

This was the response from Terminal when I typed in 'compiz' to attempt to check out why.

----------------------------------------

harrie@mumserver:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5975 (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (in brackets) 2048: Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.

-----------------------------------------

I apologize now if I have duped this error, I have seen a few posts on here but nothing that I could make any real sense of. Will someone who knows what the above means, let me know, cos right now, all I know is that it does not look good!

I really would appreciate any help.

regards

---

### Post by jocko on 2008-04-15
If you, as you say, have gutsy (7.10) installed, you should NOT use that OLD guide. If you read on the page it says it's for feisty (7.04), and as feisty had a different version of xorg it is very likely that those packages will not work in gutsy..
Compiz fusion is already available in the standard gutsy repos and as far as I remember, it's installed by default (but probably not activated).
I suggest you first uninstall everything you installed from that guide, inactivate treviños repo and reinstall compiz and compiz-fusion from the standard repo, and see if you get it working.

Note that you first need to set up your graphics driver properly, otherwise you'll get an error similar to the one you got...

---

### Post by ithinkthereforeiam on 2008-04-15
Hi Jocko,

Firstly, thank you for replying, I do appreciate the assistance.  Im a newbie so forgive my ignorance, but how do i inactivate treviños repo and reinstall compiz and compiz-fusion from the standard repo?

---

### Post by jocko on 2008-04-16
> **ithinkthereforeiam said:**
> Hi Jocko,

Firstly, thank you for replying, I do appreciate the assistance.  Im a newbie so forgive my ignorance, but how do i inactivate treviños repo and reinstall compiz and compiz-fusion from the standard repo?

donna

To remove treviños repo: go to System --> Administration --> Software Sources, click on the second tab (Third-Party Software), and look for these two lines[FONT=monospace]:
[/FONT]```
http://download.tuxfamily.org/3v1deb feisty eyecandy
http://download.tuxfamily.org/3v1deb feisty eyecandy (Source Code)
```
Select them and click "Remove". Click the first tab, and make sure the first four tick boxes are activated (the lines ending with "(main)", "(universe)", "(restricted)" and "(multiverse)"). 

Close the Software Sources application.

Then open up Synaptics (System --> Administration --> Synaptic Package Manager), click the "Reload"[COLOR=#6C7AA1][/COLOR] button.
Click the "status" button in the lower left corner, and then select the category "Installed (Local or depracated)" (I translated this from swedish, so I'm not sure this is the exact line you see).
Now you should see a list of all things you have installed from somewhere else than the active repos, and as you removed treviños repo, all your installed compiz related things should be here.
Select every package with either "compiz", "emerald"or "libdecoration" in their name, right click and select "Mark for Complete Removal". Click Apply to start the uninstall. Leave synaptic open.

To install from the standard repos: Use synaptic's search function to find packages with "compiz" in their names.
Install these:
```
compiz
compiz-gnome
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compizconfig-settings-manager
```
That's it.


[COLOR=#6C7AA1][/COLOR]

---

### Post by ithinkthereforeiam on 2008-04-16
:popcorn::guitar::KS:

[SIZE="5"]OMG IT WORKED!!!!!!![/SIZE]


Thank you, Thank you, Thank you Jocko, you are fantastic!!!..  It happened that I had already followed this link [http://wiki.archlinux.org/index.php/Xgl]("http://wiki.archlinux.org/index.php/Xgl") Method 1 which I got from another post on here to sort display, and then following your instructions did the trick! I am so going to learn alot from this forum and hopefully in time, give something back.  Thanks everso..   Im going to go and play now.. Thanks again!

kind regards

---

### Post by ithinkthereforeiam on 2008-04-16
Im hyperventilating.. I can't take the excitement!  However, right now I can only do 

ALT+TAB	           Window switch
SUPER+TAB	 Flip switcher or ring switcher depending on which is enabled.
CTRL+ALT+D      Show desktop
ALT+F7	            Initiate 'move windows'
SHIFT+ALT+UP   Initiate window picker 

I can't do these:

SUPER+SHIFT+DRAG LEFT MOUSE	Draw fire 	
SUPER+SHIFT+C	                           Clear fire 
CTRL+ALT+DRAG LEFT MOUSE	   Rotate cube
CTRL+ALT+LEFT ARROW	               Rotate cube
CTRL+ALT+DOWN ARROW	             Flat desktop
CTRL+ALT+DOWN	                          Unfold cube 

SUPER+G	Group Windows - hold the super button then select the windows you want to group and then hit Super+G 	

I would really really love to do the cube.   Currently, the wizard doesn't let  me edit the effects?  Am I meant to allow the desktop settings to previous temporarily to allow me access to the effects so that I can choose the ones I want?

regards

---

### Post by jocko on 2008-04-16
I'm glad I could help!

When you say "the wizard doesn't let" you edit the effects, what do you mean?
Do you mean you can't find the options to activate the plugins in CCSM (System --> Settings --> CompizConfig Settings Manager)?
Or do you mean CCSM gives you an error message that the plugin can't be activated?

---

### Post by ithinkthereforeiam on 2008-04-16
Hi Jocko, 

I have got myself so carried away with compiz I haven't even taken a breather to come back and post my success in activating ccsm package and being able to customise.  I enabled all cube effects and gave myself two desktops.  I can see the cube and turn it now, woooo hoooo!  I just have to remember the shortcuts.  In all my years of working on computers, I don't think I have ever had so much fun on a pc, it has always been work, work work..  Thank you sooooo much.  When my Euphoria has calmed down, do you think it is worth me detailing the process including your contribution and those of others with relevant links for the benefit of others on here, or has that been done already for an Acer 5100 with ATI Radeon Xpress 1100?

Also, how does one formerly Thank helpers on here or does the forum just count all messages that have the words Thank you in them related to a member?

kindest regards

---

### Post by jocko on 2008-04-16
To thank people, there is that little star in the lower right corner of each post.

I don't know if it's needed to make any specific guide for your specific computer, I guess most thing are covered in the forums already, if you know what to search for. But of course if you think it will help people, and have the time to spare, then go for it...

---

