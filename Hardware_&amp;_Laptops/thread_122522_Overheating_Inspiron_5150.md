---
title: "Overheating Inspiron 5150"
date: 2006-01-27
forum: Hardware &amp; Laptops
---

### Post by mabster on 2006-01-27
My Inspiron 5150 constantly overheats.  This doesn't appear to be related to what I'm doing at the time, it just seems to happen every couple of hours.  The fan will start to go nuts and then I know at that point I've got about 5 seconds left.  When I restart the machine I get the Dell "overheat warning".

I am aware that the Inspiron 5150 is well known for having overheating problems, but under Windows XP it was /very/ unusual for it to overheat, so I'm sure there must be software remedies for it.  Also, I'm pretty sure my machine runs hotter under Linux than under Windows.

I've tried moving across to the non-smp kernel in the hopes that it would throw out less heat, but that didn't really help either :(

What can I do to alleviate this?

---

### Post by byen on 2006-01-27
now what kind of processor do you have? You said Inspiron so Im thinking an Intel based.. well are you sure you are using the right kernel for your computer? I had similar issues with my Presario with an AMD athlon processor and after i changed my kernel from 386 to K7... I saw a good difference in the performance and a considerate improvement with the "heat" issues. 
To find out whcih kernel suits your pc you can type  "uname -m" in the command line.

Not a great solution but it might help. Goodluck.

Edit: Here is a [link]("http://www.ubuntuforums.org/showthread.php?t=85917") that explains a little about installing the right kernel for you

---

### Post by mabster on 2006-01-27
Thanks for the reply.

My processor is a 3.06-GHz Mobile Intel Pentium 4 (w/ Hyperthreading).  That seems to fit the bill (686 based kernel, SMP to get the Hyperthreading).

```
mabster@mab:~$ uname -m
i686
mabster@mab:~$ uname -r
2.6.12-10-686-smp
```

---

### Post by byen on 2006-01-27
here is a [post]("http://www.ubuntuforums.org/showpost.php?p=190445&postcount=11") that might help you. See if that works. Goodluck!

---

### Post by mabster on 2006-01-28
Ok, I've tried disabling apmd as it said.  Once I restarted my machine, I tried:

```
mabster@mab:~$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             62 C
```

That's about the same as it was before, but it's difficult to tell how hot an Inspiron 5150 is /meant/ to run ;)  I'll try using my laptop for the next couple of days and post whether it's still overheating.

Thanks!

---

### Post by mabster on 2006-01-28
Nope.  Just overheated :(  I checked the temperature just before it overheated and it was running at 82dC.  After boot, 72dC.

---

### Post by pinkpanther_bc on 2006-01-28
Hello
 
I am a new linux user. I have just upgraded my kernel to 686, I am using a compaq presario r3000 with a AMD M.
The new kernel works great.
I just love using linux, and still learning stuff. How do I now delete/remove the other kernels.
I have a 40 gig HD and dual boot with windows and every thing is working fine.
I will eventualy remove windows! I need all the space possible and I just do not see a reason to keep the old kernels.

Thanx:) :)

---

### Post by byen on 2006-01-28
> How do I now delete/remove the other kernels.
simple... System>Administration>Synaptic>search>linux-image>Right Click on the kernel you want to remove>Complete Removal>Apply

That should do the trick! Goodluck!

---

### Post by mabster on 2006-01-28
Personally, I kept the 386 kernel around because that would be pretty safe bet if my 686-smp kernel went down. *shrugs* :)

---

