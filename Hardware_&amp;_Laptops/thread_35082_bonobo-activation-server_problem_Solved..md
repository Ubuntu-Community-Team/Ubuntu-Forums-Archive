---
title: "bonobo-activation-server problem Solved."
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by yakkmeister on 2005-05-17
This thread is for the benefit of users with iBook laptops and any other laptop that may have a problem with dropping hardware date and time.

Specifically, this addresses these symptoms:

Upon login to the standard Gnome interface, the following are encountered (posted by Arizona previously):

Error #1 
Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem.

Error #2
There was an error starting GNOME Settings Daemon. Some things, such as themes, sounds, or background settings may not work correctly.

Error #3
There was a problem registering the panel with the bonobo-activation server.
The error code is: 3
The panel will now exit.

The solution lies with the hardware clock.

NOTE:
If the laptop drops the hardware clock values, or resets to something like 1905 or something stupid, the cause may need to be addressed as well. (In my case it was the laptop crashing under OS9 when hybernating, remove battery to get it to startup and your date is gone)

When the errors are displayed (for simplicity sake), enter this combination:
[ctrl]+[option]+[f1]

This will open a virtual terminal.
Then, obtaining the correct time and date, enter the following command:
> sudo hwclock --set --date "MM/DD/YYYY hh:mm:ss"

To state the obvious (in case it's not): "Month/Day/Year hour:minutes:seconds"
I believe that this is the only accepted format.

That command sets the *hardware clock*
I think it'd be possible to simply restart at this point, but I decided to make the system clock match the hardware clock.
> sudo hwclock --hwtosys

then I checked it:
> date

And I restarted:
> sudo shutdown now

I understand that there is probably a million cooler and easier ways to do that, but this way worked for me.

Sorry if this post has bothered anyone.

---

### Post by Lupine on 2005-06-27
[QUOTE=yakkmeister]
Error #3
There was a problem registering the panel with the bonobo-activation server.
The error code is: 3
The panel will now exit.
[/QUOTE]


I've seen this problem for a while now.  My hwclock is fine, and this only happens whenever I "killall gnome-panel" to allow new apps to show up.  This continues to happen, and I've found no way around this.  Can't get it to stop, other than Ctrl+Alt+Backspace and log back in.  Most annoying :-x

---

### Post by amil salis on 2005-06-28
Thanks a lot.

It worked fine.

---

### Post by Lupine on 2005-06-28
Ok, found at least a way around the problem, without having to Ctrl+Alt+Backspace my way out of X.  Just get to a console and type "**killall bonobo-activation-server** ".  Doing this allowed the panel to reset and everything came back correctly.  Weird!

---

### Post by manfo on 2005-08-17
[QUOTE=Lupine]Ok, found at least a way around the problem, without having to Ctrl+Alt+Backspace my way out of X.  Just get to a console and type "**killall bonobo-activation-server** ".  Doing this allowed the panel to reset and everything came back correctly.  Weird![/QUOTE]

Same for me.

I don't know what happened: I haven't had the "killall gnome-panel" problem since today (when I installed gDesklets... I don't know if that could mean something). It's quite strange. Killing bonobo-activation-server seems to work, though.

(By the way, I'm also having some problems with Smeg: it can't see some of the menus that actually appear in the Gnome panel... Had to edit a couple of desktop files by hand)

Bye
.m

---

### Post by urbandryad on 2005-09-25
I've had this problem too. If this stuff works to help me fix it you  get lotsa kisses.  ^_^

---

### Post by urbandryad on 2005-09-27
it worked! :D Thanks!=D> :-({|= :-\\\

---

### Post by electroconvulsive on 2006-08-29
> I understand that there is probably a million cooler and easier ways to do that, but this way worked for me.


I hope you can tell me a few of them most likely one that involves doing this via the mac firmware. Reason being I tried your method om a G4 tower where im having the same problem on install of ubuntu 6.06 ppc and when I try to sudo hwclock it returns an error message staing that there is no way the install disk can access the hwclock. The problem is also preventing me from installing OS9 on the machine and doing it that way.

---

### Post by liam_stoush on 2006-08-30
I've just solved this problem on my iBook 700, whose battery I neglectfully let run flat while suspended.
I couldn't use the first process as I "could not access the hardware clock by any known method", but in the failsafe xterminal, I used

```
sudo date --set 30/08/2006
```

...then exited, restarted, and made a small jump for joy. 

One question I still have after the whole thing is---what on earth does the bonobo-activation-server *do*?

---

### Post by rabidsnail on 2006-09-03
> **liam_stoush said:**
> One question I still have after the whole thing is---what on earth does the bonobo-activation-server *do*?

The bonobo-activation-server starts [Bonobo](http://en.wikipedia.org/wiki/Bonobo_%28computing%29), which is a daemon that manages connections between programs in gnome.

---

### Post by thirteenpixels on 2006-09-05
> **liam_stoush said:**
> I've just solved this problem on my iBook 700, whose battery I neglectfully let run flat while suspended.
I couldn't use the first process as I "could not access the hardware clock by any known method", but in the failsafe xterminal, I used

```
sudo date --set 30/08/2006
```

...then exited, restarted, and made a small jump for joy. 


This worked for me but I had to take one more step to make the settings stick:

```

sudo clock -uw

```

---

### Post by kounavi on 2006-11-07
You are my hero!
[B]
Thank you![/B] A million times :)

Who would have thought...

---

### Post by bluedemon on 2007-05-22
Thanks alot yakk. Problem is solved..........:p:p

---

### Post by Mr Potter on 2007-10-27
Hey guys was running into a similar problem with 6.10 on a PPC Powerbook G3 (amber).  Long story short, I'm trying to move from my Xubuntu install to Ubuntu.   My problem was happening on boot with the Ubuntu live cd (Xubuntu was working fine), Nautilus would die after login.  Though I used the installed copy of Xubuntu to fix the problem you should be able to do the same from the live cd.  Once booted just ignore the errors and go to System>Administration>Time and Date.  Set to appropriate time.  Open terminal and then:> sudo hwclock --systohc.  This will set the hardware clock to the corrected settings in the system clock.  Reboot and Nautilus should be ok, along with bonobo.  

In case it hasn't been pointed out, this problem is partly to blame on a dead or dieing bios battery (laptops will be ok, provided you keep their battery charged). 

The earlier fix in this thread wasn't working for me (most likely because I'm a noob, and couldn't get the time format correct).  After applying this fix the system booted the cd and installed with out a fuss.  

I'm hoping that someone will take up the 6.10 Feisty distro and keep it alive for a while, for all of us with PPC hardware. I've ran Xubuntu on this Powerbook since January, and it's preformed great.  Not sure if this fix will help at all, figured I'd throw it out there just in case.

---

