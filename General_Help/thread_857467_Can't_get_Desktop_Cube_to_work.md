---
title: "Can't get Desktop Cube to work"
date: 2008-07-12
forum: General Help
---

### Post by IGottaWii on 2008-07-12
I finally got Ubuntu 8.04 (Hardy Heron) running!  I just have a few questions.  I can't get the Desktop Cube running.  I checked Desktop Cube and rotate cube, but when I ctrl alt click my screen just flips to the other side.  I can't even initiate the cube...

Also How do I install an emerald theme.  I have the theme manager, but when I click on the theme I imported there is not apply button.

And another question is, how come ubuntu runs slower than my Windows Vista.  Ubuntu has lag on my computer while windows doesn't and Ubuntu takes a little bit longer to boot up.

Here are my PC Specs: **[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01048301&lc=en&cc=ca&dlc=en&product=3436821&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01048301&lc=en&cc=ca&dlc=en&product=3436821&lang=en)**

I want to become a full time Ubuntu user because I heard it runs fast and is prettier.  Thanks in advanced for the help.

---

### Post by kaboodle_fish on 2008-07-12
Hi 

Under General Settings in the CompizConfig Settings Manager set the Horizontal Virtual size (which is under the Desktop Size heading) to 4 and this will give you the cube

---

### Post by IGottaWii on 2008-07-12
> **kaboodle_fish said:**
> Hi 

Under General Settings in the CompizConfig Settings Manager set the Horizontal Virtual size (which is under the Desktop Size heading) to 4 and this will give you the cube

K I'll give it a try in a little bit.

any idea how to fix these problems: Also How do I install an emerald theme. I have the theme manager, but when I click on the theme I imported there is not apply button.

And another question is, how come ubuntu runs slower than my Windows Vista. Ubuntu has lag on my computer while windows doesn't and Ubuntu takes a little bit longer to boot up.

---

### Post by kaboodle_fish on 2008-07-12
In the Emerald theme manager just select the theme you want and it will automatically change. There is no need to apply

---

### Post by 1xx1 on 2008-07-12
> **kaboodle_fish said:**
> Hi 

Under General Settings in the CompizConfig Settings Manager set the Horizontal Virtual size (which is under the Desktop Size heading) to 4 and this will give you the cube
It is set to four ...but i can't change to extra effects(nor to normal) and start the fusion icon with compiz and emerald-this is the problem...(only metacity works fine;when set to compiz the windows are without any borders)

Help guys !!!

Edit:also there is a daw-indirect rendering(in the menu of the fusion icon---when i disable it there is still no direct rendering;by default it is disabled when  made a fresh install of the system-but now ... :(   )
I  got 3d working in the past (with 7.04 ,7.10 even with 8.04,a few weeks ago-but after changing my mobo i made new install of win xp and ubuntu ...)

---

### Post by IGottaWii on 2008-07-12
> **kaboodle_fish said:**
> In the Emerald theme manager just select the theme you want and it will automatically change. There is no need to apply

No it doesn't :(  any fix to that?

Also the font looks kindy of crappy, like low quality how can you fix that?

---

### Post by Sealbhach on 2008-07-12
Hve you enabled emerald?

See the setion on emerald here.

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

These fonts? Where are they?

Personally I had a lot of trouble with emerald - a bit buggy.


.

---

### Post by IGottaWii on 2008-07-12
> **Sealbhach said:**
> Hve you enabled emerald?

See the setion on emerald here.

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

These fonts? Where are they?

Personally I had a lot of trouble with emerald - a bit buggy.


.

Thanks, I'll try it out in a bit. 

Here is a screenshot: [[IMG]http://img242.imageshack.us/img242/8385/screenshotqy8.th.png[/IMG]](http://img242.imageshack.us/my.php?image=screenshotqy8.png)

The problems there:
You see the line next to the trash bin... How do I get rid of that?

About the fonts Here is a screenshot that shows it:  [[IMG]http://img234.imageshack.us/img234/6386/screenshot2fu1.th.png[/IMG]](http://img234.imageshack.us/my.php?image=screenshot2fu1.png)

Thanks, 
IGottaWii


EDIT:  Youtube also stopped working, like the sound... It was working yesterday.  I uninstalled and reinstalled plugins, but the same thing.  Sorry for being such a noob.

---

### Post by Sealbhach on 2008-07-12
> **IGottaWii said:**
> Thanks, I'll try it out in a bit. 

The problems there:
You see the line next to the trash bin... How do I get rid of that?

I see what you mean. I don't know what that is. 

You could try another dock, like cairo-dock?

> **IGottaWii said:**
> 
About the fonts Here is a screenshot that shows it:  
Thanks, 
IGottaWii
It's recommended to install msttcorefonts - that might help if you havent already done that. 

```
sudo apt-get install msttcorefonts
```

You can also change the default fonts in Firefox (Edit/Preferences/Content tab).

Might help

More worrying is your computer being slower than Vista - how's that working out since you last posted?

You could install preload.

```
sudo apt-get install preload
```

Will speed start-up of apps.

There are lots of blogs and posts about Ubuntu tweaks - if you google for "speed up ubuntu" or something like that.

Hope this helps.

---

### Post by IGottaWii on 2008-07-12
> **Sealbhach said:**
> I see what you mean. I don't know what that is. 

You could try another dock, like cairo-dock?


It's recommended to install msttcorefonts - that might help if you havent already done that. 

```
sudo apt-get install msttcorefonts
```

You can also change the default fonts in Firefox (Edit/Preferences/Content tab).

Might help

More worrying is your computer being slower than Vista - how's that working out since you last posted?

You could install preload.

```
sudo apt-get install preload
```

Will speed start-up of apps.

There are lots of blogs and posts about Ubuntu tweaks - if you google for "speed up ubuntu" or something like that.

Hope this helps.

I've heard good things about awn the dock I'm using now, but I can't explain that line...

Well the ubuntu start up goes way slower than Vista don't know why, and Firefox is sometime unresponsive in Ubuntu...

How do I make the Fonts look more smooth on like everything, not just firefox?

---

### Post by kaboodle_fish on 2008-07-13
> **Sealbhach said:**
> It's recommended to install msttcorefonts - that might help if you havent already done that. 

```
sudo apt-get install msttcorefonts
```

+1 for this suggestion

---

### Post by Canis familiaris on 2008-07-13
> **IGottaWii said:**
> No it doesn't :(  any fix to that?



TO get emerald:
Press Alt+F2:
```
emerald --replace
```

To get gtk-window-decorator:
Press Alt+F2:
```
gtk-window-decorator --replace
```

---

### Post by IGottaWii on 2008-07-13
> **kaboodle_fish said:**
> +1 for this suggestion

Ubuntu still runs slower than Vista, and firefox locks up more often.  I tried the code, and the fonts look the same...  

Also I have no sound on youtube?

---

### Post by Sealbhach on 2008-07-13
> **IGottaWii said:**
> Ubuntu still runs slower than Vista, and firefox locks up more often.  I tried the code, and the fonts look the same...  

Also I have no sound on youtube?

I don't know why Ubuntu is slower for you, sorry.

You could try removing and re-installing firefox. Or you could try another browswer like Opera or Swiftweasel - they might work better?

Regarding the problem with Youtube,it must be something to do with flash. 
I strongly recommend following the Multimedia How-to here:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Just do exactly as it says there and it will hopefully fix your Youtube problem.


.

---

