---
title: "Toshiba sat. M115: lcd brightness and battery power"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by mortoss on 2006-12-18
Hi,

I' ve installed Kubuntu EE on my toshiba m115 laptop. Almost everything works OOB. CPU scaling needed some tunning but now works greate :). Even WiFi astonished me with configuration simplicity. But... There are some problems too: 

I have no idea how to control lcd brightnes. It's pretty important when on battery power.. I've googled for weeks after any clue and found nothing that works... (not omnibook, not omke, not even toshiba_acpi, kernel recompilation failed - perhaps because of lack of my experience...) Do You have any ideas what else could be made?

Second strange thing is:
When I turn the laptop off from linux (shutdown command or button). It seems that notebook shuts down (no LEDs, no any sound, etc..) Seems ok? Yes but .. after 24h battery state is ~60%? Why? When powering off from windows - after 24h - battery is 100%? Strange... (pls don't try to proove that I'm confusing stanby and shutdown... Standby in windows is LED indicated etc...)

Thx!

---

### Post by mortoss on 2006-12-19
....overnight test - after shutting down from windows (20h before) - battery remains full ?!?

---

### Post by darkstar62 on 2006-12-29
> **mortoss said:**
> Hi,

I' ve installed Kubuntu EE on my toshiba m115 laptop. Almost everything works OOB. CPU scaling needed some tunning but now works greate :). Even WiFi astonished me with configuration simplicity. But... There are some problems too: 

I have no idea how to control lcd brightnes. It's pretty important when on battery power.. I've googled for weeks after any clue and found nothing that works... (not omnibook, not omke, not even toshiba_acpi, kernel recompilation failed - perhaps because of lack of my experience...) Do You have any ideas what else could be made?

SNIP

I've been seeing the same problem.  I've traced down where the brightness value is held (it's in the embedded controller, address 0xA3, taking a value between 0x00 and 0x07), but nothing happens when I change this address.  There's something still that has to kick the EC to get it to apply the changes.  Not sure what yet though.  Anyone have any ideas?  For reference, this is a Phoenix, not Toshiba, BIOS.

In theory, using the omnibook module with ectype=14 *should* work, but because it isn't sending the right "apply" command, it doesn't work.

Just my two cents.

- Cory

---

### Post by katabatic on 2007-01-14
I also have a Toshiba M115 with a Phoenix BIOS.

ANYBODY???

I really need to be able to dim the screen, too! And maybe make the FN hotkeys work.

---

### Post by katabatic on 2007-01-15
Please.

---

### Post by katabatic on 2007-01-16
.

---

### Post by katabatic on 2007-01-23
.

---

### Post by mortoss on 2007-01-24
Spaming in this thread won't help. If U are really interested in finding solution as I am - write an email to toshiba. We should be their 'pain in the neck ' :guitar: They should care about linux community.. ](*,)

---

### Post by katabatic on 2007-02-23
I got it working! I have just read this post: [http://www.orangegroove.net/articles/2007/02/08/toshiba-linux-and-lcd-brightness-2/](http://www.orangegroove.net/articles/2007/02/08/toshiba-linux-and-lcd-brightness-2/)
and decided to give it a try. I went on the Toshiba website and got the BIOS update for my model (M115-S3094). The update requires Windows to either write it to a disk or to update directly. I did the direct Windows option from their program as I dual-boot.

After update, I did ```
cat /proc/acpi/video/VGA/LCD/brightness
```
and got:

levels:  75 35 10 25 35 50 60 75 90 100
current: 0

Those are the brightness levels.

So, I did: ```
echo 10 | sudo dd of=/proc/acpi/video/VGA/LCD/brightness
``` to set the level to 10

And it freakin worked! I hope this helps and works for you. I'm not sure if it was the BIOS update, but I assume so. I don't think I tried this before updating.

:guitar:



If you would like to change the brightness automatically when the battery is used, you can use a simple script.

Here is how I did it:

Using sudo nautilus or sudo konqueror and sudo gedit or sudo kate will make it easy.

I had to turn on laptop-mode by going to /etc/default/acpi-support and making ENABLE_LAPTOP_MODE=TRUE
I've read it could also be in /etc/defaults/acpi-settings

Then, go to /etc/laptop-mode/batt-start and batt-stop

And put in a script in batt-start containing: ```
echo 10 > /proc/acpi/video/VGA/LCD/brightness 
```

And a similar one in batt-stop containing ```
echo 90 > /proc/acpi/video/VGA/LCD/brightness
```
Or any value you want for brightness.

Now, right-click each script, Properties, and check "Is executable" or something similar as I am in Kubuntu. May need to reboot now

---

### Post by mortoss on 2007-02-24
Thanks!!!! :popcorn:   

After flashing bios - 'made for vista' - changing brightness works in ubuntu :D  Thanks again!


**SOLVED**

---

### Post by katabatic on 2007-02-24
Great!

So how did you get your CPU frequency scaling to work on your M115?

---

### Post by mortoss on 2007-02-26
I followed instructions from [http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)

As a kernel module I use 'speedstep-centrino', as a managing program 'cpufreq'. To change governor
 ```
cpufreq-set -c 1 -g ondemand 
 cpufreq-set -c 0 -g ondemand
```

as cores could be menaged seperatly :)

---

### Post by Tom Tiger on 2007-02-26
Great work!  Thank you for posting.  :)

