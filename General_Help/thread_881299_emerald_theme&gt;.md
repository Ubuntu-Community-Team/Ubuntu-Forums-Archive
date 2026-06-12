---
title: "emerald theme&gt; ??"
date: 2008-08-05
forum: General Help
---

### Post by oneouncebrick on 2008-08-05
hey! i was wondering how to install Emerald themes... i download them from gnome-look and then i cant open them with archive manager to drag them into my themes...? could someone help me with this lol.. :confused:

---

### Post by overdrank on 2008-08-05
> **oneouncebrick said:**
> hey! i was wondering how to install Emerald themes... i download them from gnome-look and then i cant open them with archive manager to drag them into my themes...? could someone help me with this lol.. :confused:

Hi and you will need to import them with emerald manager. I assume you are using compiz also.

---

### Post by tuxxy on 2008-08-05
Move/Drag you newly download theme folder into **/home/username/.emerald/themes**

Now it should appear in you theme list in emerald once you reload it.

---

### Post by oneouncebrick on 2008-08-05
ok sounds good... umm i dont know if i have compiz? i have hardy heron... O_o lol and how do i drag them into /home/username/.emerald/themes/

---

### Post by tuxxy on 2008-08-05
Places > home folder and navigate to **/home/username/.emerald/themes**

Compiz are you desktop effects

---

### Post by OutOfReach on 2008-08-05
Compiz is installed by default in Hardy Heron.

---

### Post by overdrank on 2008-08-05
> **oneouncebrick said:**
> ok sounds good... umm i dont know if i have compiz? i have hardy heron... O_o lol and how do i drag them into /home/username/.emerald/themes/

What I meant was if you are not using compiz (desktop effects) then you can not use emerald. See the FAQ's link in my signature.

---

### Post by oneouncebrick on 2008-08-05
ok i know how to get to my home > user name folder.. .will i have ot create a ".emerald" themes folder and a themes folder?

---

### Post by hotrod6657 on 2008-08-05
if you download the themes to your desktop, open emerald and click import.  Select your theme from the desktop and it should install it.  It will show up somewhere on that list.

That's another option that works for me.

---

### Post by hotrod6657 on 2008-08-05
the "." means that the folder is hidden.  It should be there if you have emerald installed, you just have to hit ctrl + h to show the hidden directories.

---

### Post by OutOfReach on 2008-08-05
Do you have emerald installed?

---

### Post by oneouncebrick on 2008-08-05
so i download the emerald theme, save it to my desktop... and open it in archive manager? then import it to emerald? ??? umm im confused  i dont even know if i have a .emeralds folder or how to import things into it i go with tar.gz things that i can simply dragg in.. lol this is new for me.

---

### Post by OutOfReach on 2008-08-05
Seems a little odd that you don't have an .emerald directory.
Do you have emerald installed?
If not type this into the terminal (Applications>Accessories>Terminal)
```
sudo apt-get install emerald
```

---

### Post by oneouncebrick on 2008-08-05
ok lenme do that.

---

### Post by oneouncebrick on 2008-08-05
ok emerald is installed... now what?

---

### Post by OutOfReach on 2008-08-05
Ok now type this into the terminal:
```
sudo apt-get install fusion-icon
```

---

### Post by oneouncebrick on 2008-08-05
ok.. done

---

### Post by oneouncebrick on 2008-08-05
so, now what? lol

---

### Post by overdrank on 2008-08-05
Moved to  Desktop Effects & Customization

---

### Post by tuxxy on 2008-08-05
YOu wont be ablle to see the .theme folder as it is hidden youneed to muanlly type that dir into your nautilus file browser.  Theres an option at the top left to ebnable you to type in rather than click.

```
/home/username/.emerald/themes 
```

If you can open a terminal you could move the file like this

```
sudo mv /home/username/Desktop/theme-name /home/username/.emerald/themes
```

Now just open emerald and select the new theme

---

### Post by oneouncebrick on 2008-08-05
ok. so say i download the vista aero theme... i just download it to my desktop, and without opening it just type in the name of it? and baisically plug it into the what you said?... right?

---

