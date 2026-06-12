---
title: "[SOLVED] Problem with window sizes in Thunderbird, Emerald Theme Manager, Advanced De"
date: 2008-08-08
forum: General Help
---

### Post by Beth1957 on 2008-08-08
Hi all, Noob here.
I'm playing around happily with Ubuntu but have a couple of problems which are bugging me. I'll do the most annoying one first..
In some applications the size of the widow displayed isn't right; for example in Thunderbird the screen for the cards in the address book don't show the bottom of the card with the "save" or" apply" buttons, and there isn't a scroll bar. This means that I can only add users who have mailed me to the address book, and that I can't save any information I try to add (e.g. preferred email formats). I've attached a screenshot. I can't drag this window any further up using [Alt+button 1], unlike other windows.

I've tried moving the window about(, and resizing it, but it doesn't help. I can "push" the bottom border further down, but not far enough to see the "Save" button.

I have a very similar problem with Emerald Theme Manager; the window is too big, and it also seems to jump about in a rather odd manner when I try to hange some of the preferences - I can get to the "save as" dialogue by dragging the top of the window ip so it's off-screen, but when I try to type in the dialogue box, or click "save", the page jumps back down.

Any help welcome, preferably in words of one syllable for a poor old Noob fresh to both Linux & programming

I'm running Hardy Heron on a Lenovo 3000 C100/0761/3EG spec: Celeron M 370(1.5GHz),
1 GB RAM,
40GB 5400rpm HD,
15in 1024x768 LCD,
Intel 900,

---

### Post by northern lights on 2008-08-08
This is odd indeed.

You can drag windows by holding the "Alt" key while left-clicking anywhere on a window. This as a short term solution.

You could also try the following: Run

sudo /etc/init.d/gdm stop

from a terminal. This will kill the graphical desktop environment, so jot down the next few lines first. Log into the shell by pressing "Alt+F1", then reconfigure X by running

sudo dpkg-reconfigure -phigh xserver-xorg

Restart the desktop environment with

sudo /etc/init.d/gdm start

Any better?

---

### Post by gjoellee on 2008-08-08
there is might a fix for this problem in the updates, have you updated Ubuntu recently?

---

### Post by Beth1957 on 2008-08-08
> **northern lights said:**
> This is odd indeed.

You can drag windows by holding the "Alt" key while left-clicking anywhere on a window. This as a short term solution.

[COLOR="DarkSlateBlue"][FONT="Verdana"]This works to an extent on the apps; on Emerald and Advanced Deskto: I can drag the windows, but if I try to do anyting at the newly-revealed bottom of the screen it goes haywire & the window jumps back down (then back up again if I try to close it normally: I end up closing it through the system monitor :sad:)
In the Contact Cards in Thunderbird I can move the windows with Alt + left click but still can't get to see the bottom bit.  
I though this might be a problem with Thunderbird so I tried Evolution, but got the same problem.[/FONT][/COLOR]

> You could also try the following:
 <snip>
Any better?

[COLOR="DarkSlateBlue"][COLOR="DarkSlateBlue"]Aah... just tried that; thanks but it didn't help; I got the following error messages:- 

sudo dpkg-reconfigure -phigh xserver-xorg - package "phigh" is not installed and no information is available

sudo /etc/init.d/gdm start -no such file :???: 
Thanks for trying to help, though! [/COLOR][/COLOR]

---

### Post by Beth1957 on 2008-08-08
> **gjoellee said:**
> there is might a fix for this problem in the updates, have you updated Ubuntu recently?

Thanks; I install the update packages I'm notified of; is this what you mean,Joellee, or am I missing something? It's more than likely :lolflag:

---

### Post by northern lights on 2008-08-08
> **Beth1957 said:**
> [COLOR="DarkSlateBlue"][COLOR="DarkSlateBlue"]sudo dpkg-reconfigure -phigh xserver-xorg - package "phigh" is not installed and no information is available[/COLOR][/COLOR]

That sounds a lot like you didn't put the '-' in front of 'phigh'...

---

### Post by Beth1957 on 2008-08-08
> **northern lights said:**
> That sounds a lot like you didn't put the '-' in front of 'phigh'...

Aha... I'll try again!

---

### Post by Beth1957 on 2008-08-08
> **northern lights said:**
> That sounds a lot like you didn't put the '-' in front of 'phigh'...

Indeed you're right, I hadn't :oops:
I've managed to run the script you gave me correctly now though, but unfortunately it hasn't made any difference. Thanks for trying to help, though!

---

### Post by Beth1957 on 2008-08-13
Any more suggestions, anyone? I've switched to Evolution as my email client, but I have the same problem there... It's driving me nuts :(
Could it be my graphics driver, & if so how do I go about getting a new one, please?

---

### Post by Beth1957 on 2008-08-15
After much googling, searching of threads here, sheer dogged persistance & swearing I've found what isn't exactly a solution but a work-round.

I picked up from another thread that the problem is caused by compiz, which for some strange reason is messing up both Emerald and Evolution on my laptop.

So, getting rid of compiz sorts out the difficulty with the misbehaving winows. But hang on - without compiz installed I don't seem to be able to use my pretty Emerald theme or, of, course, have whizzy windows! I had a vague memory of coming across a reference to a program to switch compiz on & off easily (I thought at the time - "why?") & googled. Sure enough I found this:-
[http://forlong.blogage.de/article/pages/Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch)
and installed it.

And \\:D/ now I can leave compiz running most of the time & just switch it off when I want to fiddle with Emerald themes or add a new contact to my address book.

Off now to play with other window management systems on a rest user I D :-D

I've marked this thread as solved but if anyone has a more elegant solution....

---

