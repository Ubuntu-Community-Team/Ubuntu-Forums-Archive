---
title: "WORKING: Hardy + ATI + Laptop + External Monitor"
date: 2008-05-02
forum: Hardware
---

### Post by rvandam on 2008-05-02
I had a hell of a time finding the information to get this to work so I thought I should post it for anyone who needs it.  This isn't so much a HOWTO as it is a transcript of what I did, for better or worse.

Setup:

Fresh install of Hardy Heron 8.04 (but using /home shared with previous Feisty)
ATI Technologies Inc M22 [Mobility Radeon X300]
Dell Inspiron 9300 Laptop, max resolution 1440x900
ViewSonic External Monitor, max resolution 1680x1050

> If you're screen resolutions are different, every time you see these two resolutions in the instructions below, replace them with your resolutions.  [COLOR="Red"]But see the note at the bottom if you use a resolution as big as 1920x1200[/COLOR]

Steps:
1) In System->Administration->Hardware Drivers, I enabled ATI accelerated graphics driver.

2) I installed ATI Catalyst Control Center.  At this point, I could use Catalyst to get me into BigDesktop mode instead of cloned mode but only at a resolution of 2880x900 which is my laptop resolution double-wide.  But my external monitor supports a much larger resolution and the so it was a little box instead of a big black box.  If you can't even get to that 
point, the rest of this may not help any.

NOTE: I don't know for certain whether or not this next step is necessary so I recommend trying the later steps first with the driver Ubuntu provides by default.  Heck, I don't even know if the driver installed by EnvyNG is even different than the one I already had, I was just blindly following another forum post ;).

3) I installed envyng-gtk.  This also installs envyng-core.  I'm assuming envyng-qt would work similarly but I haven't tested it.  I used envyng (via Applications->System Tools->EnvyNG) to install the latest driver.  This uninstalls the previous driver AND Catalyst and reinstalls both and then some more stuff and configures everything automatically.

[SIZE="4"][COLOR="Red"]FAILED ATTEMPT: Maybe this will work for you [/COLOR][/SIZE]
[SIZE="4"][COLOR="Green"]This does work for larger external monitors 1920x1200[/COLOR][/SIZE] See note at the bottom.
4) I opened up a terminal and typed

```
sudo aticonfig --mode2=1440x900,1680x1050
```
Notice the comma.

5) I opened up the new randr utility (System->Preferences->Screen Resolution OR gnome-display-properties) and the new mode WAS NOT THERE.  Maybe if you're lucky it will work for you.

[SIZE="4"][COLOR="Green"]SUCCESSFUL ATTEMPT:[/COLOR][/SIZE]
6) Back in the terminal I typed

```

sudo aticonfig --add-pairmode=1440x900+1680x1050
sudo aticonfig --list-pairmode

```
Notice the plus (+).

Which gave me this output:
```

Get pair modes: 2
 0    1680x1050 + 1680x1050 --> 3360x1050
 1    1440x900 + 1680x1050 --> 3120x1050

```

If you see something like that you should be well on your way.  You can also double check the new set of possible values by typing

```
xrandr
```

You should see at least one really big resolution from the pair mode list above.  Possibly two.  Actually, you should see a whole lot of resolutions but if you don't, that's a whole 'nother can of worms.

7) I went back to Screen Resolution and changed my resolution to one of the new pair mode/big desktop resolutions and voila! Dual Monitors working perfectly.

IMPORTANT NOTE:

If you try to do this on a larger monitor and you get this type of error:

```
FGLRX_AddPairMode failed when try to add mode : 1440x900+1920x1200
```

Then in this case using just mode2 worked for me (no idea why)

Mode2 DOES NOT WORK WITH pairmode! So if you want a larger resolution external monitor, try this:

```
sudo aticonfig --remove-pairmode=0
```
Repeat while --list-pairmode still gives any results and then

```
sudo aticonfig --mode2=1440x900,1920x1200
```

---

### Post by Saint Angeles on 2008-05-02
good stuff. i'm not trying to hijack your thread, but heres a post i wrote explaining how i've gotten ATI to work on several machines.

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

---

### Post by user1234 on 2008-05-02
> **rvandam said:**
> 

1) In System->Administration->Hardware Drivers, I enabled ATI accelerated graphics driver.

2) I installed ATI Catalyst Control Center.  At this point, I could use Catalyst to get me into BigDesktop mode instead of cloned mode but only at a resolution of 2880x900 which is my laptop resolution double-wide.


Uhm, can you please tell me what those are via command line, I don't have the same GUI as you, (I use fluxbox in xubuntu).

---

### Post by DreamerMd on 2008-05-02
Any idea how to make it work on Nvidia cards?
Got XPS 1330 Nvidia 8400 GS andeverything is working now..compiz...  wireless... bluetooth, but dvd's, mp3, and of course external  monitor.. need some help!:KS

---

### Post by rvandam on 2008-05-02
> **Saint Angeles said:**
> good stuff. i'm not trying to hijack your thread, but heres a post i wrote explaining how i've gotten ATI to work on several machines.


Nice tip and I'm sure somebody can use it but it's not really specific to getting dual monitors with different resolutions working which is what I was going for.

---

### Post by boppp on 2008-05-02
Nice one man :D it does work for me!

Really, really nice, just 1 disappointment here, compiz stops working from the moment that i use 2 monitors, when i unplug the second and i restart, compiz works again, any clue?

---

### Post by rvandam on 2008-05-02
> **boppp said:**
> Really, really nice, just 1 disappointment here, compiz stops working from the moment that i use 2 monitors, when i unplug the second and i restart, compiz works again, any clue?

I'm glad it worked for you.  I don't know yet about compiz but I suspect that, at least with ati, you can't do compiz with dual monitors in different resoultions.

I say that mostly because I know someone at work who has Hardy working with an Nvidia card and compiz in dual monitors but his monitors are identical (same make and model).

I, on the other hand, cannot get compiz to work unless I'm only in single monitor mode.  (Maybe its also the non-identical outputs of laptop lcd versus dvi connected lcd?)

---

### Post by kiddai on 2008-09-26
Hi,

thank you for your post. I didn't work perfectly for me, but nonetheless it guided me to a working solution. My set-up is: laptop (1600x1200 FireGL 3200) + external LCD (1680x1050). What i had to do was:

[LIST=1]
[*]Install envyng gtk
[*]Install latest ATI driver
[*]Type in console: **[FONT="Fixedsys"]sudo aticonfig --initial=dual-head --screen-layout=left[/FONT]**
[*]Remove **ALL** pairmodes: **[FONT="Fixedsys"]sudo aticonfig --remove-pairmode=0[/FONT]**
[*]Set resolution of external screen: **[FONT="Fixedsys"]sudo aticonfig --mode2=1680x1050[/FONT]**
[/LIST]

Using **[FONT="Fixedsys"]sudo aticonfig --help[/FONT]** will give some additional hints on how to solve similar problems.

Have fun :)

---

### Post by An..?42! on 2008-10-27
Thanks a lot, very useful also for me.
I've wrote only: sudo aticonfig --mode2=1440x900,1920x1200 and all work on my notebook asus e philips 24"
Thanks for trick

---