### Post by OutOfReach on 2008-08-05
Now goto System>Preferences>Emerald Theme Manager.
Click on the 'Import' button, A file dialog will come up go to where you saved the emerald theme you downloaded, select it, and click Ok, It should appear in the list.
Now keep the Emerald Theme Manager open and goto Applications>System Tools>Compiz Fusion Icon. A blue icon thing will come up in the notification area (See the picture attachment). Right click on that, a drop down menu will appear, in the drop down menu, goto Select Window Decerator and click on Emerald. Now go back into the Emerald Theme Manager, and select your theme that you imported from the list.

---

### Post by oneouncebrick on 2008-08-05
can i just import the theme directly off my desktop after i download it ??? import.. then browse for it??

---

### Post by OutOfReach on 2008-08-05
Yes you can.

---

### Post by oneouncebrick on 2008-08-05
OK i did everything you said.. now how do i select it off of the emerald themes manager interface as my theme for my windows! lol  in other words.. how do i make it work..

---

### Post by hotrod6657 on 2008-08-05
you should be able to import it through emerald.

If you have a file saved on your desktop open emerald and on the right side hit import, navigate to the directory it's in (just click desktop on the left and click the file) and click open.  That should install it.  Make sure that you do follow the steps outlined by outofreach though so that emerald is used as your theme manager.

---

### Post by OutOfReach on 2008-08-05
Did you goto Applications>System Tools>Compiz Fusion Icon and right click on the blue icon (See my other post above with the picture) and select Select Window Decorator, and select Emerald?

---

### Post by hotrod6657 on 2008-08-05
> **OutOfReach said:**
> Now goto System>Preferences>Emerald Theme Manager.
Click on the 'Import' button, A file dialog will come up go to where you saved the emerald theme you downloaded, select it, and click Ok, It should appear in the list.
Now keep the Emerald Theme Manager open and goto Applications>System Tools>Compiz Fusion Icon. A blue icon thing will come up in the notification area (See the picture attachment). Right click on that, a drop down menu will appear, in the drop down menu, goto Select Window Decerator and click on Emerald. Now go back into the Emerald Theme Manager, and select your theme that you imported from the list.

If you did that then it should be all set.  That should make emerald your theme manager.  To see your new theme for the first time you might have to type:  ```
emerald --replace
``` to get it to switch for you.  After the first time you shouldn't have to do that part again.

hotrod

---

### Post by oneouncebrick on 2008-08-05
ok, so now i located it and browsed it from the "themes" interface ( right click > change desktop> themes) and then i clicked install... so i browsed into the emerald folder and selected my theme... ckicked on it and nothing happened.. so i tryed dragging it in and it said invalid theme?

---

### Post by hotrod6657 on 2008-08-05
If you mean just how do you select it you just have to find it on the list in emerald and select it.  Just click on it.  The replace command should make the screen change and display your new theme.

---

### Post by hotrod6657 on 2008-08-05
what is the file extension of the theme you're trying to use?

---

### Post by oneouncebrick on 2008-08-05
oh, ok lol.. so now its taking a wile.. lol its stuck on " reloading..." in my ter minal

---

### Post by oneouncebrick on 2008-08-05
the extension of my theme is like 1.0.emerald.. or somthin like that

---

### Post by hotrod6657 on 2008-08-05
okay, that theme should work providing it isn't corrupt or anything.

---

