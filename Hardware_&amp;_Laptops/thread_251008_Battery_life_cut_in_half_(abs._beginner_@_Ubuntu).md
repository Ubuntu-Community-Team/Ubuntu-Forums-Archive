---
title: "Battery life cut in half? (abs. beginner @ Ubuntu)"
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by Mimsy on 2006-09-04
I love the fact that ubuntu runs faster on my seven years old laptop than WinXP does on a two years old machine. It zips around like a little sportscar now, and overall, it's turned from a uselss old relic into a really cool little machine.

There is one strange thing though, that bothers me very much. Yesterday, before I went through the "easy customization for beginners guide" and made sources.list available, made it possible for Firefox to run flash and videos in the browser, and so on, I have a battery life of about 2 hrs, in Ubuntu, as well as in WinXP, for the short time I used it before I switched systems. Today however, the green power manager icon tells me I have one hour of battery life, when it is fully charged. Huh??? What happpened to the other hour? :confused: 

I looked in Synaptic for power managment packages, but there are a bit too many for me to be able to make sense of the list, and I ended up more confused than I was before. The laptop is a Compaq Evo N410c, with the original battery.

Thanks,
Mimsy

---

### Post by meng on 2006-09-04
One question is whether your concern is that you actually have less battery life, or that the applet/icon is falsely telling you that you have less battery life. I would think the latter is more likely. I'm not sure how the applet estimates the remaining battery life, but my experience has been (with both Windows and Linux) that it is fairly hit and miss in terms of accuracy.

---

### Post by Mimsy on 2006-09-04
I think the applet being confused is more likely, since I don't see how the battery could have gone all wonky over night, without being severely abused. I'm running the laptop on battery right now, to see what happens when it goes down to zero. Will Ubuntu sit there with a confused look on its face as the laptop runs on, even though the battery is "dead"? Or will it act on the incorrect information and hibernate, as it has been told to do when battery life is critical?

If it does the latter then, in my mind, I have a serious problem. Is there something I can do to adjust or fix this?

Thanks again,
Mimsy

---

### Post by meng on 2006-09-04
I'd suggest a third possibility - that the battery "timer" counts down more slowly than you'd otherwise think.

---