### Post by towsonu2003 on 2006-01-28
Here ( [http://lists.suse.com/archive/suse-linux-e/2005-Jul/2362.html](http://lists.suse.com/archive/suse-linux-e/2005-Jul/2362.html) ) it says you can buy a fan for $35... 

At this point, before buying stuff, check out other distros ( [www.distrowatch.com](www.distrowatch.com) ) and see whether 5150 overheats the same way. Go from the most popular to the least one by one. And very important: in each distro, don't wait until the laptop signals you the 5 seconds timeout... You could for example use conky (or your hand for that matter) to monitor the heat (pls ask if you're interested in that). 

I mean, ubuntu is *useless* for you as you have to reboot due to overheat. And overheating is actually *dangerous* for your computer's physical health... I get scared when mine goes to 62 degrees (hp pavilion zv5120us - my hand burns while playing with mouse) during a virus scan (I'm paranoid)...

If nothing works, I'd switch back to windows. It's just not worth risking the hardware. you might wanna do research for the next toy's (computer) compatibility w/ linux.

---

### Post by mabster on 2006-01-28
I was worried someone would say that :-(

The reason I arrived at Ubuntu is that I wanted an easy to use system with some good package management support.  RH was awful (what a mess, files all over the place).  Debian doesn't install (it never has over the 3 or so revisions I've tried over the past few years).  Ubuntu installed and just worked.  I'm not giving up on Ubuntu just yet ;).

I've read some stuff on cleaning the heatsync etc. that might help and I've also read about people changing the thermal paste.  Both last-step measures, but there is the option.  There's also on-going discussions on i8k / powernowd utilities.  Hopefully the catch-all solution comes rolling in :D.

---

### Post by wetland on 2006-02-21
You might want to try this out. [http://www.ccs.neu.edu/home/jabra/projects/dell5150.html](http://www.ccs.neu.edu/home/jabra/projects/dell5150.html)
See: APCI 
I have a 5150 with mandrake 10.1 this worked for me as a temp. fix.

---

### Post by ephman on 2006-02-21
hi,

i have a dell inspiron 5100.  not that much difference between our models, the main guts are the same, except for more vid mem, a larger hdd, but the mainboard is still the same.  my machine was running pretty HOT, and would sometimes overheat.  i called dell (have extended warranty), and they told me that for my machine there is a defective heatsink/fan/gel when they were made.  they came out and replaced the unit and i noticed a huge difference, i dropped about 10 degrees celsius.  you might be having the same issue.  worth the call.

thanks for the bandwidth,
ephman

---

### Post by akniss on 2006-02-21
Have you tried running gnome-system-monitor to see what processes are running when you start to get hot?  My inspiron 600m would do a similar thing now and then.  I installed gdesklets so I could monitor CPU usage and sure enough, whenever the fan was running hard, the CPU was hovering around 98%.   When I opened gnome-system-monitor, I found that evince-thumbnailer was going crazy.  I uninstalled evince (i use acrobat reader anyway) and haven't had an overheat since.

---

### Post by wetland on 2006-03-06
mabster,

I saw ephman's post and thought I would do a little searching. I found out that others did get there 5150's repaired by Dell with Dell admiting there was a problem with the heat sink and fan. So since my 5150 is out of warranty I figured I would contact Dell via email and explain my situation about over heating and what I had read on the internet. Two hours after I had sent the email I recived a reply saying they would honor the repair at no cost to me. 

I am typing this on the repaired 5150 right now the fan seems to be functioning properly, and no over heating.

Might be worth a try?

---

### Post by moopet on 2006-03-10
Take it apart. Clean the radiator. Clean the old heat gunk off with alcohol on cotton wool. Squirt on some arctic silver. Reassemble.

Happens to 5150s all the time. Fix takes 5 minutes, costs about $8 of your funny money.

P.S. I repair laptops for a living.

---

### Post by pestypest on 2006-03-21
[QUOTE=mabster]Ok, I've tried disabling apmd as it said.  Once I restarted my machine, I tried:

```
mabster@mab:~$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             62 C
```

That's about the same as it was before, but it's difficult to tell how hot an Inspiron 5150 is /meant/ to run ;)  I'll try using my laptop for the next couple of days and post whether it's still overheating.

Thanks![/QUOTE]
im not sure if im doing somthing wrong but i typed ~$ cat /proc/acpi/thermal_zone/THM/temperature in term and i get this error "bash: ~$: command not found" any ideas ? thanks

