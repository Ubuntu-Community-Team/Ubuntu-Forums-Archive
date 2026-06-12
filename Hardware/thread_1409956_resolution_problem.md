---
title: "resolution problem"
date: 2010-02-18
forum: Hardware
---

### Post by tejashs on 2010-02-18
my computer is an AMD athlon X2,
M2N68-AM SE2 motherboard.
it has  an on board n-vidia graphics card n-7025

I have Ubuntu 9.10  installed via wubi
i also installed the graphics driver ver-185
but  even if i change my resolution it gets reset every time I boot to  800*600.
what should i do?

---

### Post by labinnsw on 2010-02-25
Here are 2 good links.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

[http://solutionz.yolasite.com/linux/add-a-new-screen-resolution-with-the-terminal-on-ubuntu-9-10](http://solutionz.yolasite.com/linux/add-a-new-screen-resolution-with-the-terminal-on-ubuntu-9-10)

---

### Post by tejashs on 2010-02-27
Also all the video players except VLC and totem give video output errors

---

### Post by labinnsw on 2010-02-27
Were you able to fix the resolution using the links?
If not what problems did you encounter?

> **tejashs said:**
> Also all the video players except VLC and totem give video output errors

Please list the output errors.

---

### Post by tejashs on 2010-03-03
That's not the problem
All resolutions supported by my monitor are shown
when i log on the resolution is 800 x 600
then i change to a higher resolution and click apply
after restarting my system the resolution resets to 800 x 600

---

### Post by labinnsw on 2010-03-04
Are you saying that the instructions in the first link, under the heading> Setting xrandr changes persistentlydid not work for you?

---

### Post by realzippy on 2010-03-04
> **tejashs said:**
> That's not the problem
All resolutions supported by my monitor are shown
when i log on the resolution is 800 x 600
then i change to a higher resolution and click apply
after restarting my system the resolution resets to 800 x 600

you have to click

"*save to X configuration file*" 

also after you clicked "*apply*".

---

### Post by tejashs on 2010-03-04
> **labinnsw said:**
> Are you saying that the instructions in the first link, under the headingdid not work for you?
i am new to linux and not able to use command line.
i tried to save the settings to my xorg.conf file but the following message appears 
"  Unable to create new X config backup file '/etc/X11/xorg.conf.backup "

---

### Post by realzippy on 2010-03-04
..that's because you have no root privileges.
You have to open the terminal and simply type:

**gksudo nvidia-settings**

---

### Post by labinnsw on 2010-03-04
> **tejashs said:**
> i am new to linux and not able to use command line.


Don't be scared of it. It is the most powerful and versatile tool on any OS.

Just go to Accessories >> Terminal
Once open, copy and paste the commands from the tutorials.
Sometimes you will need to input your password to perform some functions.
As you put the password in, you will not see any masking or any indication that the password is being entered but whatever you type will be registered.
Press the "Enter/Return" key after each input.

Check out some YouTube "How Tos" to see the command prompt in action.

---

### Post by underquark on 2010-03-04
> **tejashs said:**
> i am new to linux and not able to use command line.I agree - don't be scared; try it.  IMHO it's essential to the best use of Linux (and Windows, for that matter).

> **tejashs said:**
> i tried to save the settings to my xorg.conf file but the following message appears 
"  Unable to create new X config backup file '/etc/X11/xorg.conf.backup "
Yes, you need permissions set correctly but - even then - directly changing the xorg.conf file or choosing "Save to..." when setting the resolution won't always make it permanent.


Have a look [here](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

or [this one.](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

---

### Post by tejashs on 2010-03-04
> **realzippy said:**
> ..that's because you have no root privileges.
You have to open the terminal and simply type:

**gksudo nvidia-settings**


thank you guys, i was able to set it right.:P

---

### Post by tejashs on 2010-03-04
> **realzippy said:**
> ..that's because you have no root privileges.
You have to open the terminal and simply type:

**gksudo nvidia-settings**

thank you guys. I was able to set it right.:P

---

### Post by DonThompson on 2010-03-04
This worked for me until today's updates.  Sadly I paid no attention to what they were.
Now I get:

[I]root@lanthia4:/home/don# cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

root@lanthia4:/home/don# xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  23
  Current serial number in output stream:  23[/I]

I see no named color or font.

---

### Post by realzippy on 2010-03-04
...thats why you run xrandr as root.Edit: WRONG!!See posts below.
*xrandr --newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync*
as user will work.

---

### Post by DonThompson on 2010-03-04
Running as user does not help either with or without sudo.

This seems to be a problem created by the updates put through March 1-3 as everything was fine until the restart was required.  (Although, since I had not rebooted in some time, it could have been from longer ago.)

---

### Post by realzippy on 2010-03-05
[Edit:
see next post.

---

### Post by realzippy on 2010-03-05
Ahh!!!

This error happens when you run
xrandr --newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync
twice.
Got to my testaccount,first time:

```
test@holzhaus:~$ xrandr --newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync
test@holzhaus:~$ 

```

Then :
```
test@holzhaus:~$ xrandr --newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  16 ()
  Serial number of failed request:  18
  Current serial number in output stream:  18
test@holzhaus:~$ 

```

!!
So you should go on with *xrandr --addmode* ......aso.

---

### Post by DonThompson on 2010-03-05
Thanks, realzippy.

Not quite able to do the addmode, but you led me in the right direction.  Even though the new resolution did not show up when using xrandr it was apparently hidden in there.  So using --delmode and then readding it worked and it showed up.

So for me, for now, whenever i go to add a resolution i will first delete it - but only if it's not there.

---

### Post by tejashs on 2010-03-05
now i am getting
"
Failed to parse existing X config file '/etc/X11/xorg.conf'!
"

---

### Post by labinnsw on 2010-03-06
[Here is a solution that has been known to work.]("http://ubuntuforums.org/newreply.php?do=newreply&p=7165382")

> **ajayrockrock said:**
> How I fixed it:

1)  open a terminal
2)  sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2)  sudo touch /etc/X11/xorg.conf  
3)  sudo nvidia-settings
4)  hit "save configuration"