### Post by Mimsy on 2006-09-04
I thought of that, but sadly, its minutes are just as long as the ones on my watch. :(

Update:
After the promised hour I got a message saying "battery discharging", or something similar, I don't remember the exact words. The laptop then went pssssh! and the screen went black. I'm typing from my desktop PC while the laptop battery charges again.

If this is a permanent change, it's a very bad one. Is there anything at all I can do, another package to install, some tweak I can attempt, that can fix this situation? Anyone? Please?

I really need the laptop to work for more than 45-60 minutes without the AC acapter plugged in.

Thanks,
Mimsy

---

### Post by dan.erasmus on 2006-09-05
the faster battery consumption might have something todo with the acpi settings!?!

is the CPU fan running all the time?

---

### Post by s0lar on 2006-09-05
You probably have to enable laptop-mode-tools. There is a wiki page about it.

---

### Post by Mimsy on 2006-09-05
The fan only runs occasionally, at least from what I can hear. I had the laptop shut down from over-heating once actually, so if anything it's not running often enough.

Laptop-mode-tools need to be enabled? Gotcha. I'll check out the wiki and see if that helps. Expect more n00bish questions as I trudge along. :)

Thanks!

/Mimsy

---

### Post by David Gerard on 2006-09-05
Tell you a weird thing that's happened to my N410c - my battery appears to have decided it doesn't like me any more. Battery life has gone down from about an hour to twenty minutes. I am rather annoyed by this ... but lithium-ion batteries do get clapped-out after a certain lifetime. How annoying (and expensive).

---

### Post by Mimsy on 2006-09-05
In other words, it might be age? Darn. I'm still going to try that laptop-mode-tools though.

/Mimsy

---

### Post by Mimsy on 2006-09-05
Another weird thing just happened. I unplugged the laptop from the wall outlet, mainly since said outlet is three buildings away, so right now I'm running it on battery power. Just as it came out of hibernation, I got the pop-up message that said: "Laptop is now running on battery power. Laptop battery 3 hours 22 minutes remaining."Laptop is now running on battery power. Laptop battery 3 hours 22 minutes remaining.(99%)"

Wtf? Wasn't it one hour this morning?

As I was reading the message, it changed to "Laptop is now running on battery power. Laptop battery 1 hour 6 minutes remaining.(96%)"

This is all weird.

/Mimsy

---

### Post by Titan_Prometheus on 2006-09-05
The Representation Is mathematical. I can't recall the exact location, but it take the current power of the battery and divides it by the current power comsumed. For the over all percent it just does Total power ever by power consumption. So it'll vary on time, but not on charge.

---

### Post by rsk on 2006-09-08
> **Mimsy said:**
> Another weird thing just happened. I unplugged the laptop from the wall outlet, mainly since said outlet is three buildings away, so right now I'm running it on battery power. Just as it came out of hibernation, I got the pop-up message that said: "Laptop is now running on battery power. Laptop battery 3 hours 22 minutes remaining."Laptop is now running on battery power. Laptop battery 3 hours 22 minutes remaining.(99%)"

Wtf? Wasn't it one hour this morning?

As I was reading the message, it changed to "Laptop is now running on battery power. Laptop battery 1 hour 6 minutes remaining.(96%)"

This is all weird.

/Mimsy

Mimsy,
I just ran across this thread because I have a brand new ThinkPad T60 with a 9-cell battery and the 3-cell Ultrabay battery all plugged in and the battery applet (battstat) that comes on under a normal Ubuntu install has gone completely retarded on me.

First time I booted the machine with just the 9-cell it said 5hours remaining, then I shut it down added the ultray bay and booted it up. I decided to charge the ultrabay so I plugged in the AC cord, then it said "2hrs to full charge", an hour later, it said "1hr to full charge" and 1 more hour after that it said "4 hours to full charge".. cute.

So now when the battery is running down, the time estimates it gives are all over the place. The computer has had "1hr 15mins of life remaining, 34%" for the last hour, the time keeps ticking down, but the battery icon seems somewhat more sane/accurate.

I'm doing a full charge right now after a full discharge and see how it looks after that.

I've been playing with battery/power saving stuff all morning, i'm going freaking nuts over here. It looks like Novell has the most advanced power saving library right now, powersaved, but of course not everyone agrees on the underlying mechanism it uses. The Novell/KDE folks agree that it should all be done through DBus, so they use that. The Gnome folks think it should all be done through HAL, which is what gnome-power-manager uses.

All I can tell after playing with ALL this stuff, is that I don't think I care anymore. I'll just use gnome-power-manager along with the CPU monitor applet to make sure my CPU's are adjusting their speed correctly and then go lookup why my fan won't stop spinning and I'll be happy... if I feel brave, I'll try and get ATI power play working automatically, right now the power saving works, but I have to set it manually =(

---

### Post by rsk on 2006-09-08
FYI, I just found a quick way from the console to tell the status of your batter(ies):

```
rkalla@rkalla-laptop:~$ cat /proc/acpi/battery/BAT0/state
``` > present:                 yes
capacity state:          ok
charging state:          charging
present rate:            41266 mW
remaining capacity:      46380 mWh
present voltage:         11906 mV
 ```
rkalla@rkalla-laptop:~$ cat /proc/acpi/battery/BAT1/state
``` > present:                 yes
capacity state:          critical
charging state:          charged
present rate:            0 mW
remaining capacity:      0 mWh
present voltage:         11222 mV
 
hmmm so my ultrabay batteryis charged WITH a 0mWh capacity... interesting.

I better post a new thread about this :(

**Update #1:** It seems according to [this Thinkwiki entry](http://www.thinkwiki.org/wiki/How_to_use_UltraBay_batteries) that the ultrabay battery is always filled last and discharged first, so that might explain the weird status (although I still don't understand the "charged" state).

Also it says that gnome-power-manager already correctly adds both battery status together, so I'm just going to let the computer sit here and fully charage up until it's maxed out, then I'll hvae a look at the power status again.

---

### Post by Mimsy on 2006-09-08
Thanks for all the details, rsk. I'm still trying to figure out what is going on, and what confuses me the most is that the energy shortage is consisten... it starts at the same number each time, ticks down at the same rate each time, and then shuts itself off due to low battery power.

Of course, I could just have a very bad battery. It is 7 years old after all. I have tried the full discharge - full recharge method, but it didn't change anything, that I could tell.

As the weekend comes up and I'll have more time to experiment, I'm going to play around a bit more with the battery and especially the gnome-power-manager.

Thanks,
Mimsy

---

### Post by rsk on 2006-09-08
My experience with Linux thus far is that out of the box it is going to give you poorer power savings without some elbow grease than Windows. So if your battery lasts 2 hours in Windows, having it (out of the box) last 1 hour in Linux sounds reasonable to me.

As far as the times going haywire, this occured even on my macbook pro, I would boot after a full charge, 4hrs remaining, then 10mins later, it will be 2hrs and 30mins remaining. Drove me nuts. All I know is that the litle icon thing in the task bar was usually right, same seems to be the case with ubuntu, the numbers go haywire depending on what you are doing.

I've since installed all the power management stuff for my video card and processors (no luck with the fan, I'm hoping it will shut off now that the vid card stuff is installed)

ALSO, the most important part, your battery is 7 years old, I'm amazed it still *runs*, so I would point the finger at that before anything else.

Also I don't know if your machine is going to support all the ACPI/HAL power saving stuff, so it may be running full tilt from start to finish, which would also explain the poor battery life.

---

### Post by Mimsy on 2006-09-08
> **rsk said:**
> 
ALSO, the most important part, your battery is 7 years old, I'm amazed it still *runs*, so I would point the finger at that before anything else.

Yes, this has occurred to me. :-)

However, the battery did run for two hours when Ubuntu was newly installed, and it wasn't until after a few days that it went down to one hour over-night, which is why I am puzzled. I would expect an old tired battery to gradually fade away...

/Mimsy

---

### Post by rsk on 2006-09-08
Hmm that's a good point, I must have missed that part. I would be confused too.

Did you say something derogatory infront of it? Maybe it's just mad at you? :)

---

### Post by Mimsy on 2006-09-08
Hmm. Good point. :-)

