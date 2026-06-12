---
title: "[SOLVED] Processor Fan and Inbuilt Memory Card Reader problems."
date: 2008-12-04
forum: Hardware
---

### Post by jdc.84 on 2008-12-04
I hate windows and refuse to spend the stupid amounts of money on an 'apple'. I also do not want to become an "Apple boy"!

...I really want Ubuntu to work.

I have just installed Ubuntu 8.1 onto a laptop which is around 4years old:
Fujitsu Siemens Amilo M 1420 from late 2004.



Everything seems to work perfectly except for two things:

1. The built in card reader at the front which i use everyday cannot be seen. I went back into windows to find out what driver it was using to run the card reader (i've attached a screenshot [i hope] of the device manager relating to the card reader) but it said it was just using a standard driver. 
Does anybody know how i can get Ubuntu to see the card reader?

2. The processor fan now comes on and stays on for the majority of the time. Fujitsu Siemens had the sense to build in a seriously annoying fan with a high pitched noised which makes you want to throw the computer out the window. 
Does anyone know of any way of controlling the processor fan?


Any help would be very much appreciated.
Thanks.
John.

---

### Post by andreasis on 2008-12-04
I found this [https://bugs.launchpad.net/ubuntu/+bug/153174](https://bugs.launchpad.net/ubuntu/+bug/153174)

do you have the same memory card controller as that user?

does lspci produce this line?:

Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)

---

### Post by jdc.84 on 2008-12-04
Hi,

No. The only line which relates to the card reader is:

02:04.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller

---

### Post by jdc.84 on 2008-12-04
oh sorry and...

02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 01)

---

### Post by andreasis on 2008-12-04
I've checked out launchpad and other website and I've come across bad news for you: 

