---
title: "Anyway to increase battery life?"
date: 2008-11-28
forum: Hardware
---

### Post by saffagirl on 2008-11-28
Hi guys, well I've been running ubuntu (almost ) successfully for 3/4 months now.

Most of the problems are work arounds, kernel updates normally upset something on my machine and although it's not ideal it's managable to do a work around. However, I have noticed that I get about half the battery life in UBuntu that I do in Vista. Any ideas what can be done to better this? I'm running a vostro 1310.

---

### Post by sdennie on 2008-11-28
Though not the same model as your machine, I would imagine many of the components are similar and this guide should get you moving in the right direction: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773")

---

### Post by saffagirl on 2008-11-28
> **vor said:**
> Though not the same model as your machine, I would imagine many of the components are similar and this guide should get you moving in the right direction: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773")

Vor , thanks for this info:)

I've a couple of questions-I've never really modsified script like this before so am a little nervous, sorry. My harddrive,wifi are different (and there's no usb), how would I  adjust the script accordingly?

Thanks:)

---

### Post by sdennie on 2008-11-28
You'll notice descriptions of what each command is doing in the script.  An easy way to not make the script do what is described is to add a "#" in front of the command being described (similar to how the comments have a "#" in front of them).  You may also be able to find a graphical application to generate this sort of script for you.  I know that this project exists but, I have not tried it before: [http://ubuntuforums.org/showthread.php?t=988309](http://ubuntuforums.org/showthread.php?t=988309)

---