But no, I don't think it has any reason to be mad at me. I even defend it against derogatory comments from its previous owner about how it is an old piece of junk... Maybe it overheard me comment on how cool it would be to run Ubuntu on a Macbook, and now it thinks I'm planning to replace it?

/Mimsy

---

### Post by An3Azz on 2006-09-14
What are the specs of the Evo 410, I own an Compaq Evo 600n, will check my battery life this evening, for comparsion. Maybe we have the same battery? My battery last about 3.10 hrs in windows...installed ubuntu on the machine yesterday.

---

### Post by Mimsy on 2006-09-15
Well, I have a Pentium III CPU, 256 MB of RAM, and I would rather not rip out the battery to check the serial number right now. Would you mind specifying what type of specs you're after, so I can find the details?

/Mimsy

---

### Post by Mimsy on 2006-09-15
To my great surprise and joy I have temporarily become a bit less poor, and I may even be able to buy a memory upgrade for my N410c. My question to those who know more about hardware than I do is, will a memory upgrade affect battery life?

Thanks,
Mimsy

---

### Post by David Corrales on 2006-09-15
I might add that something that really affects battery life is the display. Actually, it's the #1 battery draining source :)
If you're using ATI propietary drivers, you can use a utility called **aticonfig** to check all the available power states: **aticonfig --lsp**
and to change them, **aticonfig --set-powerstate=#**, where # is the number of the powerstate you want to change to. This setting alone gives me around 45 more minutes of extra battery!
I think there should be something similar for nvidia/intel cards also so you might want to look for those if you don't have an ati card.