---

### Post by mortoss on 2007-02-26
One more question?

Does Your microphone-in work in linux? I've got troubles with that...

---

### Post by katabatic on 2007-02-26
I do have a problem with the microphone. I listened carefully, and it does actually record sound but very very faintly. If you find how to fix that, let me know.

---

### Post by katabatic on 2007-02-26
If you would like to change the brightness automatically when the battery is used, you can use a simple script.

Here is how I did it:

Using sudo nautilus or sudo konqueror and sudo gedit or sudo kate will make it easy.

I had to turn on laptop-mode by going to /etc/default/acpi-support and making ENABLE_LAPTOP_MODE=TRUE
I've read it could also be in /etc/defaults/acpi-settings

Then, go to /etc/laptop-mode/batt-start and batt-stop

And put in a script in batt-start containing: ```
echo 10 > /proc/acpi/video/VGA/LCD/brightness 
```

And a similar one in batt-stop containing ```
echo 90 > /proc/acpi/video/VGA/LCD/brightness
```
Or any value you want for brightness.

Now, right-click each script, Properties, and check "Is executable" or something similar as I am in Kubuntu. May need to reboot now

---

### Post by mortoss on 2007-02-27
> If you would like to change the brightness automatically when the battery is used, you can use a simple script.

Does it work with tosh M115? No hangs or sth?:confused:

---

### Post by katabatic on 2007-02-27
Yeah, I have an M115. Is it not working for you? One thing is that laptop-mode can adjust cpu frequency. Maybe it's conflicting with the other way you did it? You can turn off the CPU frequency control in laptop-mode config.

---

### Post by mortoss on 2007-02-27
I'll try enabling laptop-mode after backing up disk image :)  

btw: is Your M115' microphone input working correctly?

---

### Post by katabatic on 2007-02-27
> **mortoss said:**
> 
btw: is Your M115' microphone input working correctly?

Already answered. Nope, it is not working correctly in Linux.

---

### Post by Solicitous on 2007-03-03
Well I followed the bios update tip and now my toshiba m110 brightness adjust works using the cmdline command.  Thanks.

FYI if you're interested, I tried out the Feisty cd last night (Herd 5 I think) and the FN-F6/F7 brightness keys work.  Not perfect, occasionally the screen will blank going up or down, but another press will bring the screen back up.  Perhaps it's passing unknown brightness levels to the screen now and then, but for useability it works better than always dropping to the cmdline.

Now has anyone managed to get sound to come back up after resuming from sleep/hibernate?  Currently the only way I've been able to do it is after resuming is to kill the mixer_applet2 process,  then reload the sound module.

---

### Post by katabatic on 2007-03-15
Feisty does indeed appear to be working better with this laptop. I'm having that sound issue after suspend, as well.

---

### Post by Solicitous on 2007-03-18
Are you able to get sound working again after suspend/hibernate?

FYI the process I follow is;
Once I've logged back in after resuming from hibernating, I load up a cmd terminal and do the following.