### Post by oneouncebrick on 2008-08-05
ok.. it still isnt working :( lol i did the replace code and went and clicked on my theme in my emerald themes manager and now its not doing anything my terminal just says reloading... and its been that way for like 10 minutes

---

### Post by OutOfReach on 2008-08-05
Did you try my way?

---

### Post by oneouncebrick on 2008-08-05
yea i did both of your ways... lol and wen i click on the theme, in the list it juat wont show up around the edge of my windows :( i dont want to give up on this :((((

---

### Post by OutOfReach on 2008-08-05
Hmm, interesting, Go back and right click the blue icon thing and under Select Window Decerator, but this time select GTK. Then when window borders appear go back and right click on the blue icon under Select Window Decerator, select Emerald.

---

### Post by oneouncebrick on 2008-08-05
i have borders, there just not emerald :( is there somethin i did wrong? lol did i download it wrong should i have extracted somthing? is there a program to automatically do this FOR ME?! lol jk.... so confused..

---

### Post by OutOfReach on 2008-08-05
Hmm,Goto the terminal and type in ```
emerald --replace
``` again.

---

### Post by oneouncebrick on 2008-08-05
this comand literally does nothing.. lol :(

---

### Post by hotrod6657 on 2008-08-05
if you give me the link to the theme you're trying to use i'll see if i can get it to do anything on mine.  It might just be that the theme we're working with has a problem.  Usually the replace command will basically refresh the display and allow you to start using the new theme.

---

### Post by OutOfReach on 2008-08-05
Yes emerald --replace SHOULD have worked, if you can just give us the link to the theme so we can try it.

---

### Post by alsamman on 2008-08-05
Instead of typing emerald --replace in terminal, press alt+f2 and type emerald --replace in there and click Run

---

### Post by oneouncebrick on 2008-08-06
here is the link to the theme encase someone wants to try it [http://gnome-look.org/content/show.php/Fusion+Glass+?content=8651]("http://gnome-look.org/content/show.php/Fusion+Glass+?content=8651")

---

### Post by hotrod6657 on 2008-08-06
I'll give that a shot and see how it works

---

### Post by hotrod6657 on 2008-08-06
sorry, link's bad, can you try it again?

---

### Post by Zyren on 2008-08-06
hey all i've been stuck not being able to replace my emerald theme. I am not that much of a noob with ubuntu and have used it on and off for the past couple years but im no expert on it. When i started reading this thread i had already done most of what has been said. i have compiz and emerald installed and i had already imported the theme i wanted. Its listed as a theme in emerald theme manager, but when i doubt click on it, it does enable.

Now i noticed that you guys said i need to enable emerald theme by going to applications, system tools, compiz fusion, but i have no system tools section. i looked everywhere and the only way i can change stuff form compiz fusion is from the advanced desktop effects settings. I cant find at all where to set emerald as my default themes manager.

When i do emerald -- replace it changes my theme but then a split second later my borders disappear until i log out. When i log back in it reloads the default theme.

Any help please?

---

### Post by Crafty Kisses on 2008-08-06
Emerald themes are pretty simple:

Install Emerald by doing the following:
```
sudo apt-get install emerald
```

Then download what Emerald theme you want, then open up "Emerald" then click the "Install" option, find the Emerald file you wanted to install, and double click on it.

If it doesn't instantly replace your Window Manager, do the following, ```
Alt+F2
```

Then you should get a prompt that says run, and in that box type the following:

```
emerald --replace
```

After that you should be set.

---

### Post by hotrod6657 on 2008-08-07
If you're not seeing anything under system tools try this:

I'm assuming you have desktop effects enabled and have installed the Advanced Desktop Settings.  It's the place where you can add the cube, change window effects, etc.  From there go to Window Decoration, in the effects category.  From there edit the line that says command.  type in "emerald"  That will tell your system to use emerald as it's window decorator.  

Then do the Alt + F2 ```
emerald --replace
```

That should get it to work.

If you don't have the settings manager try this:

```
sudo apt-get install compizconfig-settings-manager
```

That should give you the manager.

---

### Post by hotrod6657 on 2008-08-07
> **OutOfReach said:**
> Seems a little odd that you don't have an .emerald directory.
Do you have emerald installed?
If not type this into the terminal (Applications>Accessories>Terminal)
```
sudo apt-get install emerald
```

This will give you the thing to click in System Tools (it will add that whole option) If you go that route then follow his instruction for making Emerald the window decorator and it should take care of it.  either way should work.

hotrod

---

### Post by axmasta on 2008-08-07
hey guys, quick question
I`m having a tough time finding all the config apps I need to get the kind of desktop i`m looking for.

Is Emerald only for the frame and titlebar of your windows?

---

### Post by hotrod6657 on 2008-08-07
Yeah, emerald is only the window decorator.  The rest of the desktop can be changed by going to:  System, Preferences, Appearance.  The themes tab there should give you some options for the rest of your desktop.  If you want more themes download GTK themes from the sites where you get your emerald them.  Just drag and drop them into the Appearance window where the other themes are listed.

hotrod

---

