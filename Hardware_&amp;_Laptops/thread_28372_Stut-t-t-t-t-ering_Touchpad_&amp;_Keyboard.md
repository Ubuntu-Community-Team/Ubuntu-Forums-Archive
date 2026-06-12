---
title: "Stut-t-t-t-t-ering Touchpad &amp; Keyboard"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by TheAngryPenguin on 2005-04-19
Just did a clean install of Hoary on my Dell Inspiron 8100, and I am thoroughly annoyed with the behaviour of the mouse and keyboard.  The thread title says it all.  There's really no rhyme or reason to it -- it just happens randomly and often enough to make me want to slick this laptop and revert back to Warthog.

Interestingly, this also occurred when I had the Hoary Preview freshly installed on a Latitude C600.  Obviously, there's some correlation going on here:  Dell Laptops; both with Synaptics Touchpads; etc.  Can anyone help?!?  I'd like to keep my ubie installs current...

---

### Post by Laurent Cazalet on 2005-04-20
Hmmm. 
I have a C600 too. And no problems with the keyboard of touchpad (except the well know random mouse problems - that sometimes blocks the pointer in a corner of the screen, which you can diagnose using the tip below).

do you have cpu at 100% while this happens?
have you updated to the latest BIOS? I run the A23
you could try to recompile your kernel changing a couple of options, like preemptive, or unnecessary mouse drivers.