$ lsof /dev/snd/*
COMMAND     PID   USER   FD   TYPE DEVICE SIZE   NODE NAME
mixer_app 12863 adrian   17u   CHR  116,6      241947 /dev/snd/controlC0
$ kill -9 12863 (or whatever the PID is)
$ sudo rmmod snd-hda-intel
$ sudo modprobe snd-hda-intel

As you may notice, when killing the mixer_app process, a gnome box appears mentioning that the "Volume Control has died unexpectedly" with the option of 'reload' or 'don't reload'.  I leave this box up while I remove and reload the sound module, then hit the 'reload' button.

Works but it is very messy.  I hope installing Fiesty will fix this issue, but I'm not willing to install it on my laptop until a week or so after it is released as I essentially need to guarentee myself a reliable working laptop atm.

Have you come across the issue the thread poster mentioned regarding to battery usage while the laptop is shutdown after running Ubuntu vs Windows?  I'm experiencing the same thing, but havent found anywhere on the net a similar issue being reported.

---

### Post by mortoss on 2007-03-18
> Have you come across the issue the thread poster mentioned regarding to battery usage while the laptop is shutdown after running Ubuntu vs Windows? I'm experiencing the same thing, but havent found anywhere on the net a similar issue being reported.

Acctualy no...

What I do is shutting down ubuntu and then running 'express media player' - when EMP loads I simply press power button... I takes 10 more seconds to poweroff PC and keeps battery power longer.. I know.. it's not very elegant but practical...

---

### Post by katabatic on 2007-03-19
Darn Toshiba + Linux = :-(

I haven't noticed the battery draining issue, so I will test it.
I have also deleted the Express Media Player partition that took up a friggin 200 MB, cause I don't use it or care for it.

---

### Post by mortoss on 2007-03-20
> ..cause I don't use it or care for it.

...I beleve it's pretty usless.. Only reason I kept EMP is that I suspect it has something to do with linux.. (?) (manual mentioned sth like that: 'diffrent license' and 'possibility of obtaining the source code')

---

### Post by katabatic on 2007-03-22
> The Express Media Player software provided with the laptop utilises a 2.4 series Linux kernel and numerous other GPL software packages, though the extent of customisation of this software is not yet known.


I have now tested the battery draining issue, and it does indeed drain overnight to 70% after shutting down from Ubuntu. Looks like our next problem to fix if Feisty doesn't fix it

BTW, do you guys find the front of the laptop ugly, namely the corners?

---

### Post by iheartmuseums on 2007-03-23
I've got a Toshiba M100 running Edgy, and i'm experiencing the battery drain as well. 100% power on shutdown, and then later in the day when I restart, it's down around 75-80%. What could possibly be causing this?

---

### Post by mortoss on 2007-03-23
> What could possibly be causing this?

My only idea was that Linux 'stops' battery recharge before full level - but its incorrect - when I boot into M$ it also says 'fully charged'.. Maybe ubuntu does not shutdown all devices of the notebook?! But how? &y?

---

### Post by iheartmuseums on 2007-03-23
I don't have any problems with my battery reaching full charge - acpi tells me it's at 100% after i've had the AC charging the battery. But to have 20% or more of the battery power drain away while it's totally switched off is so strange and more frustrating than anything else.

---

### Post by jfhian on 2007-04-19
> **katabatic said:**
> I got it working! I have just read this post: [http://www.orangegroove.net/articles/2007/02/08/toshiba-linux-and-lcd-brightness-2/](http://www.orangegroove.net/articles/2007/02/08/toshiba-linux-and-lcd-brightness-2/)


The URL has changed, it should be [http://slu.ms/articles/2007/02/08/toshiba-linux-and-lcd-brightness-2/](http://slu.ms/articles/2007/02/08/toshiba-linux-and-lcd-brightness-2/) now. It redirects in the meantime. Cheers.

---

### Post by Solicitous on 2007-04-29
Well to add to the power usage whilst the laptop is turn off, I've done a little research and I think I may have come to a possible reason as to why.  I was looking through [http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)
and it mentions two power modes of interest, G2 (S5) and G3.
Briefly, the G2 is a soft power off mode, which shuts down the PC yet power is still consumed by keeping devices alive, so it can perform a wake-on-lan option etc.  And G3 state being what is defined as a Mechanical Off, basically no power is run through the computer.  

After reading that, it sounded to me like a good assumption was the laptop is turning off in a G2 state, but not a G3 state, hence the power usage when turned off.

Anyone have any ideas/opinions on what I have just written?

Cheers,

---

### Post by funnyguyfunnyguy on 2007-04-30
Thank you everyone for this post. It has been very helpful getting my laptop up and running. I am trying to create the scripts to change the lcd brightness and I have run into a problem.

(1) I created the scripts and placed them in /etc/laptop-mode/batt-start and /etc/laptop-mode/batt-stop. They work when I run the scripts from the command line, but not when I plug/unplug my machine. I did enable laptop mode in file that was mentioned.

Another question. Someone mentioned that the fn+f# keys work under feisty for the lcd. This is true, but it was suggested that the linux is skipping over certain levels. I think this is true. Under Windows Vista most laptop show increments on 10. i.e. 

```
cat /proc/acpi/video/VGA/LCD/brightness
```

would perhaps produce:

```
cat /proc/acpi/video/VGA/LCD/brightness
levels:  10 20 30 40 50 60 70 80 90 100
current: 10
```

(2) Perhaps a file exists that tells linux what those levels are. If so would it be possible to alter those values? I am somewhat of a noob, but maybe this could help.

---

### Post by ac1201 on 2007-05-18
I've got a Toshiba M110, and I'm experiencing the power issue too. Neither hibernate or shutdown appear to be fully shutting down the computer, so the battery continues to drain.

---

### Post by funnyguyfunnyguy on 2007-05-31
So ... has anyone figured out a fix to the battery life issue after shutdown?

---

### Post by katabatic on 2007-06-03
> **funnyguyfunnyguy said:**
> 

(1) I created the scripts and placed them in /etc/laptop-mode/batt-start and /etc/laptop-mode/batt-stop. They work when I run the scripts from the command line, but not when I plug/unplug my machine. I did enable laptop mode in file that was mentioned.
.

Make sure you made them executable as I have shown in the other post. Is laptop-mode turning on? Check this as well /etc/laptop-mode/laptop-mode.conf

Look at these settings:
# Enable laptop mode when on battery power.
ENABLE_LAPTOP_MODE_ON_BATTERY=1

# Enable laptop mode when on AC power.
ENABLE_LAPTOP_MODE_ON_AC=0

If they are 0, try putting 1 in the top one or both.

---

### Post by iheartmuseums on 2007-07-01
> **Solicitous said:**
> Well to add to the power usage whilst the laptop is turn off, I've done a little research and I think I may have come to a possible reason as to why.  I was looking through [http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)
and it mentions two power modes of interest, G2 (S5) and G3.
Briefly, the G2 is a soft power off mode, which shuts down the PC yet power is still consumed by keeping devices alive, so it can perform a wake-on-lan option etc.  And G3 state being what is defined as a Mechanical Off, basically no power is run through the computer.  

After reading that, it sounded to me like a good assumption was the laptop is turning off in a G2 state, but not a G3 state, hence the power usage when turned off.

Anyone have any ideas/opinions on what I have just written?

Cheers,

Nice fact-finding there. It sounds like something that would cause this power drain problem. I would *love* to know if there's a way to configure my laptop so it's using the G3 shutdown.

---

### Post by dwc-ubu on 2007-07-01
This works with a Toshiba A135-2386 bought in late Jun 2007 without a BIOS upgrade, just doing the scripts described above.  Thanks!

-dwc

---

### Post by iheartmuseums on 2007-07-19
Is there any way we can get someone to officially look at this power drain issue? Or at least point out where the G2/G3 option can be switched between? I had my laptop switched off from 8am to 6pm today and lost 25% of my battery charge so... i'm not really happy about that. 

Anyone?


Bueller...?

---

### Post by funnyguyfunnyguy on 2007-07-29
bump

---

### Post by secretkeeper81 on 2007-08-01
> **iheartmuseums said:**
> Is there any way we can get someone to officially look at this power drain issue? Or at least point out where the G2/G3 option can be switched between? I had my laptop switched off from 8am to 6pm today and lost 25% of my battery charge so... i'm not really happy about that. 

Anyone?


Bueller...?
I have been having this same battery drain problem too!! It's really annoying... please someone help!

P.s: I'm also using a Toshiba Satellite laptop.

---

### Post by fAlCoNNiAn on 2007-08-08
Im having the same problem with my laptop (toshiba M115), when it is turned completely off, the battery drains pretty much all the way. at first i thought it was because i had a usb mouse pluged in and the computer kept powering it. Unpluged it, nothing changed. Is it a linux issue or a toshiba issue (aka bios). anybody know if this happens in windows?

---

### Post by secretkeeper81 on 2007-08-08
Well I have a dual boot system on my laptop, and when I turn it off from Windows, the battery definitely does *not* drain the way it does when I shut down Kubuntu.. :(

---

### Post by fAlCoNNiAn on 2007-08-08
did anyone experience this issue with previous releases? (edgy, hoary, etc) i remember i didnt, at least i dont think so.

---

### Post by secretkeeper81 on 2007-08-08
My first distro was Mepis, and I don't remember experiencing similar problems; however, in a few weeks I switched to Kubuntu 6.10, and I'm sure the problem appeared before I upgraded to 7.04..

---

### Post by fAlCoNNiAn on 2007-08-08
is it a toshiba issue in general (all toshiba laptops) or just the M series?

---

### Post by glrossetti on 2007-08-22
Same problem on Vaio S2XP hibernated

---

### Post by secretkeeper81 on 2007-08-28
> **fAlCoNNiAn said:**
> is it a toshiba issue in general (all toshiba laptops) or just the M series?

Mine is a Satellite A100-114

---

### Post by iheartmuseums on 2007-08-30
Could the battery drain while the system is shut off be anything to do with Toshiba's 'Express Media Player'? That function doesn't have anything to do with the operating system itself, but could possibly drain power as it is ready to go at any time?

---

### Post by secretkeeper81 on 2007-08-30
But the problem never presented itself until I installed Kubuntu, and still now if I shut down from Windows it doesn't drain..:confused:

---

### Post by iheartmuseums on 2007-08-30
So it's got to be something tied directly to Ubuntu as a system, then. Why isn't it shutting down completely, what could possibly be still using power after quitting?

Argh!  :(

---

### Post by secretkeeper81 on 2007-08-31
I have no idea. I've tried shutting down with 

```
sudo shutdown -P now
```

but no luck either..

---

### Post by funnyguyfunnyguy on 2007-09-27
Has anyone tried shuting down with Gusty? Perhaps, the new kernel has fixed the issue.

---

### Post by finlay.thompson on 2007-10-10
Hi

I have an M110 computer, similar to the M115s. 

I just upgraded the BIOS, and it hasn't made the Fn F6|7 buttons work, but that is not such a big problem for me.

The battery draining is though. I wonder if there is something we can add to the acpi scripts to help really shut the computer down...

btw, Im running gutsy as of a few days, and its really nice.

Finlay

---

### Post by Solicitous on 2007-10-13
I've got the m110 as well.  The bios update I found did make the Fn F6/F7 buttons work under feisty, but (and this is only using the LiveCD) didn't work for gutsy (I'm unsure if the results would be different by upgrading feisty to gutsy).  
Now if I do recall, I tested Fedora 7 LiveCD once.  That still suffered from the battery drain issue (I tested to see if it was resolved under another distro).  So to me it doesn't seem to be anything specific to they way Ubuntu handles the shutdown/hibernate scripts.

---

### Post by funnyguyfunnyguy on 2007-11-22
I just installed openSuse 10.3 on my M115, and my machine suffered the same batter drain issues. It must have something to do with all linux systems, perhaps the kernel? Would compiling the kernel myself solve this issue?

Thanks,
Steve

---

### Post by fAlCoNNiAn on 2007-12-06
Been running Gusty for alittle over a month now. Completely wiped fiesty before to hopefully maybe see if this battery issue has been fixed. No Dice. Still having drainage problems, which is really annoying when i need to take my laptop to a meeting and then to find out that i have to plug in the AC adapter to make it work because of the dead battery.

Any idea on what allows windows to shutdown completely and not drain the power, and why Ubuntu, and I guess on what other users here report, Linux in general, can't shutdown?:(

---

### Post by oellegaard on 2008-04-26
> **mortoss said:**
> Thanks!!!! :popcorn:   

After flashing bios - 'made for vista' - changing brightness works in ubuntu :D  Thanks again!


**SOLVED**

Is there any way to flash from ubuntu, without installing that Vista virus all over again?

---

