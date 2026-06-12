---
title: "No application is registered as handling this file error Intrepid 8.10"
date: 2008-11-12
forum: General Help
---

### Post by ToastyMallows on 2008-11-12
Just burned a Intrepid 8.10 iso, checked the disc for errors (there were none) and then installed the OS.

After installing a couple of programs from the Add/Remove programs menu, I encountered this error while saving an openoffice document:
```

Could not open location 'file:///home/ross'
No application is registered as handling this file
```

As I pondered this problem I went to **Places>Desktop** and it still gave me the same error.  I have also plugged in my flashdrive and nothing pops up.  I can't access any folder under the **Places** menu without getting this error.

Is it a program that I need to install?  Or something under the Synaptic Package Manager that needs to be installed?  Please help it's driving me crazy.  I looked under the current bugs and workarounds and this was not one of them.

Another problem that I have is no sound.  I really don't know how this one happened at all.  When I test the sound nothing works.

---

### Post by plucky on 2008-11-13
> I looked under the current bugs and workarounds and this was not one of them.


See Post #20 or click on link below.

This [link](http://ubuntuforums.org/showpost.php?p=6102124&postcount=20) might help.Usually it tries to open folders with some other applicatiion.


Good Luck

---

### Post by ToastyMallows on 2008-11-13
That did not do that trick but from reading the posts I found out about Nautilus, and that made me figure out that it wasn't installed under the Synaptic Package Manager, which I found odd.

I still have a problem with no sound though, what should I serach under the Package Manager I can't seem to find anything.

---

### Post by ToastyMallows on 2008-11-15
Bump, still need audio help.

---

### Post by darkazurka on 2008-11-23
Have you solved your other problem? I had the same problem as you.

On the audio side problem, I get strange sounds, and I bet all my previous audio settings have been reconfigured. I remember reading up a lot on the audio system in the past.

ALSA vs. OSS usually... (the audio war?) :confused:

---

### Post by briealeida on 2009-02-24
I had the same problem and was able to resolve it by 'sudo apt-get install nautilus'.

---

### Post by nineacres on 2009-05-01
Many thanks for that - I had same problem in Jaunty and sudo apt-get install nautilus solved the problem for me.

---

### Post by AnthraxMouthwash on 2009-05-06
Thanks.

I have been having this same problem.

For me, it only started after updating to Jaunty.

---

### Post by oOarthurOo on 2009-05-19
Just encountered the same problem, however, for me nautilus was already installed, it had simply forgotten how to use it.

Hit alt+f2, then type nautilus
When it opens, right-click on a folder and choose open with...
Browse for an app, scroll down till you get to nautilus then choose ok.
Close nautilus and try again. Should work ok now.

Not sure what causes it to suddenly forget its associations. All I was doing prior to this problem was customizing the menu.

---

### Post by minj on 2009-08-30
> **oOarthurOo said:**
> Just encountered the same problem, however, for me nautilus was already installed, it had simply forgotten how to use it.

Hit alt+f2, then type nautilus
When it opens, right-click on a folder and choose open with...
Browse for an app, scroll down till you get to nautilus then choose ok.
Close nautilus and try again. Should work ok now.

Not sure what causes it to suddenly forget its associations. All I was doing prior to this problem was customizing the menu.

lol thanks for the tip. EXACTLY the same prob here

---

### Post by vishnu.patel on 2009-09-01
I tried
Hit alt+f2, then type nautilus
When it opens, right-click on a folder, But in my case there is no any option of open with...

At right-click on a folder, i have one disabled option +Add Bookmarks and two check boxes show hidden files and show size column.

With nautilus i can open folder but i can't open folder directly places->> Documents tabs etc.

i don't know how i can solve his.


--Vishnu

---

### Post by vishnu.patel on 2009-09-02
> **oOarthurOo said:**
> Just encountered the same problem, however, for me nautilus was already installed, it had simply forgotten how to use it.

Hit alt+f2, then type nautilus
When it opens, right-click on a folder and choose open with...
Browse for an app, scroll down till you get to nautilus then choose ok.
Close nautilus and try again. Should work ok now.

Not sure what causes it to suddenly forget its associations. All I was doing prior to this problem was customizing the menu.


This is not worked with me can you please suggest some thing else

---

### Post by Simon Cropper on 2010-05-25
Hi,

the same problem occurred for me and was solved using the above technique (with minor modifications). The cause was removing the 'nautilus' icon from the system menu. Obviously this list also doubles as a file association register, as when you choose 'Open with...' this is the list that appears.

I cleaned up my list because I had multiple file icons appearing in this list (regardless of whether they are ticked or not ) so I went mad and removed those icons I thought I would not use. As nautilus opens whenever I click on a folder I removed the icon from the menu -- this is when the problem occurred.

Following the above instructions you can reinstate the association, except type nautilus under 'Use a custom command' rather than pick an icon (in my case I removed icon).

Simon

---

### Post by Fluffgar on 2010-10-20
> **oOarthurOo said:**
> Just encountered the same problem, however, for me nautilus was already installed, it had simply forgotten how to use it.

Hit alt+f2, then type nautilus
When it opens, right-click on a folder and choose open with...
Browse for an app, scroll down till you get to nautilus then choose ok.
Close nautilus and try again. Should work ok now.

Not sure what causes it to suddenly forget its associations. All I was doing prior to this problem was customizing the menu.

Thanks this worked. 

I submitted what I did at: 
[http://ww.ubuntuforums.org/showpost.php?p=10000023&postcount=20](http://ww.ubuntuforums.org/showpost.php?p=10000023&postcount=20)

---

### Post by Mike_tn on 2010-10-27
> **oOarthurOo said:**
> Hit alt+f2, then type nautilus
When it opens, right-click on a folder and choose open with...
Browse for an app, scroll down till you get to nautilus then choose ok.
Close nautilus and try again. Should work ok now.


Thanks so much! Apparently it's still a problem almost two years later.
Happened when I was re-arranging the Main Menu items, same as you.
Makes your wallpaper disappear too. I'm running Lucid i386 on a Dell laptop
MSWindows also has problems like that with file associations getting forgotten or mixed up.

---

### Post by Mike_tn on 2010-11-01
[FONT=Verdana][SIZE=2]> **Simon Cropper said:**
> 
Following the above instructions you can reinstate the association, except type nautilus under 'Use a custom command' rather than pick an icon (in my case I removed icon).
Simon

There is another way you can fix the bug yourself, it may be more permanent because you won't run the chance of accidentally deleting your association created by a main menu icon. Likely this can be improved, but it works:

This assumes nautilus is installed but just doesn't turn on at boot time.[/SIZE][/FONT][SIZE=2] 
It assumes nautilus is located in the folders *usr > bin*. I run Lucid 10.04
Search your file system with the term *nautilus* if needed.

Open gedit or right click the desktop, make an empty file, 
type this in:

[COLOR=Blue]#!/bin/sh[/COLOR][/SIZE][SIZE=2][COLOR=Blue]
/usr/bin/nautilus[/COLOR]

Save it. The title matters. [/SIZE][SIZE=2]The title cannot have any spaces.[/SIZE]
[SIZE=2]   I titled it "Nautilus_Startup" no quotes.[/SIZE][SIZE=2]

Use the terminal to open a root folder (in Gnome) with this command:[/SIZE] [SIZE=2]

**gksudo nautilus**[/SIZE]    [SIZE=2]

It will ask for your password.
  Navigate from "File System" in the browser that just opened to your /etc/init.d folder[/SIZE] [SIZE=2]
  Copy (drag drop) "Nautilus_Startup" into your /etc/init.d folder

 Open another terminal as root user.[/SIZE] [SIZE=2]Type:

**sudo -s**[/SIZE]    [SIZE=2]

Hit enter and it will ask for your password:
  [sudo] password for your_user_name: {put in password}

[/SIZE][SIZE=2]Make "Nautilus_Startup" an executable text file in your new root terminal, type:

[/SIZE][SIZE=2] **chmod +x /etc/init.d/Nautilus_Startup**[/SIZE][SIZE=2]

  Note: Where it says "Nautilus_Startup" above, put in your title instead if different.[/SIZE] [SIZE=2]
  Hit enter. You are done with script file set up.

Go to the *System* dropdown in the desktop panel's launcher.[/SIZE][SIZE=2]
Find *Startup Applications*. Open it. On the *Startup Programs* tab click the *Add* button.  Put in the title you like and for the command use the directory to your new script. 

In my example the startup command would be [/SIZE] [SIZE=2]**/etc/init.d/Nautilus_Startup**
  Click *Add* and *Close* and your are done![FONT=Verdana]

_Extra_
You can use the basic idea here, beginning with a basic text file, to run anything you like at startup or to instead run anything on demand  from the main menu. To add something to the main menu, click the main menu icon to open it or right click the panel's launcher and choose *edit menus*. Add an application's or script's directory into it. To do this first choose your menu; *Applications, System, Preferences or Administration*, then click the *+New Item* button. You are creating an item similar to the *Startup Applications*. Easiest to add are applications already existing such as Firefox. You type in Firefox for both the name and command, done. But that won't run Firefox on startup, only on demand with the button.  Or maybe you installed a new application manually and you'd like to include it. Put its directory in as the *New Item's* command.  Click the boingy launcher icon to pick your own icon too. Another possibility is running terminal commands on demand via your *New Item's* button by putting the desired terminal command line into a script just like we installed above. For terminal commands, when you type the directory into the *New Item's* dialog box, type [COLOR=Blue]gksu[/COLOR] followed by a space and then the directory location of the script. 
[/FONT][/SIZE]

---

### Post by landennick on 2011-01-21
Banshee did this to me in Maverick 10.10 to me.  I installed Banshee using software centre and it took over from nautilus.  The work around of running nautilus with run Application worked for me but this bug is still going strong.  But I guess it's rare?

---

### Post by servant74 on 2011-02-18
Same solution worked in 10.04 (finger checked in the title).  

Alt-F2, then start nautilus.
Choose a directory
Add /usr/bin/nautilus as the command to open it.

thanks to all who assisted...:popcorn:

---