---

### Post by towsonu2003 on 2006-03-21
[QUOTE=pestypest]im not sure if im doing somthing wrong but i typed ~$ cat /proc/acpi/thermal_zone/THM/temperature in term and i get this error "bash: ~$: command not found" any ideas ? thanks[/QUOTE]
command is this: ```

cat /proc/acpi/thermal_zone/THM/temperature
```

---

### Post by pestypest on 2006-03-21
i tried it and this is what i got    "jason@jason:~$ cat /proc/acpi/thermal_zone/THM/temperature
cat: /proc/acpi/thermal_zone/THM/temperature: No such file or directory"
any ideas?

---

### Post by towsonu2003 on 2006-03-21
[QUOTE=pestypest]i tried it and this is what i got    "jason@jason:~$ cat /proc/acpi/thermal_zone/THM/temperature
cat: /proc/acpi/thermal_zone/THM/temperature: **No such file or directory**"
any ideas?[/QUOTE]
try using the tab key (on the keyboard) and see what you got in there... so:
```

cat /proc/acpi/ther[tab]/[tabtab]/[tabtab]
```
[tab] -> hit tab once so it will complete the name for you (if there is a file/folder with that name)

[tabtab] -> hit tab twice so it will give you a list of contents for that directory; choose one and continue 

ex: 
cat /proc/acpi/ther[tab]->{mal_zone}/[tabtab]
blabla1 blabla2 blabla3
cat /proc/acpi/thermal_zone/blabla1/..........

I am pretty clueless how to explain this, sorry for this weird explanation...

---

### Post by mabster on 2006-03-27
Also, to help get us an idea of ur configuration you could post the results of:

```
ls /proc/acpi/
```

and if that doesn't come up with anything (it comes up with 'no such file or directory' or some such):

```
ls /proc/
```

...

---

### Post by sn123 on 2006-03-27
[QUOTE=mabster]Also, to help get us an idea of ur configuration you could post the results of:

```
ls /proc/acpi/
```

and if that doesn't come up with anything (it comes up with 'no such file or directory' or some such):

```
ls /proc/
```

...[/QUOTE]

If cat /proc/acpi..... doesn't work, you can try acpi from the terminal directly.
```

$ acpi -V

```

S

---

### Post by slightly72 on 2006-03-27
I have a Dell Inspiron 5160, with similar overheating problems (of which I found after buying it, and with the warranty expired) -- its normal state, not doing anything major, being around 75-78C. After a lot of tweaking, the temperature now hovers around 51-56C (while writing this message). Steps:

1. Remove the battery to allow for some more air flow. The laptop is quite poorly designed, and the fan does not take much air. Since I'm using it as a desktop replacement, it's always on AC power.
2. In BIOS, I've disabled IntelSpeedStep technology. Contrary to the BIOS help, the processor is not placed in the worst state, it does work at 2.8GHz (nominal frequency). Again, this is not a laptop for moving around, don't quite need multiple speeds. With cpu frequency scaling after step 1, the temperature was around 72, and staying there. Steps 1+2 got it to about 65-67C (these temps are after a boot).
3. According to some advice here on the forums (post 190445), you should disable apmd or acpid on boot -- apmd in my case. That was worth about 3 degrees.
4. I've tried to clean it, but can't get to the cpu and fans without removing the display, which I did not feel to brave enough doing. So instead, I've tried to blow air  to blow the dust off through whatever opening it had (couple on the sides, one below). That got me to whatever temperature is now.