Another thing that windows does usually is turn off the wired nic if you're on battery (you can turn it on manually) and that also helps. You should disable the wireless nic unless you're using it also, it drains some power too.

Finally, enable the laptop-mode tools like it was said before, that usually helps with the HD eating too much battery.

All in all, I think stuff like this should be enabled by default whenever it's available to make our battery lives longer.

Edit: I forgot to add that Edgy has a 2.17 kernel which has improved power saving features and also Gnome 2.16 which has a much better power management interface. I'm upgrading to it after it comes out and the initial bugs get squated.

---

### Post by Mimsy on 2006-09-16
Okay... let me check out the disply drivers and ge back to you. This is a  pre-built system that used to belong to someone else, so I'm barely done checking out hardware numbers and what I have to work with, in terms of chips.

Again, I'll get back to you sometime tomorrow.

/Mimsy

---

### Post by Mimsy on 2006-09-16
> **rsk said:**
> FYI, I just found a quick way from the console to tell the status of your batter(ies):

```
rkalla@rkalla-laptop:~$ cat /proc/acpi/battery/BAT0/state
```  ```
rkalla@rkalla-laptop:~$ cat /proc/acpi/battery/BAT1/state
```  


Continuing the evening's quest of reviving old threads, I went back and tried these commands. My terminal said 

> cat: /proc/acpi/battery/BAT1/state: No such file or directory

I'm a bit confused now. I assume I must have typed in the wrong path, since I'm pretty sure I do have a battery, but how do I find the right path?

Thanks,
Mimsy

---

### Post by canardo on 2006-09-18
Hi I also have a EVO n410c which suffers from appaling battery life, in the slow process of getting all the drivers to work properly 

you battery is actually here [Cl8B through to C18E] holds 4 batterys if you use the meu

cat /proc/acpi/battery/C18B/

---

### Post by Mimsy on 2006-09-18
My problem when it comes to making this work, is that I have no idea how to find drivers, how to install them or even what I need rivers for. In Windows I could find tht information, but in Ubuntu I have no idea where to look for it, and where to look for the drivers once I have the part numbers. I'll be more than happy to imitate everything you do though. :)

Thanks for the battery path! I'll try it out when I get home tonight.

/Mimsy

---

### Post by Mimsy on 2006-09-19
At last I've had time to sit down and work at this and try to figure it out. Sadly, I failed. I think I need very detailed "Laptop-mode-tools for Dummies"-type instructions. The only instructions for enabling them that i could find were for Hoary, and the commmands didn't work in Dapper. And how do I stop it from accessing the hard-drive every two seconds?

Thanks,
Mimsy

---

### Post by parsons151185 on 2006-09-19
I don't know what your telling about but perhaps its todo with the acpi settings as Dan.erasmus said. I have an Fujitsu Siemens fitted with a AthlonXP 2600+ and 786MB DDR333, the battory life is around 40 mins on Windows but put Linux on it and it can last more than 2 hours. I havent 'tweaked' Ubuntu at all, Im not very use to Linux, I have used Windows for fare tolong and have been trying to find the right Distro to goto, Personaly I think I have found it, either this or Dedian.

---

### Post by canardo on 2006-09-19
Ive given up for the moment Mimsy the most important bit I found is  to install the correct graphics card  driver M6 (theres a how to in the tips and tricks section)
and then goto /etc/default/acpi-settings and enable laptop mode

this did give me nearly comparable life to windows but not enough and I suffered the same annoyance as you which was the drop out when you reach 40% to it suddenly dying (this is a 2 week old battery so it isnt that)

Hopefully Edgy and the update to Gnome 2.18 will solve the problems, I have had a go with knot 3 and its a lot better so fingers crossed, my transition back to windows will only be for a few more weeks. 