you can also take a look at /proc/bus/interrupts, and check if you get a lot of interrupts on the mouse while you are not touching it (normally you get an interrupt only when the you move the mouse or press a key.
try this to see mouse interrupts (it should be the same interrupt number on your machine)
```
 while true; do cat /proc/interrupts | grep 12: ; sleep 1 ; done
```

(CTRL+C to stop)

---

### Post by TheAngryPenguin on 2005-04-20
[QUOTE=Laurent Cazalet]Hmmm. 
I have a C600 too. And no problems with the keyboard of touchpad (except the well know random mouse problems - that sometimes blocks the pointer in a corner of the screen, which you can diagnose using the tip below).

do you have cpu at 100% while this happens?
have you updated to the latest BIOS? I run the A23
you could try to recompile your kernel changing a couple of options, like preemptive, or unnecessary mouse drivers.[/QUOTE]
Lastest BIOS images have been installed on both laptops.  I'll have to pay more attention to the CPU usage.

[QUOTE=Laurent Cazalet]you can also take a look at /proc/bus/interrupts, and check if you get a lot of interrupts on the mouse while you are not touching it (normally you get an interrupt only when the you move the mouse or press a key.
try this to see mouse interrupts (it should be the same interrupt number on your machine)
```
 while true; do cat /proc/interrupts | grep 12: ; sleep 1 ; done
```

(CTRL+C to stop)[/QUOTE]
Thanks for the tip.  I'll give it a shot and report back when I have some results.

---

### Post by speedman on 2005-04-20
[QUOTE=Laurent Cazalet]while true; do cat /proc/interrupts | grep 12: ; sleep 1 ; done[/QUOTE]

Or the watch command can be used as follows:

watch 'cat /proc/interrupts | grep 12'


Regards,

SM

---

### Post by TheAngryPenguin on 2005-04-21
Well, I'm not exactly sure what to be looking for, but here's the output:

It starts out at somewhere around:
```
 12:      62902          XT-PIC  i8042
```
...and after about ten minutes of normal use (eg. merely browsing with Firefox), it goes up to:
```
 12:      236998          XT-PIC  i8042
```
During this time period, I've definitely noticed the stuttering.  Any ideas?

---

### Post by Laurent Cazalet on 2005-04-22
the idea is to monitor this value while actually you're *not* touching the mouse.
if the value changes in spite of mouse inactivity, something is wrong.
this can come from a hardware problem. or maybe you can try to recompile your kernel with different options, then.


speedman: thanks for the watch tip.

---

### Post by TheAngryPenguin on 2005-04-22
The value definitely increases while being idle, however, not as much as it increases when there's normal activity.  I'll need to watch it a little more closely, I guess.

I doubt that there's a hardware problem since this wasn't and hasn't been an issue with 4.10 (Warty Warthog) and other OSes.  To me it's worth putting forth the effort towards recompiling the kernel; however, this is something that I've never done before.  Any tips, pointers, etc.?  It would be really great if someone could guide me through this, perhaps outside of the forums, and if/when I figure it out, I'll report back here.

---

### Post by TheAngryPenguin on 2005-04-26
[QUOTE=Laurent Cazalet]...I have a C600 too. And no problems with the keyboard of touchpad...[/QUOTE]
Just out of curiousity, what, if any, switches did you use when you installed?  I used:
```
linux vga=771 [1] noapic nolapic
```
[1] or whatever the recommendation is.

This is the same way I installed Warty, and the keyboard/mouse problem was never an issue.  I'd be more than willing to start over using your recommendations...

Edit A:

Well, I just did a normal install with no options.  It didn't change a thing.  However, I got kubuntu up and running this time around and it seems to be running a little bit smoother.  I can't say that the jerkyness when using the mouse or keyboard is completely gone, but it's definitely a lot less noticable in KDE.  Any ideas?

Edit B:

Tonight I slicked my laptop once again, installed Warty, played around with it for a while and as expected, encountered no problems.  However, it seems that I can no longer upgrade things like Firefox and Thunderbird anymore, so I figured I'd change my source and do a dist-update.  Once finished, I noticed that the stuttering was also occuring with the startup sound that I apparently missed previously.  It looks like I'm totally SOL now -- Hoary is frustrating to use and Warty cannot be easily updated anymore.  As I stated before, I'm willing to put forth more effort into resolving this, but I need guidance.  In the meantime, I'm afraid that I'm going to have to add myself to the "I'm leaving..." list, which is a damn shame because I totally believe in everything Ubuntu stands for.

---

### Post by TheAngryPenguin on 2005-05-03
Perhaps I should have replied instead of edited my last post a few times.  At any rate, I'm beginning to believe that my problem is Xorg -- is it possible to use Xfree instead, as a last resort?  I'm in Ubuntu withdrawal...  ](*,)

---

### Post by My_World on 2005-05-15
I have exactly the same problem here, but my laptop is a Mecer 2.8 Celeron.

The mouse will seem tremendously sluggish and unprecise and the keyboard very unresponsive often missing keypresses.

I was looking forward to giving Ubuntu a test run (Gentoo is my flavour of choise) and it will be a shame if there is no fix for this!

What I did try and do is to manually edit xorg.conf and remove the synapses entry and used only the default /dev/psaux driver and settings with marginal success for the touchpad, but the keyboard ussage drives one out the walls.

Any fix or something we must look into to get it working right?

---

### Post by My_World on 2005-05-15
[QUOTE=My_World]I have exactly the same problem here, but my laptop is a Mecer 2.8 Celeron.

The mouse will seem tremendously sluggish and unprecise and the keyboard very unresponsive often missing keypresses.

I was looking forward to giving Ubuntu a test run (Gentoo is my flavour of choise) and it will be a shame if there is no fix for this!

What I did try and do is to manually edit xorg.conf and remove the synapses entry and used only the default /dev/psaux driver and settings with marginal success for the touchpad, but the keyboard ussage drives one out the walls.

Any fix or something we must look into to get it working right?[/QUOTE]
 Okay, seems like i may have narrowed down the problem. Installed Fluxbox and have had no problems so far. Will try KDE quickly and see if there is a problem, but I think we can place our money on Gnome being the culprit here.

Oh, btw, have I mentioned that I hate Gnome?
:P

---

### Post by golpira on 2005-05-24
[QUOTE=My_World]Okay, seems like i may have narrowed down the problem. Installed Fluxbox and have had no problems so far. Will try KDE quickly and see if there is a problem, but I think we can place our money on Gnome being the culprit here.
[/QUOTE]
I'm having the same problem on my Dell laptop -- very annoying.  I tried switching to Fluxbox also, but it didn't seem to make much of a difference.
Has anyone figured out what is really causing this yet?

---

### Post by elsewhere on 2005-05-24
I had a similar problem on my Inspiron 8100, my mouse/keyboard would freeze up randomly for just a second or so, had to disable powernowd to make it go away (although I lost cpu scaling).  Had something to do with an irq conflict between acpi and the synaptic touchpad.

Might be worth a shot ?

Cheers,
KV

---

### Post by Chunk of Earth on 2005-05-24
[QUOTE=TheAngryPenguin]Just did a clean install of Hoary on my Dell Inspiron 8100, and I am thoroughly annoyed with the behaviour of the mouse and keyboard...[/QUOTE]

Just another data point: I have the same problem on a Latitude C610. I thought it might be an artifact from my upgrade from Warty to Hoary but it seems not.
It looks like it might be CPU related because the keystrokes and mouse movements are buffered during the slowdown and play back as soon as things free up. I have the system monitor running and I've caught a couple of pegs on the CPU meter. **hdparm -i** says I'm in udma5 for my hda and mdma2 for my cdrom so it's probably not i/o bound.

I haven't optimized the graphics yet. (it's kind of a pain on this system) 
Using the "radeon" driver in x.org.