You should also check [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles") The link has some tricks with the temperature sensors. In particular, you should install i8kutils and gkrellm-i8k -- the software can control the temperatures at which the fans start. If you don't mind the fan noise, you might set them up lower -- I did mind, so left the defaults that are dected/set by Ubuntu. 

Hope this helps.

---

### Post by gamma on 2006-04-11
Yea this is one hot laptop. When I first bought the system I wanted something "portable" yet powerful. This was the perfect system since it was the only laptop that did 1600x1200 at the time with a low-end DX9 card. Now I bring my laptop to school more and more and notice how much of a pain this thing is to transport. It's also annoying to have the fan turn on while being in class.

I've cleaned the fan out a few times, it's not hard or dangerous just unsnap the blue piece that the power button is on while the screen touches the ground and lift it up. Unhook the keyboard then unscrew the right plate and you can blow out the fan.

My system hovers around 53-70C depending on what I'm doing. As of writing this I'm at 54C.

EDIT: For me the fan seems to turn on at around 55-56C, although it's not the full blast fan, but it's still annoying.

---

### Post by ephman on 2006-04-12
hi,

i used to have a 5100 ran about at the same temps 55.  now i have an inspiron 6000 (sweet machine) and it's pretty steady at 34c  big difference.  just for a little perspective.

ephman

---

### Post by TSJason on 2006-05-06
Hi,

 I also have the 5150 and it does get bloody hot; and will frequently overheat in the exact manor you described. I found that using several of these tweaks helped out; I also installed Kpowersaved (running on kubuntu here) and set the CPU frequency policy to dynamic. I tried out the Intel Speedstep setting in the bios but that didn't seem to really help at all and it would cut my processor down to about 1.5Ghz instead of anywhere near it's fastest at 3.06Ghz :---) 

 Ah well; I suppose this is what I get for buying from Dell...on the other hand; my desktop machines are pretty sweet (and cool!!); and run kubuntu like rocks!

---

### Post by capt_cope on 2006-05-06
I'm writing this on a 5150 (still using xp, have ubuntu downloading right now) and I too had absurd overheating troubles. I did break down and clean the internals out, but that was after I gave it up for dead. Something to watch on your 5150, there is a fairly well known design flaw in the case in which a little plastic tab on the cover for the internal wireless card rubs on a chip and cracks the solder. If you move this laptop around a lot you run the risk of slowly breaking the chip off the mobo. I know mine started showing the symptoms (shuts down if you tap the front left side, or appy any preasure on the underside front left. eventually it wouldn't start correctly (cpu and hd run but lcd stays black) long story short I had it in pieces to fix it, cleaned the internals then, and bought some cheap ($15) external usb powered fan/stand. Dropped my temps from the 70s to the 50s. I know this post is rambling, but my main point is this: as a current xp user I have the same troubles. I think you should look for a hardware fix, the overheating "reaches across" os boundries.:rolleyes:

**edit** Well just booted up into ubuntu for the first time. I'll let you know if I run into any overheating.

---

### Post by pokeyflan on 2006-05-14
[QUOTE=mabster]Also, to help get us an idea of ur configuration you could post the results of:

```
ls /proc/acpi/
```

and if that doesn't come up with anything (it comes up with 'no such file or directory' or some such):

```
ls /proc/
```

...[/QUOTE]

What's supposed to be there?  I have a DELL Latitude C610, which is having mysterious shutdowns.  The fan hardly ever runs, the acpi temp readings are ~50s but sometimes shoot up with no discernible (to my hand) change & it shuts down.  Very frustrating.  My  ls /proc/acpi looks like this:

ac_adapter  dsdt                 fan             processor     video
alarm       embedded_controller  hotkey          sleep         wakeup
battery     event                info            sony          wmi
button      fadt                 power_resource  thermal_zone

The /fan directory is empty.

In /thermal_zone/THM/
cooling_mode  polling_frequency  state  temperature  trip_points

with these cat readings:
cooling_mode:  <setting not supported>
cooling mode:   critical
polling_frequency:   <polling disabled>
state:  ok
temperature:  45 C
trip_points:  critical (S5):           100 C

I can't test if this machine works OK with windooze because it's Ubuntu-only.

I hope someone can please help me decipher all this.  

TIA......chris

---