### Post by chadeldridge on 2008-11-28
saffa do some research on laptop_mode ([http://samwel.tk/laptop_mode/](http://samwel.tk/laptop_mode/)).  You need to make sure you are not running the Ubuntu version though because it basically does nothing. Using this utility and turning a lot of options on have increased my XPS M1710 from 1.2 hours to nearly 3.  It's well worth the time to read up on it.

---

### Post by saffagirl on 2008-11-29
> **chadeldridge said:**
> saffa do some research on laptop_mode ([http://samwel.tk/laptop_mode/](http://samwel.tk/laptop_mode/)).  You need to make sure you are not running the Ubuntu version though because it basically does nothing. Using this utility and turning a lot of options on have increased my XPS M1710 from 1.2 hours to nearly 3.  It's well worth the time to read up on it.
Chadelridge,
Thanks for this- this looks a much less complicated way to do it,I've just installed it and am going to try and fiddle around.. 

I'm assuming there's no graphical version as everything is scripted, right?Still a linux noob, so am learning slowly.

---

### Post by iggykoopa on 2008-11-29
If you look at the thread vor posted I'm writing a gui to manage all the power saving stuff. I don't have every option added yet but it's getting there. Plus it autodetects pretty much everything for you.

---

### Post by chadeldridge on 2008-11-30
saffa,  You are correct there is no GUI for this its all editing of text config files in \etc\laptop_mode.  

Iggy, I would be extremely interested to see what you have put together via gui .. I have managed to get about 2x the battery power from this laptop using laptop_mode, would love to see your app.

---

### Post by iggykoopa on 2008-11-30
the thread is here [http://ubuntuforums.org/showthread.php?t=988309](http://ubuntuforums.org/showthread.php?t=988309) same one vor posted. Thanks for the interest the more people that test it the better I can make it. It's not really documented right now but the safe options are checked by default and if you've been messing around with laptop mode then you should know most of  the rest.

---

### Post by chadeldridge on 2008-11-30
Should i disable laptop mode before installing?

---

### Post by iggykoopa on 2008-11-30
you don't have to, but if you set some of the same things in laptop mode then those settings might overwrite some from my gui. Its mostly the stuff about journal writeback and stuff like that.

---

### Post by the_fury on 2008-11-30
Hey, I've tried out the LAPTOP_MODE=TRUE solution, and it works! I get 40 minutes, opposed to the 25 minutes previously.

But that's also the problem.

I see people getting like 2 hours on their machines, and I get less than an hour? Any suggestions? I'm running a Sony VAIO, VGN-FZ series.

---

### Post by chadeldridge on 2008-12-01
Have you gone through the settings in /etc/laptop_mode/conf.d/  each config file there has settings for your machine that are either on 1 or off 0.  Open each config file and edit as you see fit.  The files are all commented really well so you should have no issue understanding what they are for.  My main ones were cpufreq.conf, hal-polling.conf, and intel-sata-powermgmt.conf.

---

### Post by iggykoopa on 2008-12-01
that does seem a little low, I have a dell 1420n with the 9-cell battery and I get about 3-5 hours with normal usage(mostly surfing the internet, a couple flash games)

---

### Post by saffagirl on 2008-12-01
Guys thanks for the fab health. I've been xmas shopping my apologies- so haven't really been able to read the messages:)Wow, v. impresed at all your help.

The gui sounds fab and would be a great idea for noob's who are nervous of scripting.

---

### Post by saffagirl on 2008-12-01
> **iggykoopa said:**
> If you look at the thread vor posted I'm writing a gui to manage all the power saving stuff. I don't have every option added yet but it's getting there. Plus it autodetects pretty much everything for you.


Iggy, I just tried running the script in terminal,but I've just got a command prompt, what am I meant to do from here?
j-laptop:~$ svn checkout [http://wattospm.googlecode.com/svn/trunk/](http://wattospm.googlecode.com/svn/trunk/) wattospm
Checked out revision 21.
j-laptop:~$ cd wattospm
j-laptop:~/wattospm$ sudo sh -c python powersaving.py
Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

What am I missing ? I had a look at the script and looks like it covers a lot of te basis, which is gr8, good project. FYI I'm getting just under 2 on a 6 cell  battery, vista I'm easily getting over 3.

---

### Post by chadeldridge on 2008-12-01
look on your gnome-panel bar now, you should see a lightning bolt either blue / red / or orange.

---

### Post by the_fury on 2008-12-01
> **chadeldridge said:**
> Have you gone through the settings in /etc/laptop_mode/conf.d/  each config file there has settings for your machine that are either on 1 or off 0.  Open each config file and edit as you see fit.  The files are all commented really well so you should have no issue understanding what they are for.  My main ones were cpufreq.conf, hal-polling.conf, and intel-sata-powermgmt.conf.

I found the folder in my filesystem, but "ac97-powersave.conf" and "wireless-ipw-power.conf" are both empty. Is this a bad thing?

---

### Post by iggykoopa on 2008-12-01
you need quotes around the python and powersaving.py part...like this:
sudo sh -c "python powersaving.py"

thanks for giving it a try and I hope it helps you out. The script needs to run with admin rights, and one or two of the settings don't work with normal sudo...thats why you need the sudo sh -c

edit: the way you typed it in it just saw the python command...that puts you in the interactive python console

---

### Post by saffagirl on 2008-12-02
> **iggykoopa said:**
> you need quotes around the python and powersaving.py part...like this:
sudo sh -c "python powersaving.py"

thanks for giving it a try and I hope it helps you out. The script needs to run with admin rights, and one or two of the settings don't work with normal sudo...thats why you need the sudo sh -c

edit: the way you typed it in it just saw the python command...that puts you in the interactive python console

I know, LOl. I tried with the quotes first and I got file not found....so tried without afterwards, thanks though. i'll look later and get back to you guys on progress.

---

### Post by saffagirl on 2008-12-02
Ok, I've looked again- there's  defintely not a thunderbolt on my desktop or my gnome panels or menus. I don't get any errors when i go into terminal...I'm at a loss here. thanks in advance.

---

### Post by chadeldridge on 2008-12-02
Make sure you have a notification area on your gnome-panel bar?  Right click the bar, add to panel, select notification area.

---

### Post by iggykoopa on 2008-12-02
after you do the: cd wattospm part type in ls... just to make sure you pulled down everything correctly from svn
because your output from svn should look like this(dont worry about the wattospm2 I just already had that directory on my desktop):
eric@lappy:~/Desktop$ svn checkout [http://wattospm.googlecode.com/svn/trunk/](http://wattospm.googlecode.com/svn/trunk/) wattospm2
A    wattospm2/powersaving.glade
A    wattospm2/performance.png
A    wattospm2/config
A    wattospm2/power_saving.png
A    wattospm2/stock.png
A    wattospm2/config.default
A    wattospm2/powersaving.py
Checked out revision 21.

---

### Post by saffagirl on 2008-12-03
> **iggykoopa said:**
> after you do the: cd wattospm part type in ls... just to make sure you pulled down everything correctly from svn
because your output from svn should look like this(dont worry about the wattospm2 I just already had that directory on my desktop):
eric@lappy:~/Desktop$ svn checkout [http://wattospm.googlecode.com/svn/trunk/](http://wattospm.googlecode.com/svn/trunk/) wattospm2
A    wattospm2/powersaving.glade
A    wattospm2/performance.png
A    wattospm2/config
A    wattospm2/power_saving.png
A    wattospm2/stock.png
A    wattospm2/config.default
A    wattospm2/powersaving.py
Checked out revision 21.


My first time i had this , subsequently it hasn't looked like this at all. I did check the notification area icon,nothing I'm afraid.( get  checked out revision 21 and that's it before the prompt)

---

### Post by the_fury on 2008-12-03
> **chadeldridge said:**
> Make sure you have a notification area on your gnome-panel bar?  Right click the bar, add to panel, select notification area.

I've got the lightning bolt, and I've figured out how to switch to "power save" mode... is there any way to configure it to switch to power save whenever you are on battery power?

---

### Post by iggykoopa on 2008-12-03
yup, right click on the lightning bolt and click on auto, click on manual to switch back. The default setting though is auto unless it didn't detect your battery correctly. Light blue lightning bolt is powersaving and red is performance.

---

### Post by RookieUbuntuUser58 on 2008-12-22
Sorry to bump an old thread but have a question.

What do I type into the terminal to edit the laptop_mode_tools. I already have it set to laptop_mode=true but would like to check out settings in laptop_mode_tools.

Next I dont have the lightning bolt icon in my notification area (even though I have laptop_mode_tools installed). How do i get this to enable power savings.


Thanks in advance for any help.

---

### Post by chadeldridge on 2008-12-22
You are talking about 2 different things.  

Laptop_mode is part of ubuntu, and honestly without a lot of manual effort does not work all that well (out of box).

The lightning bolt is part of the wattospm project and is totally separate from laptop_mode.  I have all together stopped using laptop mode and went solely to wattospm for power management.  It just works better and is easier to work with. 

You can get the application from svn on googlecode.  

Make sure you have subversion installed:
```
sudo apt-get install subversion
```

Then get the code
```
svn checkout http://wattospm.googlecode.com/svn/trunk/ wattospm
```

This will download the project to a directory called wattospm, from where you need to run the command:
```
sudo python installer.py install
```

Then reboot.

When your machine comes back up run from inside X (Alt-F2) python wattospm.py

You will now have the lightning bolt, if you wish for it to run automatically when you start X then place it in your session/ startup items.

---

### Post by RookieUbuntuUser58 on 2008-12-22
When I type the second code, I get URL doesnt exist.

---

### Post by chadeldridge on 2008-12-22
Sorry .. disadvantave of typing fast, i missed the spacebar:
```
svn checkout http://wattospm.googlecode.com/svn/trunk/ wattospm 
```

---

### Post by RookieUbuntuUser58 on 2008-12-22
Not sure what Im doing wrong but it is not working.

Just to make sure is this what I have to do exactly after your second code?

cd wattospm

then sudo python installer.py install

reboot

on desktop hit alt-f2

type "python wattospm.py"
 
and hit run

but nothing happens when I do this. Could laptop_mode_tools be affecting it?

---

### Post by iggykoopa on 2008-12-22
when you type in
sudo python installer.py install
what does it say? it should tell you that you need to reboot. Also try just running:
wattospm.py
from the terminal, that way you can see if it gives you any errors.

---

### Post by RookieUbuntuUser58 on 2008-12-22
Thanks got it working. When I pressed alt-F2 I had to put in "wattospm.py" instead of "python wattospm.py".

So how do I set it up to work efficiently or is it preprogrammed to work as is? Besides performance and power saving mode, anything else I need to do?

---