As a side note it has taken me longer to get to a functional machine (ie with wireless belkin f5d7010 and everything installed ) with windows than ubuntu, mainly due to automatix, and I dread the slow down that is inevitably going to occur(should last till edgy!)

---

### Post by Mimsy on 2006-09-19
I am reluctantly accepting that I have to switch back to Windows as well, while I wait for this to be fixed. What is even more frustrating is that I have an application, a game-like program that simply won't work. I have tried wine, I have tweaked and ran from terminal (and I've had great help from a number of very patient forum members!), and I now have to accept that most likely the application simply can't handle Ubuntu.

I am grudgingly switching back to Windows. For now. As soon as Ubuntu stops eating my laptop battery alive, I'll be back. Tweaking the game-thing was more fun than annoying, but I have to have decent batterylife.

But I'll be back!

/Mimsy

---

### Post by gn2 on 2006-09-20
Have you looked in the BIOS?

My Portege 3440CT has user-configurable power management settings in the BIOS, and changing it seems to have affected how Ubuntu manages things.

Now get four hours on (long-life) battery same as with W2kPro.

---

### Post by Mimsy on 2006-09-20
Not yet... where do I find that in Ubuntu? More importantly, what do I need to look for/change/change it to, et cetera?

Thanks,
Mimsy

---

### Post by gn2 on 2006-09-20
To get into the BIOS restart and press F10 as it re-starts.
This will take you to the set-up screen.

Do you have any buzzing when the laptop's running?
There was a known problem with this model's voltage regulator...

But it's most likely that it's new battery time...

Batteries can be envigorated by fully discharging put it in a waterproof bag and place in a deep freeze for 24 hours.
Let it come up to room temperature then fully charge it with the laptop switched off.
Then disconnect AC Adaptor and run laptop till flat.
Repeat.
Have tried this trick myself with mobile phone battery and it worked like new again.

---

### Post by Mimsy on 2006-09-20
> **gn2 said:**
> Batteries can be envigorated by fully discharging put it in a waterproof bag and place in a deep freeze for 24 hours.
Let it come up to room temperature then fully charge it with the laptop switched off.
Then disconnect AC Adaptor and run laptop till flat.
Repeat.
Have tried this trick myself with mobile phone battery and it worked like new again.

Neat. I have to try that! The battery is seven years old, after all. It'll probably appreciate a little viagra. :)

And I'll give F10 a shot tonight, when I am home again and have access to the laptop. (It doesn't go to work with me, since it gets carsick very easily.) After all, I have current backups of everything, so what's the worst that can happen, right? 

And yes, it does buzz now and then, but it sounds a lot more like fans or accessing the hard drive. If it was the voltage regulator, wouldn't the buuzz be consistent?

/Mimsy

---

### Post by gn2 on 2006-09-20
The buzz needn't be consistent as it can change as the load varies.
Doesn't do it in windows safe mode, which runs with lower load for example.
HP Compaq forums worth a look too.
Have you tried a different distro yet to eliminate that as a possible cause?

---

### Post by Mimsy on 2006-09-20
I haven't tried any other distributions, though the thought of course crossed my mind. Once the semester is over and I have this exotic thing called "free time" that I have heard legends about, I probably will though, if I can't get things to work right in Ubuntu. I barely have time to figure Ubuntu out, and I'm too new to Linux to be able to do things fast yet. ;)

HP Compaq forums is a good idea, I'll have to check that out as well... unless the BIOS tweaking works, of course.

/Mimsy

---

### Post by canardo on 2006-09-20
Hi Mimsy I am convinced this isnt a battery problem though you are doing well with it being 7 years old (this isnt me I have brought two batteries from them though on ebay do a search for the user hkbay86).

I am convinced this is an issue with gnome 2.14 and the gnome power manager, as Suse (kde) does not seem to cause it I imagine because KDE doesnt use the HAL method of interacting with acpi, and neither does Windows, I am back up to 4 hours life in windows but more importantly I dont get the weird drop out where the battery will suddenly die.