with the empty xorg.conf, nvidia-settings should properly save the file.

See post No. 48 of the same thread is this does not work, but P L E A S E ignore the rude comments.

---

### Post by tejashs on 2010-03-06
i used 
"sudo nvidia-settings"
in terminal and tried to save it
then i got
"
Failed to parse existing X config file '/etc/X11/xorg.conf'!
"
i got the following error message in terminal
"
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required.

Segmentation fault

"

---

### Post by realzippy on 2010-03-06
Simply delete your xorg.conf and make a new one with nvidia-xconfig,then "parsing error" is gone.
Type in terminal:

**sudo rm /etc/X11/xorg.conf**

[I](To the guys jumping in the thread and claiming "you should backup first":
 No.No sense to backup trash.No discussion.)[/I] ;-)

Then create new xorg.conf:

**sudo nvidia-xconfig**

After this you can successfully run your nvidia-settings,but use **gksudo**
instead of **sudo**.In this case (nvidia-settings) it does no harm,but e.g.
*sudo nautilus* would smash things up.Allways use *gksudo* for a graphical (GUI) app,so:

**gksudo nvidia-settings**

---

### Post by tejashs on 2010-03-06
thank you it worked :)
but when i try to play videos with mplayer i get the following message is it related to this or is it different.
"
Fatal Error!
Error opening/initializing the selected video_output (-vo) device.
"
and then only the audio part plays

---

### Post by realzippy on 2010-03-06
...maybe you make a new thread if this:

[http://ubuntuforums.org/showthread.php?t=20039](http://ubuntuforums.org/showthread.php?t=20039)

does not help you....

---

### Post by labinnsw on 2010-03-06
Comment withdrawn. Comment was a result of a misunderstanding.

---

### Post by realzippy on 2010-03-06
@labinnsw

Real sorry,swear this comment was **not** addressed to you.

Only happened in former nvidia-resolution threads,and I wanted to
prevent a recurring discussion about backupping corrupted xorg.conf
in this special (nvidia-)context.
Again,sorry.

---

### Post by labinnsw on 2010-03-06
> **realzippy said:**
> @labinnsw

Real sorry,swear this comment was **not** addressed to you.

Only happened in former nvidia-resolution threads,and I wanted to
prevent a recurring discussion about backupping corrupted xorg.conf
in this special (nvidia-)context.
Again,sorry.

No problem, I respect your work

---

