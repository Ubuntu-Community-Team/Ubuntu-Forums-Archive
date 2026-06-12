---
title: "Change Middle Button so it Right Clicks"
date: 2019-12-30
forum: Hardware
---

### Post by West Swan on 2019-12-30
Hello,

I have an Evoluent Vertical Mouse 4 for my tennis elbow which has top, middle and bottom buttons plus a scroll wheel.

Top is for left click and bottom is for right click.  I use X-Mouse Button Control to tell Windows 10 that the middle button is also right click.  

I do that because I keep accidentally hitting the middle when I mean to hit the bottom button.  If they are both right click the problem is solved.


Is there a program for Lubuntu 19.04 that I can achieve the same result with?


I'd rather not use Terminal but if there is no program with a graphical user interface available I can force myself to try and follow step by step instructions.  A program would be better though :)


Scroll wheel is working perfectly in Windows and Lubuntu so any changes I make would hopefully not change that.


Hope the above makes sense.


Cheers,

Paul

---

### Post by CatKiller on 2019-12-30
I found [ a reddit post](https://www.reddit.com/r/ManjaroLinux/comments/bdblih/is_there_a_gui_client_to_help_configure_mouse/) that said

> Thanks for the couple of options. I tried both, neither worked unfortunately. I ended up using xinput commands. xinput test to see which button IDs I had, xinput set-button-map to adjust. As most things do in linux, it took a little trial and error and some documentation reading, but it wasn't bad at all.

---

### Post by West Swan on 2019-12-30
Hello,

I found a solution myself that lets the middle mouse button be used as a right click.  It was adapted from a solution somebody else who has the same mouse found for their situation.

My solution:

[B]xinput set-button-map "SONiX Evoluent VerticalMouse 4" 1 3 3 4 5 6 7 8 9 10 
[/B]

But it doesn't persist during a restart.

I know people have asked how to do this type of things (ie make it permanent) for various xinput scenarios but I am struggling to apply it to my specific situation.

Can anyone please explain step by step how to do this?

Preferably just a simple command that will work rather than opening files and adding text etc if that is possible please.




Regards,

Paul

---

### Post by West Swan on 2019-12-31
Oh and thanks in advance for anyone's time in helping me with this :-)

---

### Post by CatKiller on 2019-12-31
> **West Swan said:**
> Preferably just a simple command that will work rather than opening files and adding text etc if that is possible please.

I don't have experience with this kind of thing, but the solution is likely to be exactly putting some text in a text file. The initial configuration parameters for that device are read from *somewhere* and you want to change them, which will probably mean putting your parameters in a text file somewhere. The other approach, of utilising one of the scripts that gets run at times like starting the X server, or logging in, to automatically run the command that you've found works whenever your machine starts, will also involve putting your command in a text file somewhere.

---

### Post by West Swan on 2019-12-31
Hi again CatKiller,

Bugger.  I was hoping it would be easy.  Why can't these manufacturers support Linux with proper programs instead of forcing people to do things the hard way.

Half the time I can't even find the text files and then it looks different to what other people post.

Will wait to hear if anyone has a simple way of doing this that doesn't require any knowledge just step by step.

In the meantime I will put a text file (mouse.txt) on the desktop and copy and paste that command each time I login to Lubuntu.

That will be about once a week so not such a bad idea.  Will take less than 10 seconds.

30 years ago I could probably solve it myself but these days the old grey matter don't work so good :-)

Thanks again,

Paul

---

### Post by guiverc on 2019-12-31
I'm not in any fit state to reply currently, but I'd suspect the answer you want can be achieved via

[https://manual.lubuntu.me/stable/3/3.2/3.2.13/session_settings.html](https://manual.lubuntu.me/stable/3/3.2/3.2.13/session_settings.html)

(the Lubuntu manual page; stable=19.10, esp. AutoStart section) on Session settings, which says

"[COLOR=#404040][FONT=Lato]*Session Settings is the way to change what happens when log into Lubuntu. Here you can manage default applications and services at startup.*"

I'd hope you could put your text file you copy/paste into the command line from, as a 'script' to run (adding a shebang or "#!/bin/bash" to the first line so it knows how to interpret the line)  in the AutoStart application list. Yes I'd expect you to need to make it executable (`chmod +x`) - but I can try looking at this tomorrow if you like (*hopefully I feel better, or at least more awake*).  I would probably run it with "Wait for System Tray" checked.

--
I created a file called `blah.sh` on a Lubuntu 20.04 box which contained
```
#!/bin/bash
paplay /home/guiverc/Music/music_file.ogg

```
Made it executable (`chmod +x ~/blah.sh
Added it to the Autostart as per Lubuntu manual
Logout & login again, and the music_file.ogg plays as expected.
ie. you put whatever commands you need where I used "paplay" (or pulse-audio-play that I often use for testing)

[/FONT][/COLOR]

---

### Post by West Swan on 2019-12-31
Hi Guiverc,

Thanks you.

As an update I tried all that and ballsed it up.  Somehow I mucked up the She Bang.  Before now I always thought it was a Ricky Martin song.

However, this morning I sold a book to a customer who happens to work at a computer store as one of their technicians.  He offered to get the mouse working how I want it.

So he followed your instructions.  It took him about half an hour because he usually works with Windows computers  but it is now all working perfectly.

Appreciate your help :-)

Regards,

Paul

---

