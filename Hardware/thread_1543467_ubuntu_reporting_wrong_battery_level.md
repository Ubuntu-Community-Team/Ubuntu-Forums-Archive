---
title: "ubuntu reporting wrong battery level"
date: 2010-08-01
forum: Hardware
---

### Post by x-shaney-x on 2010-08-01
This has only started happening in the last few days and affects both lucid and maverick.

If I unplug the AC cable while ubuntu is running it instantly reports that battery levels are around 16%, even when it has been plugged in a while and previously said battery fully charged.
Also, it randomly does the same if I boot up while on battery power, but other times report it as being full.
Not only that, it DOES continue to keep counting down and will eventually go into hibernate mode.
If I then boot back into ubuntu it will report battery as being nearly full again.

At first I though I might have a faulty battery but this is ONLY affecting ubuntu (lucid and maverick), other distros are reporting it normally, as is windows.

HP G62 with lithium ion 6 cell battery

<EDIT>
Forgot to say, it carries on counting down to hibernate if I click on the icon in the panel but the icon itself never changes, shows the same 16% or whatever.

---

### Post by x-shaney-x on 2010-08-02
Sorry to bump but does nobody else have this problem?

---

### Post by InTheSand on 2010-08-18
Hi,

I have a similar problem on an eMachines netbook (350-21G16i, eM350 series).

Battery can be fully charged (and reports that when plugged in on AC power) but as soon as the netbook is booted up on battery power, it will work fine for about 10-15 minutes, then report remaining battery as critically low and go into hibernation then switch-off.

Rebooting will then report a more sensible battery level but again if on battery power only, will switch off again after a short time.

Netbook is almost brand new and no such problems under its supplied installation of WinXP.

Any help appreciated as it's driving my other half nuts!

 - Ali

---

### Post by x-shaney-x on 2010-08-18
Since I reported this a couple of weeks ago the problem is still there on both maverick and lucid but it is still displayed normally in openSUSE, mandriva, fedora and windows 7.

---

### Post by mastablasta on 2010-08-18
if you take out the batery, does the battery have any power level indicator? What is that one reporting?

---

### Post by x-shaney-x on 2010-08-18
If I take out the battery it shows the AC indicator (battery with a lightning symbol in it).
It shows the symbol full as if fully charged, exactly the same as it does with battery in and AC in.

I have noticed it DOES seem to show the correct level of charge when battery and AC are plugged in.

---

### Post by Dusenberg on 2010-08-29
I got same problem and replied to *this* thread [HTML]http://ubuntuforums.org/showthread.php?p=9780231[/HTML] before finding this one.

---

### Post by x-shaney-x on 2010-08-29
I've been using KDE a lot (on the same install) and don't get phantom battery reports in there, only seems related to gnome.

---

### Post by Alexislavie on 2010-08-30
Hi, I'm french and I just got installed ubuntu 10.04 on my hp g62-a50sf a few day back. I didn't have exactly the same problem you're having.
On windows 7 my battery works very fine. But in ubuntu she doesn't work as well, the applet for the battery only display the charge level when the AC power is plugged in, or whether if my charge level is under 7% (I found on windows 7 that my computer considerate this level as critically battery level).
So I can't know the charge level of my battery when not using AC power.
I search over the web, and posted a thread on ubuntu french forum but no good reply.
It seems that something in ubuntu doesn't support as well our battery management.
Otherwise I upgraded my bios but it doesn't change anything.

Also did you experience problem with sound and with wifi? I got problem with but I solved them.
Do you have an HP-G62 AMD based or Intel processor based?
If somebody tell me how in french forum how to solve my problem, I will obviously post the solution here.

---

### Post by vegarg on 2010-08-30
I have the exact same problem as InTheSand with my Acer Aspire 7735Z.

Under Windows 7, it can run for hours on a full charge. Under Ubuntu 10.04 with a fully charged battery and AC power connected, it reports that the battery is old and needs to be replaced (something about 49% capacity). Once I disconnect AC power, it only lasts for about 15 minutes before it reports critically low battery charge and hibernates.

I would be very grateful if anyone has any suggestions for a solution or workaround.

-Vegar

---

### Post by jaapz on 2010-09-13
Just wanted to say ive got the exact problem on a HP G62-110SD

---

### Post by fozzytbear on 2010-09-15
bump

Fujitsu T5010.  This used to work by I just wiped the machine and installed 10.10 beta about a week ago.

---

### Post by switch10 on 2010-09-17
I am having the same issue on a dell mini 9.  The battery was reporting the correct charge before I ran an update on a fresh install of 10.04...

---

### Post by gmgj on 2010-09-24
I think I have same issue

On my Dell Lattitude D600
Plugged in - does not show battery level
unplug does show battery level

When plugged in I want to see Battery charge level.

I will post this in absolute beginners and see if I get a response.

---

### Post by gmgj on 2010-09-24
1)

If you do <alt>+f2 and type gconf-editor you can change more functions of power manager. Go to:
/apps/gnome-power-manager/actions

and check notify when fully charged

2)
when on battery, right click, find always display on icon

[http://ubuntuforums.org/showthread.php?t=1473084&highlight=battery+level](http://ubuntuforums.org/showthread.php?t=1473084&highlight=battery+level)

3)

also use Laptop (Dell) Fn keys , in  my case Fn + F3 shows battery

---

### Post by jaybok on 2010-09-25
Same problem here!  No issues until recent Ubuntu update(~3 days ago).  Here are my observations that DID NOT happen prior to the update:
(1) upon boot get "Your Battery has very low capacity" message,
(2) Battery icon is green upon plugin (before it was always gray with a "power-flash" in between),
(3) the icon takes a lot of time to recognise if switching battery to AC or back,
(4) completely incorrect battery-time and level message.

Have been searching and tried the gconf-editor stuff and nothing seems to work so far.

Any help?

---

### Post by Knowsnothing on 2010-11-23
Bump.

I'm on an Acer AspireOne 532h netbook.

I've had a problem for awhile where the indicator will mis-report the battery charge  as being critically low when I know it wasn't true.  The problem came and went.

But now, after fully charging the battery and having the indicator disappear (as per the preferences for a fully charged battery) when I unplug the AC cable, the indicator says I only have 76%.

AND, the above problem has been occurring more frequently.  I'm thinking the two things must be linked, but I can't find any documentation on how to fix this problem.  [noob talk]  Could it be a driver issue?

---

### Post by Dreamboat on 2011-02-03
I hit this too .. 

Sometimes battery shows last 10% left which is apparently true. And will alert me with a pop up window saying 'machine will go for hibernation if not plugged in'. 

But the funny thing is, even after I plug in the charger and click cancel button it takes me to hibernate after a few seconds. This is very disturbing, I have to boot again with power button and when it comes back the session will be alive.

Besides this sometimes it shows wrong battery information too. If anyone of you guys have a solution for this, please pass it on. Thanks.

---

