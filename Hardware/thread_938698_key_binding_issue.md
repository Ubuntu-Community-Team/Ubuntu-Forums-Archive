---
title: "key binding issue"
date: 2008-10-05
forum: Hardware
---

### Post by pooyaplus on 2008-10-05
Hi every one,
I am trying to bind 2 of my tx2000 laptops with Xmodmap (replaced by the package *x11-xserver-utils*) to run a script enabling the rotation of the screen. The tips are from a translation from a Finnish ubuntu forum here:

[www.mirosol.kapsi.fi/tx2020/tx2000howto.html]("http://www.mirosol.kapsi.fi/tx2020/tx2000howto.html")

I now have a script that does the rotation work perfectly (rotation.sh). Here I want to bind its execution to key code 205 (key code of the quick launch button, checked it by executing and monitoring xev)

I made a .Xmodmap file and put these codes in it:
```

keycode 237 = XF86Launch0
keycode 205 = XF86Launch1

```

keycode 237 is for the DVD button on tx2000 series.
Now I add the commands in the GConfeditor or Compiz advanced setting manager;
```

run_command0_key XF86Launch0
run_command1_key XF86Launch1

```

and redirect it to execute some commands like this:
```

command0 elisa
command1 ~/rotation.sh

```

But neither of the buttons does the expected commands.

Any ideas?

Here is the rotation script attached:

---

### Post by gali98 on 2008-10-05
have you logged out and logged back in? (or restarted) there should be a box that pops up and asks you what xmodmaps you want to use. You have to load that file (it will already be in the window if you put the file in the right place.)
Also you can run the command xmodmap ~/.Xmodmap

 Also another way to check where your problem is is to run
xev


then press those keys..

there should be a line that looks like 

    state 0x0, keycode 65 (keysym 0x20, space), same_screen YES,
for each keypress.
if the .Xmodmap is working then "space" should be replaced by XF86Launch0 or XF86Launch1.
If not then it will say "NoSymbol". If it says XF86Launch0 or XF86Launch1 then your problem is in gconf. If it says Nosymbol then the .Xmodmap is not being loaded.


Kory

---

### Post by pooyaplus on 2008-10-06
The command xmodmap ~/.Xmodmap does nothing. And I do not see that window you are talking about.

With the xev, those buttons show what we were expecting: XF86Launch0 and XF86Launch1, but the buttons show no functionality. So what would be the problem with the gconf?:confused:

---

### Post by gali98 on 2008-10-08
First of all I just realized something..

Are you on Compiz? (the 3d graphics. This come default on Ubuntu... You need to check this first. If you are on compiz, you will need to do this another way.)
To check go to System->Preferences-> Appearance
Click on the Visual Effects Tab. If it is not set to None you are on compiz.

If you are on compiz, post that you are. If you are not on compiz run the script I uploaded below.
It will create a text file on your Desktop named output.txt. Upload that.
Kory

---

### Post by Trevski13 on 2009-03-10
> **gali98 said:**
> First of all I just realized something..

Are you on Compiz? (the 3d graphics. This come default on Ubuntu... You need to check this first. If you are on compiz, you will need to do this another way.)
To check go to System->Preferences-> Appearance
Click on the Visual Effects Tab. If it is not set to None you are on compiz.

If you are on compiz, post that you are. If you are not on compiz run the script I uploaded below.
It will create a text file on your Desktop named output.txt. Upload that.
Kory

Hi, this thread is a little old but eh... so, I am having the exact same problem, I also have the tx2000 (Ubuntu 8.10) and used that same website, my rotate script runs perfectly and my Xmodmap is successfully loaded on startup. However, after looking into it I've come to believe that my media/quick-launch/quick-play keys are actually dead (I know the rotate and config keys are dead, but it seems the DVD and Quick-Play are as well. I'm basing this on the fact that xev shows no reaction what-so-ever when I press either of them (I could be wrong on that, I honestly don't know, that was just an educated guess)). I personally am indeed running compiz so if you could post your solution for that, I'd greatly appreciate it.

Thanks

---

### Post by Favux on 2009-03-10
Hi Trevski13,

gali98's fix for the DVD and Quicklaunch key are at the bottom of the first post here:
[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")
In the "Key Code Addendum".

---

### Post by Trevski13 on 2009-03-10
Sorry, read below

---

### Post by Trevski13 on 2009-03-10
> **Favux said:**
> Hi Trevski13,

gali98's fix for the DVD and Quicklaunch key are at the bottom of the first post here:
[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")
In the "Key Code Addendum".

Thanks, those commands were the "key" (pun intended) to getting it to work, although, it took some extra tweaking and trouble shooting on my part to it to fully work... so after running said commands, the DVD button worked correctly, launching VLC. HOWEVER, absolutely NOTHING happened when I pressed the quickplay button, I eventually figured out that the quicklaunch key was, in fact, 201, not 205 as I had in my script. So after switching this, again... nothing... I FINALLY figured out that: 1. the DVD button was not 237, but was instead being read as some media launch key (thus not requiring, or even using, my bindings). And the quick launch key was for some reason rebound as 156 (not a clue why, but xev showed 201 and then something something 156 (sorry I don't recall). SO... after reassigning it from keycode 156, it finally worked :D ("and there was much rejoicing").

again, thank you (-_-)

---

### Post by Favux on 2009-03-10
Hi Trevski13,

Good job!  You're welcome.

That is some weird stuff.  My Q key changed from 205 in Hardy to 201 in Intrepid.

If you ever figure out the brightness key and the original screen rotation key, let me know.

---

### Post by Trevski13 on 2009-04-08
I'm sorry, what do you mean by figure out the brightness key? do you actually mean the settings like button? the one next to the original rotation key? or are there problems with some brightness keys that I am unaware of?

---

### Post by Favux on 2009-04-08
Hi Trevski13,

We've never detected a signal from our swivel hinge or the two keys in the lower right corner of the bezel in laptop mode.  So they don't do anything.  But if you go back a little in the Rotation HOW TO you see that MisteR2 thinks he's figured it out.  He thinks it's a kernel module called hp-wmi and he posted a bug on it that he linked.

---

### Post by Trevski13 on 2009-04-08
> **Favux said:**
> Hi Trevski13,

We've never detected a signal from our swivel hinge or the two keys in the lower right corner of the bezel in laptop mode.  So they don't do anything.  But if you go back a little in the Rotation HOW TO you see that MisteR2 thinks he's figured it out.  He thinks it's a kernel module called hp-wmi and he posted a bug on it that he linked.

Yes I know about the lack of signaling, I was just slightly confused about the mentioning of "brightness keys" that's all.

---

### Post by pooyaplus on 2009-04-19
> **Favux said:**
> Hi Trevski13,

We've never detected a signal from our swivel hinge or the two keys in the lower right corner of the bezel in laptop mode.  So they don't do anything.  But if you go back a little in the Rotation HOW TO you see that MisteR2 thinks he's figured it out.  He thinks it's a kernel module called hp-wmi and he posted a bug on it that he linked.

Just a dumb question: why there is simply no sign of life there?

---

### Post by Favux on 2009-04-19
Hi pooyaplus,

Go ahead and post on the bug report.  I was going to in a couple days to keep it alive.  The discussion starts a few posts before post #92 (bug link) and continues:  [http://ubuntuforums.org/showthread.php?t=996830&page=10](http://ubuntuforums.org/showthread.php?t=996830&page=10)

---