---

### Post by psilo on 2005-05-24
I'm having the same problem on a Dell C400.  Very irritating.  The powernowd idea looks like something to check out.  I've had the same laptop running cpufreqd under Gentoo and did not have this problem.  Has anyone tried using a different scaling daemon?  Might try it myself but it will have to wait until I get some spare time.

---

### Post by elsewhere on 2005-05-25
I did try cpufreq and cpudyn, since they were in the repository.  Couldn't get them to work, but in all honesty they require some small effort to configure and I just couldn't be bothered at the time.  I do like powernowd since it seems it follows Ubuntu's theme of just working, but I can easily replicate the problem by enabling / disabling it so it's definitely directly or indirectly causing the problem on my system.

Cheers,
KV

---

### Post by golpira on 2005-05-27
[QUOTE=elsewhere]I had a similar problem on my Inspiron 8100, my mouse/keyboard would freeze up randomly for just a second or so, had to disable powernowd to make it go away (although I lost cpu scaling).  Had something to do with an irq conflict between acpi and the synaptic touchpad.

Might be worth a shot ?

Cheers,
KV[/QUOTE]
 Excellent!  Disabling powernowd did the trick.  Thanks!

---

### Post by rpdillon on 2005-07-21
Two reasons for posting:
1) To bump this thread, which deserves it, since this is still an issue

and 

2) To add my data point.  I am using an LAC (Los Alamos Computers) laptop (The LUCGM) made specifically for use with Linux (check laclinux.com) and after upgrading my BIOS, encountered this problem in spades...

...but not with Ubuntu.  With Kubuntu.  Which means the problem is not Gnome-specific.  I have tried stopping powernowd, to no effect.  I am almost sure it is related to acpi one way or another, since most problems on systems running acpi is the acpi daemons.

Anyone else have any ideas?  I've done clean installs, tried killing off hald, powernowd, sony_acpi, pcc_acpi, klaptop.  Doesn't work.

Tried passing acpi=off to the kernel on boot, which DOES work, but kills off acpi, which has other negative side effects.

I agree with the posts above about it being an IRQ conflict - anyone know how to fix this?  I've been using Linux for years (Red Hat, Fedora, Debian, Gentoo and now Ubuntu) but have never had to manually deconflict IRQs.  Help?

---

### Post by mofoosu on 2005-07-24
I have this same problem on my Dell Latitude c610 with BIOS A16, This machine is a 1ghz pM. 768mem ram, with the touchpad disabled, PS2 mouse plugged in.

Mouse moves erratically, When typing sometimes it also stutters. 

Another thing to note is SpeedStep is enabled.
I have the latest version of Unbuntu and all updates.

VERY annoying. I tried the mouse IR polling, it is fine. all hardware is fine.

I also had a similar problem with my sloow dell 500PIII
Mouse just moves like crap.

I wish this could get fixed, until then I will install Debian.

---

### Post by elsewhere on 2005-07-24
Just as an update, it would appear that this problem seems particular to Dell although not necessarily exclusive.  I had experienced it previously in FC3 starting with the 2.6.11 kernels, so I don't think it's exlcusive to Ubuntu although it wasn't as pronounced in Fedora.

Dell's are known to have a buggy ACPI implementation, could be that patching the DSDT  may alleviate it.  I never got around to trying that since ACPI worked for the most part for me (ie. suspend, battery status etc.).

Disaling powernowd fixed the issue for me (as did disabling cpuspeed in FC3), but was a stop-gap solution because I didn't want to lose cpu scaling.  My laptop runs like an oven without it.