[https://lists.ubuntu.com/archives/kernel-bugs/2008-February/031738.html](https://lists.ubuntu.com/archives/kernel-bugs/2008-February/031738.html)

which refers to this bug:
[https://bugs.launchpad.net/bugs/31440](https://bugs.launchpad.net/bugs/31440)

You may want to check out alternatives like usb card readers (really cheap on ebay).

Now, in regards to your fan issue.. I'm assuming of course that you have the latest bios installed.

I've looked at these and more:
[http://www.amilo-forum.com/topic,46,-Amilo-M1439G-Fan-Problem.html](http://www.amilo-forum.com/topic,46,-Amilo-M1439G-Fan-Problem.html)
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/57617](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/57617)

It seems to be an ongoing bug.

I would suggest trying two things:

(1) would be to try and control the fan through the graphic driver:

Taken from aticonfig man page:

POWERplay Options:
Following options will not change the config file.
These options will be effective immediately. Other options on
the same command line will be ignored.
--lsp, --list-powerstates
Print information about power states and exit.
--set-powerstate=NUMBER
Set a power state listed by --list-powerstates.

If that doesn't work, I would suggest controlling the cpu clock and seeing if that affects the fan speed. You can do this by right-clicking on the upper panel > add to panel > cpu frequency scaling monitor. Once this applet is on your panel, you should be able to see/set the cpu speed (since you have a pentium m, which supports cpu scaling)

I have a Dell D600 which has the same problem as your laptop, except that there is a a tool (dell specific - i8kfan) that allows the user to control/ turn off the fan.

This is all of the help that I think that I can provide.  If you think that I (or even anyone else) can help you further, feel free to reply with further questions/concerns.

~

---

### Post by jdc.84 on 2008-12-04
Hi, thanks for the help. 

I added the cpu monitor to the top panel, dropped the freq from 'on demand' to a few different settings. I can now get the fan to stay off for around 5mins, but then it comes back on for 5mins.

I am myself a complete novice with all of this, a quick leaner but novice none the less:

I haven't installed the latest bios, is it complex?
Also i didn't understand what you meant with the:

Taken from aticonfig man page:

POWERplay Options:
Following options will not change the config file.
These options will be effective immediately. Other options on
the same command line will be ignored.
--lsp, --list-powerstates
Print information about power states and exit.
--set-powerstate=NUMBER
Set a power state listed by --list-powerstates.



If updating the bios and the latter are things i should know about before trying to fix this problem could you possibly point me in the direction of a site that could explain?

Once again thanks for the help so far, very much appreciated!

---

### Post by andreasis on 2008-12-05
Skiing around the Fujitsu website I was able to find two bios versions for your laptop.  v1.25 and v1.26

Do you know which one you have? (Both versions are dated 2004) [http://www.fujitsu-siemens.com/support/downloads.html](http://www.fujitsu-siemens.com/support/downloads.html)

If you have the latest bios update it's more likely that some issues may have been fixed.

It doesn't seem too complex. They're ISO images so it would involve downloading them, burning the image to a cd, restarting the computer, booting from the cd, and letting the cd do the rest of the work.


I find it very interesting that your fan is turning off after you've set the cpu scaling to ondemand, because that is the same story behind my D600, which has the pentium m 1.6ghz chip.  As I'd first installed Ubuntu, the fan was spinning non-stop so fast that I thought the notebook would take off if I didn't rest my arms on it (fan's on the bottom).  It turns out that it's actually a fault in the pentium m chips.  They like to overheat.  As I further investigated my issue, I found out that my temperature reached up to 94 degrees celsius, which is absolutely preposterous for even the most overclocked desktop cpu's. 

I hope to get a temperature monitor on your system to see the temperature range of your cpu, and possibly test a few programs in the hopes that one of them is able to communicate with either your cpu or your video card (which is a good ATI 9600/9700).

This is just an interesting thread: [http://ubuntuforums.org/archive/index.php/t-62578.html](http://ubuntuforums.org/archive/index.php/t-62578.html)

Go ahead and try these programs. They may or may not all work, but I'm holding my fingers crossed that one of them will.

From Synaptic Package Manager, you can do a quick search for temperature.

try computertemp
after you install it, you'll have to add the applet to your upper panel to see it in action. 

if it doesn't work, uninstall it from Synaptic.
then, to uninstall the dependencies that were installed for this program, go into terminal and type 
```
sudo apt-get autoremove
```
(this is standard procedure for removing any and all files on the computer that are not needed / serve no more purpose.

other programs of interest are

mbmon
lm-sensors (which you can install in conjunction with sensors-applet so that you can just put an applet in your panel)

of course, if these don't do the trick, then you can use the same procedure as above to remove them and their dependencies.

This is what other users in your position are saying: [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/57617](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/57617)

As the last post on that page implies, a solution could be obtained by instructing the fan to turn off when reaching a certain minimum temperature.

I found this on another thread [http://ubuntuforums.org/showthread.php?t=381267:](http://ubuntuforums.org/showthread.php?t=381267:)

```
echo "5" > /proc/acpi/thermal_zone/THRM/polling_frequency
```

Also try following Eversmann's instructions in the thread (the last post) and see if that does anything.

[EDIT]

The instructions below are for the program "aticonfig" which, as I understand it, is part of the ati driver for linux. 

So each of the following options would be prefixed by aticonfig

--lsp, --list-powerstates
Print information about power states and exit.
--set-powerstate=NUMBER
Set a power state listed by --list-powerstates.

Under ideal circumstances, assuming that the graphic card has some control over the fan, 
```
aticonfig --lsp
```or```
aticonfig --list-powerstates
``` would give you some options, which you could apply with ```
aticonfig --set-powerstate=#
``` where # is one of the power states that was listed with the previous command.  I don't see much discussion about this alternative, but I thought it would be worth a shot.

**And while we're talking about intersting ideas, see what happens if you boot from the live-cd with the command acpi=off [http://ubuntuforums.org/showthread.php?t=83770](http://ubuntuforums.org/showthread.php?t=83770)

---

### Post by jdc.84 on 2008-12-06
andreasis,

Thanks for the update on the thread it made a lot more sense to me, i am now starting to get to grips with the whole concept of Ubuntu.

I tried using the computertemp and mbmon with no success.

I then tried typing in, aticonfig --lsp:
The terminal then told me to install ati which i did.
After installation i then preceeded to try the powerstate commands.

Somewhere along i got amongst a huge page of scipt:

--lsp, --list-powerstates
Print information about power states and exit.
--set-powerstate=NUMBER
Set a power state listed by --list-powerstates


The terminal also read at some point (something like [it was quite late at this point]):
POWERplay innactive
or/
POWERplay unavailable.


When i now try to log on Ubuntu it keeps on saying that the computer will be running in low graphics mode.

I have now accepted defeat with this laptop. I will be wiping the HDD again, reinstalling the windows image and reinstalling the Ubuntu OS, then selling the Laptop.


Thanks again for all you help,

John

(I really want to be able to get to grips with Ubuntu. I will be buying a new laptop to replace this one, if you can offer any advice as to a make and model which runs quietly with no problems on Ubuntu?)

---

### Post by andreasis on 2008-12-07
John,

I'm very sorry to hear about your newfound grief, and this result is definitely not the outcome that I was rooting for.

I believe that the low graphics mode problem is due to a certain ati (fglrx?) driver that you may have installed, which would make sense to be a dependency of the aticonfig program, which appears to have upset your graphic card.  This is reversible, of course.

I am guessing that the last option in the post didn't help either.



You will read everywhere that laptops are purely an object of personal preference, the same with linux.  I disagree with those analogies to an extent, because some options are always better than others, depending from which perspective they're assessed.

nvidia has exponentially better support for linux than ati and they release new updates and features for their drivers as frequently as on a weekly basis ([http://www.nvnews.net/](http://www.nvnews.net/)).

AMD-based laptops tend to carry a lower price tag, but consume more power than their intel counterparts, and that comes at the expense of hotter running cpu's, decreasing battery life (and, since AMD owns ATI, these laptops sport AMD graphics) I will not list a source or link for this, because the opinion on the internet is unanimous in this regard.

I tend to stay away from dell for their overheating issues (they like to place their fans on the bottom of the laptop, which leads to decreased airflow, which in turn leads to the fan having to work harder). I have yet to meet a person that does not have a heat-related complaint about their dell laptop.

An excellent resource for laptop reviews and popularity rankings is [http://www.notebookreview.com/](http://www.notebookreview.com/)
I find them to offer solid reviews with many pictures and personal observations.

In regards to a brand/model recommendation... it wouldn't be just of me to do that.  I understand that a memory card reader is important to you, so once you'd find a laptop in your price range with the features that you like, I'd google for any problems that others may have had with the card reader or any other aspect of the notebook.

The reason why I switched over from windows to linux was because I wanted every program to do what I would tell it to do, and not what it thought would be in its better interest, and more importantly because of the large security loopholes which would enable spyware and other malicious programs to infect a computer regardless of the antivirus/antispyware protection actively running in the background.

Thanks to the many roadblocks and obstacles that I had to overcome, I am now able to have everything on my computer do what I need it to do, when and how I need it to be done.

I have shared this with you because I don't personally know a single other person that has managed to stay motivated enough to make a firm transition to linux, without turning around and running back to windows. I want to encourage people to transition because of the above reasons, and I want to encourage you to ask me anything, even if it's pertaining to a specific laptop that you're keen on getting.

Another way to look at the equation, is by taking into the account the three things (excluding design flaws) that contribute most to the heat, power consumption, and noise on laptops: CPU, Hard drive, graphic card (gpu).

Intel Core 2 Duo specifications: [http://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#Core_2_Duo_2](http://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#Core_2_Duo_2)
You can look up the cpu of a laptop that appeals to you on this list or other lists located at the very bottom of the page and see how many watts it consumes.

On a final note, I think you have a very nice laptop, and it may just be worth keeping windows on it, as you do use the card reader often, and the fan isn't as bad in windows.....

Best of luck with whichever road you decide to take.  I'll be here if anything.

Andreas

---

### Post by Zaunmayrchris on 2009-01-04
here is a howto that should solve the cpu-fan problem:
[http://s3.enemy.org/~zaunmayc/speedstep8.04.html](http://s3.enemy.org/~zaunmayc/speedstep8.04.html)

cu
      CHristoph

---