I will watch this thread with intrest though as would much prefer to have a working Ubuntu on my laptop (my main machine runs perfectly) however as I currently need it for work, having to bite the bullet and go back to windows, hey maybe when I am finished on my current project, I can help the Ubuntu project, rather than just moaning as I am a Java software dev so hopefully could contribute some how and fix this problem for both of us

---

### Post by Mimsy on 2006-09-20
Wait... does that mean Suse or any other kde system might not eat the battery alive?

Possibilities, possibilities... :)

/Mimsy

---

### Post by canardo on 2006-09-20
in my experience yes KDE fixes the problems i havent tried kubuntu, am just waiting for edgy

---

### Post by Mimsy on 2006-09-20
Well, now I know what I'll be doing tonight. KDE desktop on Ubuntu! If that doesn't work, Kubuntu. If that doesn't work, BIOS tweaking. If that doesn't work... Windows... :(

But I'll try whatever else I can think of first. Every time I have to install Windows I loose six hours of my life, and they can never be reclaimed.

/Mimsy

---

### Post by Mimsy on 2006-09-22
Brief statusreport/update:

KDE:
I downloaded and installed the kubuntu-desktop packages. Not noticable increasein battery life at all.

Kubuntu:
I was so appalled and horrified by the desktop interface that I didn't even bother with installing the full system. With Gnome, I took one look at it and it was gorgeous. With Kubuntu's deksopt, not so much... bleh. Ugly. And not at all fun to work in either.

BIOS:
No user-configurabe settings for the battery. Or for anything, for what I could find. At least I did learn that the previous owner exaggerated the laptop's age. It is four and a half years old, not seven. :)

So it looks like I either will have to switch to another distribution, or switch back to Windows. On general principle, I refuse to getrid of Ubuntu after all the time I spent on configuring it... but it frustrates me that there seems to be now solution to the battery situation.

/Mimsy

---

### Post by PlasticZak on 2006-09-22
Battery life comes from little things together. I installed flashblock for Firefox. Flash animations use the CPU which in turn eats your battery.

I have the feeling that not running the esd sound server gives me a few extra minutes. Not loading unneeded drivers (which could mean the hardware remains off) can save a little as well.

The tiny bits add up. I think that a working ACPI is crucial. Try a dmesg | grep -i acpi to see if there are any errors. Look in /proc/acpi/processor/CPU1/power to check if C-states (sleep states) are available and if at least the C2 sleep state is being used if it is available. If not there may be something in the way. Although I do not know which CPUs support which states or even if the states have the same meaning across BIOSes.

Oh yes, try to get rid of as many desktop gadgets as possible. Those nift system load graphs can do a lot of work in the background, again eating the CPU.

---

### Post by Mimsy on 2006-09-22
> **PlasticZak said:**
> 
Try a dmesg | grep -i acpi to see if there are any errors.

How do I know that? What am I looking for?

I don't have a file at /proc/acpi/processor/CPU1/power, but I have /proc/acpi/processor/C000/power. It's blank.

/Mimsy

---

### Post by Mimsy on 2006-10-15
For a number of reasons, over-enthusiastic playing with things I don't understand being the most prominent one, the laptop started to refuse to boot. Sometimes it did, sometimes it didn't. It was an interesting little adventure to press the button and see if anything would happen or if I needed to try again or not...

So I wiped the harddrive and prepared for a reinstall, then realised that this would be a good time to install WinXp and update the BIOS, before reinstalling Ubuntu. So I did that as well, hoping for battery-management tools. I also did some tweaking around in WinXP while I was at it, and here's what I found:
The battery's active life is just as short in WinXP as it is in Ubuntu.

This is GREAT NEWS, because it means I don't have to go back to that horrible  Other OS to get a longer battery life, I can stay with Ubuntu. :-D

And now I am going to go find a ziploc bag and put the battery in the freezer for a while.

/Mimsy

---