After doing some digging, I discovered some information about the kernel-based cpu speed governors (as opposed to powernnowd etc., which are user-space based).  With a little tweaking, I was able to use the cpufreq-ondemand governor which scales the processor according to load, without requiring a daemon running in the background.  This is exactly what I needed and it works like a charm, with the added benefit of being kernel-based which is apparently prefereable to userspace apps.

There are other governors for performance or powersaving, as well as a userspace governor if you want to allow an external control of the speed.

In my particular case, I default to ondemand but also load performance and powersave, I used kde and the klaptop icon in the taskbar allows easily switching between them if need be.

Unfortunately, I'm not sure if this is going to be of help to you rpdillon, sounds like you might be experiencing a similar but different issue, but may be of help to others with the issue that have narrowed it down to powernowd.

Cheers,
KV

---

### Post by jason_dc on 2005-07-25
I have the same problem with my Dell Precision M40

The stick mouses is fine, so I guess its the synaptic driver..

---

### Post by Kitty on 2005-07-25
You can try to pass *psmouse_rate=40* to the kernel.
It works for me (I had the same problem)

Edit /boot/grub/menu.list  like this :
kernel    /boot/vmlinuz..........root=/dev/hdbx ro psmouse_rate=40

Reboot and test! And report if it's working for you!

---

### Post by jason_dc on 2005-07-25
This doesnt solve it I am afraid.. :|

---

### Post by rpdillon on 2005-07-26
Update:

Tried "watch"ing the /proc/interrupts to check for the event count increasing during idle psaux times...no problems there.  No events were generated when I didn't use the touchpad.

Tried the psmouse_rate trick - no good on my machine.  Still have as much stuttering as ever, both on keyboard and mouse.

I emailed LAC linux support and they were pseudo-helpful.  They recommended turning down the update rate on my Klaptop applet from 20 secs to 120 or so.  I did, and it helped some, but that feels like a kludge to me...the real problem is that the call to update acpi status is blocking for some reason, and is on some interrupt so low that it takes precedence over psaux and keyboard (isn't keyboard usually on IRQ 3 or something?)  I'm thinking this is a kernel-level issue (since that is what has a lower IRQ than the keyboard) and I should recompile my Kubuntu kernel.

I'm guessing that there is some option enabled in their kernel that is hosing up my BIOS's implementation of ACPI.  More later if I get this working.  Luckily, I just removed Gentoo from this laptop to test out Kubuntu, so I have a pretty darn good idea what should go into the kernel.  =)

---

### Post by garretjax on 2005-07-27
I tihnk this might be a few different problems masquarading as one problem, given that symptoms are so close.

I know that some Dell laptops - C600 serries have an issue between the thumbstick and touchpad where the thumbstick sends random garbage to processior about movements when not being touched.  This is the one i am dealing with.  ?dev/psaux and /dev/input/mice seems to report movement from both the stick and the touch pad.  
What i have been trying to do is force X to only listen to Tocuhpad and usbmosue. This has been working ... sorta. I now don't have my mouse randomly trying to run to the upper or lower corner - but now it sometimes [have found no rhym or reason] decides to get choppy and sluggish.  
have tried disableing acpi -- see if that works.  But i think the thumbstick is still sending interupts to the processor, even though no program is listening to it ... 
If anyone has suggestions of how to completly disable the bloody thing, i think thats where my problem is. short of taking laptop apart and cutting wires. i am running out of ideas

Garret

---

### Post by Archalien on 2006-04-21
This thread looks old, bringing back from dead

I have an Alienware Sentia centrino based laptop.
I had ben using Fedora 4, b/c everything on my laptop worked oob, not even ubuntu could do this.  Well, since 2.6.13 in FC4 and FC5 my synaptics mouse stopped working.  it seems to be a kernel issue solely afecting my laptop,  thought Id give ubuntu another try afer reading this thread.

Well no go, KB and mouse stutter all to hell even w/ powernowd gone.
And since its still stuck in 2.6.12 I dont know if the 13+ kernel problem exists in ubuntu w/o compiling my own kernel.

So was hoping for some further help......

---

### Post by geek.de.nz on 2006-04-23
Have a look [here]("http://ubuntuforums.org/showthread.php?t=124567").

---

### Post by geek.de.nz on 2006-04-28
If you are still having problems, again, look [here]("http://ubuntuforums.org/showthread.php?p=964716#post964716")

---

