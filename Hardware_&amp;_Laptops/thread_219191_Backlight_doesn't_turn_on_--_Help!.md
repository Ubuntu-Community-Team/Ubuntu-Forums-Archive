---
title: "Backlight doesn't turn on -- Help!"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by bukzor on 2006-07-19
Here's the problem:

When I close my laptop (Dell B130) the backlight turns off, but when I open it again, it doesn't turn  back on. I can force it to turn back on by restarting X (Alt-Ctrl-Backspace) or changing consoles (Alt-Ctrl-F6, Alt-Ctrl-F7).

This is what caused it:

I used wine to install Warcraft III on Kubuntu. When I tried to play it, it worked but was horribly slow (I don't have a decent graphics card). When I exited the program, My resolution was very small (800x600 I think). I went into the "System Settings" and fixed the resolution, but that's what also started this backlight problem.

Let me know if there's any logs / config files you want to look at.

Thanks in advance!
--Buck

---

### Post by H.E. Pennypacker on 2006-07-19
You shouldn't say that the backlight is not turning back on, because that would only create nightmares.  I've actually had a backlight fail on me, and trust me, it's not pleasant.

So, the problem is not with the backlight, but with something else.  What you're describing has happened to me to.  First, let's make sure you don't have XGL/AIGLX/Compiz.  If you do, turn it off for now, because it can cause problems.

The problem lies, likely, in "Suspend" not being turned on.  Go to System > Preferences > Power Management (don't know how to do this in Kubuntu).  Change "When laptop lid is closed" to "Suspend."  Now, first make sure nothing important is on the screen, and then close the lid.  Give it a second, and open the lid once again.  The screen should turn back on.

Remember that Suspend only works on certain laptops.  It's more of a problem with Ubuntu, not the laptops.  Anyhow, that should fix the problem; it did with me.

---

### Post by bukzor on 2006-07-19
Thanks for the reply.

I don't know what XGL etc are, but they sound like some sort of OpenGL drivers, and i havn't installed any beyond the default Kubuntu setup.

As to your suggestion, I have specifically turned off the suspend on close feature, so that I can close my laptop and have it still keep working (compiling, downloading, etc). I'm pretty sure the problem isn't (directly) related to suspend mode (which worked perfectly for me out of the box btw).

A better question is: what causes the backlight to turn off when I close the laptop, why does the same mechanism not turn it on, and what broke it?

---

### Post by H.E. Pennypacker on 2006-07-20
buzor, if you don't know what XGL/AIGLX/Compiz are/is, you couldn't have installed it, and that's one thing we won't have to worry about.  Let's move on.

I see what you're saying about not wanting to suspend.  I like to leave the computer on as well while downloading stuff.  That makes sense.  

The screen turns off because the default option is set to "blank."  When you close the lid, the screen "blanks," because it is set to "blank."  When you open it back up, the screen won't turn on again.  I don't know why it does this.  Perhaps you should set "when laptop lid is closed" to "Do nothing."  That may work.  Just to get this out of the way, I don't know how to do this in Kubuntu.  I use Ubuntu.

For your own benefit, when you are not using the computer, it is best for the backlight to be off.  That is because the less you use your backlight, the longer it will last...it will have a great life-span.  Again, don't use it when you don't need it.

---

### Post by bukzor on 2006-07-20
Thanks again.

My confusion is that this all worked just perfect before I used wine. What configuration did wine change that broke this, I wonder.

---

### Post by bukzor on 2006-07-21
*bump*

I really want to fix this.

---

### Post by bukzor on 2006-07-21
Solved this one myself. Here's how:

I puzzled through the events that happen when opening and closing the lid, and found that the commands that did the real work of blanking and activating the screen were these:

xset dpms force off
su $user -c "xset dpms force on"

I then tried a little script of my own (as root):
xset dpms force off; sleep 3; xset dpms force on

This resulted in the screen turning off, but never on, which is why i was getting the problem I had. To fix this I did these edits:

add to "/etc/acpi/lid.sh"
```

     41         #su $user -c "xset dpms force on"
     42         vbetool dpms on

```

add to "/usr/share/acpi-support/screenblank":
```

      8 #xset dpms force off
      9 vbetool dpms off

```




Question 1:
How do i submit this as a bug report so that this gets worked on?

Question 2:
Is there a way to add "SOLVED" to the title of this thread?

---

### Post by robobart on 2006-08-06
Not so fast bukzor,

I'm having a very similar problem, *but* things are a bit more confusing. First of all, I am running a IBM T23 dapper xubuntu.

My backlight doesn't turn itself *most* of the time. When it doesn't I can get it turn on with Fn-F3 Fn-F4 (I always need both)

Your script is cool and I like that to test it *but* both

 # xset dpms force off; sleep 3; xset dpms force on

and

 # vbetool dpms off; sleep 3; vbetool dpms on

work for me... also I tried the modifications you suggest to no good result, my little key combo won't get the light to turn on--I had to restart!

Ok but If  I do


add to "/etc/acpi/lid.sh"
Code:
 41         #su $user -c "xset dpms force on"
 42         su $user -c "vbetool dpms on"

Then it works--though Still not every time... maybe like every 3rd time...
However, Fn-F3 Fn-F4 won't turn on my backlight so I just have to keep on opening and closing the lid hoping that it will turn on...

So let's not make the changes yet!

---

### Post by bukzor on 2006-08-07
vbetool seems to take quite a bit longer than xset dpms, sometimes up to 20 seconds. Also, I wouldn't suggest that the maintainers just use my little hack, but that someone who knows what's going on (not me) do a _real_ fix, probably an edit to the xset tool.

Would you say that you have more, less or equal success using the vbetool script? That's what i've been using since my last post and it works perfect (thought a bit slow).

It seems to me that you are experiencing a different problem from mine, with similar symptoms. It may be that your lid button is just sticky. If your lid button were to become stuck down 1/3 of the time, it would produce the symptoms you describe. You'll have to look at your model-specific documentation to find where the lid button is, and how to lube it up.

cya
--buck

---

### Post by robobart on 2006-08-07
>Would you say that you have more, less or equal success >using the vbetool script? 

With xset, the problem can be remedied by hitting Fn-F3 then Fn-F4.

However, with vbetool I must open and close my lid until it works.

I prefer to just hit the keys rather than open and close the lid.

>It may be that your lid button is just sticky. 

No. The computer comes out of suspension *every* time. I have a beep and a little light that tells me this. However the backlight doesn't come on every time. Moreover, this problem started when I switched distros. 
This is *not* strictly a hardware problem.

If I reset acpid,

/etc/init.d/acpid restart <--may not be exactly right I'm away from my laptop at the moment

then it will always work, vbetool, xset whatever.

However on the next close it doesn't.

---

### Post by H.E. Pennypacker on 2006-08-13
robocart, it sounds like we're in the same position.  I am having the same problem!

I followed bukzor's instructions, but like you said, after a restart, his instructions seem to go away by themselves, meaning that the effects of his instructions no longer work.  Weird, huh?  His instructions work, but then I restart, and they no longer work.

Did you ever find a solution?

---

### Post by H.E. Pennypacker on 2006-09-21
Are we making any progress when it comes to this issue?  It is rather important, and if it hasn't already been reported on Launchpad, I'll have to report it.

Currently, there's no way to close the lid, turn the backlight off, continue anything you had going on before (downloading a file, streaming music, burning a CD, etc), and then turn the backlight back on.  You can select "Blank screen," which will allow you to continue what you're doing, but won't turn the backlight back on.  

Or you can select "Suspend," but that means anything you had going on must be "paused" and continued after getting back from suspend.

The fundamental misunderstanding here is that ALL we want do is turn off the backlight.  We don't want to hibernate or suspend, nor do we want to blank the screen.  Turning off the backlight allows saving the backlight lifetime.  Unfortunately, not many people seem concerned about their backlights.  I've had a backlight fail on me, and I am not taking chances again.

---

### Post by robobart on 2006-09-22
It sounds to me like nearly all of us are after slightly different things.

Let me be explicit:

I am running a IBM T23 thinkpad. Xubuntu 6.06. Out of the box, a lid close will turn off the light, and start xscreensaver. Opening the lid will turn on the light and take you to the xscreensaver screen. 

I removed xscreensaver with aptitude.

Next I wanted my book to suspend when the lid was closed, so I changed: 
/etc/acpi/events/lidbtn to:

event=button[ /]lid
action=/etc/acpi/sleep.sh

Now, when I close the lid, the laptop will suspend. However, when I open the lid, I have to fiddle with it to get the backlight to come on most of the time. 

If I reset acpid, then the light will always come on once.

---

### Post by roadcone on 2008-04-26
OK, new here but have a similar problem:

I'm running Ubuntu 7.10 on a Thinkpad T61. I've started to have a problem recently that when I close the lid (I have it set to blank screen) and then open it again the screen will not come back on. If I keep repeating this, it always works on the third try. Not sure what the problem is, any help is appreciated!

---

### Post by roadcone on 2008-05-18
Bump.

---

