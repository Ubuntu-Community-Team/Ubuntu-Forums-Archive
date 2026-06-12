---
title: "Does hibernate and suspend work for you?"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by it.henrik on 2006-06-25
I think suspend should be something that works out of the box in efty. Let us show the devs how it works in dapper.

---

### Post by SnackySmores on 2006-06-25
sadly hibernate/suspend doesn't work for me. I have Dapper on my laptop(gateway 7422gx), so those options are really important. hopefully they'll fix it on the next realease.

---

### Post by krrh on 2006-06-25
I have a Toshiba Satellite A105-S2091, which was the $399 machine Best Buy advertised Memorial Day weekend.  Neither Suspend nor Hibernate work.

---

### Post by nanotube on 2006-06-25
i have a dell inspiron 5150, and it works for me on dapper after some tweaking ([http://ubuntuforums.org/showthread.php?t=201960](http://ubuntuforums.org/showthread.php?t=201960))
try some of the tweaks that are listed in that thread, and maybe it will start working for you as well.

---

### Post by Patsoe on 2006-06-25
Both functions work here. 
It only breaks with the proprietary Ati-fglrx drivers... so I try only loading those when I really need them...

There was a problem resuming when I had my usb mouse plugged in, but that's been resolved this week :)

---

### Post by spier on 2006-06-25
Everything in power management working out of the box here. Only an issue with battery life status, that prevents a critical action other than Nothing.

Edit: if it matters, running on Sony Vaio VGN FS740W

---

### Post by phibuntu on 2006-06-26
D*E*LL INSPIRON | 9300

[LIST]
[*]**Hoary** (ubuntu4): Hibernate worked in 3 of 4 cases. 
   (allways shut down, but sometimes did not come up after hibernate)

[*]**Breezy** (ubuntu5): Hibernate did **not** work at all

[*]**Dapper** (ubuntu6): Hibernate woked everytime (about 10 times till now)
[*]**Edgy Eft**: Hibernate works fine.
[/LIST]

Great feature :-)

---

### Post by gregh on 2006-06-26
HP Pavillion dv5000 Core duo

suspend/hibernate appear to work,  but when it resumes it immediatly re-boots (so its unusable)

-Greg

---

### Post by NikoC on 2006-06-26
Neither suspend or hibernate work on my Vaio S4HP. I have to be honest though and say that my last attempts to use Ubuntu were about a month ago so I have no idea how it is going right now.

---

### Post by fast1 on 2006-06-26
Both hibernate and suspend worked out of the box on my dell D620.

---

### Post by draculr on 2006-06-26
[QUOTE=fast1]Both hibernate and suspend worked out of the box on my dell D620.[/QUOTE]

Are you serious? My D820 does not work. Perhaps it has something to do with the nvidia card? I assume you have the intel GMA?

---

### Post by fast1 on 2006-06-26
Yes, I have the intel card.
btw. I think the suspend to ram requires the last kernel update.

---

### Post by drx on 2006-06-26
On my Thinkpad X41, neither hibernate or sleep work in dapper. In breezy they used to do so.
Now the computer crashes when it tries to come back to life.
This is really an issue, i need to reboot any time i want to use the laptop.

---

### Post by gmcgraw0 on 2006-06-26
Hibernate works for me on Toshiba Portege R100 (haven't tried suspend) running Dapper.  It takes a while but that is to be expected, I think.

---

### Post by wrtrdood on 2006-06-26
Fujitsu P1120 -- Breezy worked well all the time.  Upgrading to Dapper introduced an intermittent failure to return from suspend (to RAM).  Hibernate works well.  Running with the gnome-power-manager works well but I still had the resume issue.  Same with klaptop.  My default setup is E17 so it uses the scripts directly.  Had problems with LID detection (which might account for the resume problem mentioned) but it seems to be working now.  I used some of nanotube's suggestions (recommend taking a look at the link given) and things seem to be working a bit better.  Still testing...

---

### Post by lisje on 2006-06-26
I have a Toshiba Satellite Pro L20-102 and both hibernate and suspend worked in the "unstable dapper" I had on my laptop. (it was a clean install from flight 4 and updated untill two weeks ago, so it should resemble the now stable ubuntu 6.06)

Since I had to reinstall Ubuntu a few weeks ago, I installed the new Ubuntu 6.06, removing the "unstable" one... And it shocked me that the stable ubuntu from de cd didn't really resemble to what I had installed before.
Now hibernate and suspend doesn't work anymore and that's not the only thing...

I'm not really complaining a few things that started malfunctioning in the previous dapper install are fixed, but certainly not everything. And in return other things broke ... so I guess it comes down to about the same


*edit*
I found the problem... it was really stupid ... somehow the ubuntu install failed to detect where my swap partition was at... so when I tried hibernate again I got the some message indicating it couldn't find my swap-disk... soooo... I changed my /etc/fstab from:
```
/dev/hda3       none            swap    sw              0       0
```

to:
```
/dev/sda6      none            swap    sw              0       0
```
(since my laptop doesn't have a hda, because it has a sata drive)

---

### Post by syntaxer on 2006-06-28
for me personaly, suspend/hybernation works after upgrade dapper, but with some irq issues -- see the last comment by syntax_error in [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/32893](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/32893)
it drives me really mad, i've tried almost everything...

---

### Post by mvaranda on 2006-06-28
No... it does not.

My Thinkpad T42p freezes the GUI (mouse/cursor still moves).

My wife's Compaq R4000 (with i386 since AMD64 did not even install) also has similar issue.

My daughter's Toshiba M50-MX2 also has some issues. Both Compaq and Toshiba do not have "Suspend" option inside a gnome session. But if you leave (switching users) there is a suspend option in startup screen. But after waking up both have problem freezing the gnome GUI.

---

### Post by nanotube on 2006-06-29
[QUOTE=mvaranda]No... it does not.

My Thinkpad T42p freezes the GUI (mouse/cursor still moves).

My wife's Compaq R4000 (with i386 since AMD64 did not even install) also has similar issue.

My daughter's Toshiba M50-MX2 also has some issues. Both Compaq and Toshiba do not have "Suspend" option inside a gnome session. But if you leave (switching users) there is a suspend option in startup screen. But after waking up both have problem freezing the gnome GUI.[/QUOTE]
check the link i posted above, will show you how to enable suspend on the logout menu, and might also solve your problem with freezing upon resume.

---

### Post by Rollmops on 2006-06-30
Seems tu run fine on Samsung X20 notebook.

---

### Post by firehead on 2006-06-30
hi i'm running a sony vaio-s4xp (and proprietary nvidia-drivers), and hibernate works flawlessly out of the box in dapper(didn't work with breezy though)... suspend-to-ram/sleep works, but doesn't recover correctly (yet, but i'm not putting too much effort into it, since it don't really need it...).

---

### Post by sgusto on 2006-06-30
IBM T20 (2647-41U) 256MB 20G  Linksys WPC54Gv2  
Xubuntu 6.06  suspend/resume/hibernate do not work. 

I'd be VERY happy just to get suspend or standby to work where on lid-close or (Fn-F4) it sucessfully shuts down the cardbus, screen, & HD and can recover from that.  I was pretty surprised that this kind of basic functionality is so difficult to implement.  

Condsidering how popular the T20 was, I would think this has been addressed before and has a known fix for it.  There are some T20 pages out there but they generally don't specifically say how they got it to work.  

If anyone can walk me through getting it to work on a T20 I'd greatly appreciate it. 
I've been wrestling with it for days and this is pretty much a deal breaker for me. 

Love Unbuntu Dapper on my P4 desktop though! I've been using it for a few weeks.

gusto

---

### Post by madscience on 2006-06-30
Toshiba M30, using proprietary nvidia drivers (latest from repo):

Suspend and hibernate both work fine, both out of the box using the 'nv' driver, and with the 'nvidia' driver as long as I blacklist agpgart and intel_agp, and sent NvAGP 1 in xorg.conf.  From the research I've done, intel_agp and agpgart don't save the nvidia driver state properly.

On a related note, does anyone know of any tweaks to speed up hibernate?

---

### Post by sgusto on 2006-06-30
sorry, duplicate post

---

### Post by TrailerTrash on 2006-07-01
On my Dell C610..Everything works.....EVERYTHING WORKS! :KS

---

### Post by kpkeerthi on 2006-07-01
Both worked flawlessly out of the box. But after installing "nvidia" (binary restricted) they stopped working. If anyone had success with the binary driver please point me to the instructions. It would be a nice-to-have for me but not really required.

---

### Post by palmdoc on 2006-07-01
On Badger, HIbernate and Suspend (and indeed Shutdown) did not work properly.
I am happy to report all three work well on DD....

---

### Post by Peacepunk on 2006-07-01
Sony Vaio VGN-T17GP (intel855 chipset) subnotebook with 1280x768 xwga screen, on-line upgrade from Breezy to Dapper 6.06LTS: 

- Suspend works, off in 5 secs and on to Password in 35 secs - can't believe it, so slow, that's slower than de-hibernating from XP.

- Hibernate doesn't, faster to shutdown but 2 plain minutes to wake up (usual boot time 2 minutes 10 secs), "forgetting" 915resolution in the process

-Power Button pops on screen all the choices: disconnect/lock/switch/suspend/hibernate/reboot/shutdown.

I haven't checked if the Swap place is rightly configured for Hibernate, I don't know how to do that.


Keep the Pressure: A Free product that is poor becomes a cheap product.


Peacepunk

---

### Post by heri on 2006-07-01
Toshiba Tecra 8200 P3 850 Mhz 256MB RAM 20G HD no wifi.
Hibernate and suspend works fine with Dapper Drake.

---

### Post by wiresquire on 2006-07-03
I have a Mitac 8355 - AMD64, 512MB RAM, ATI Mobility 9600 with 128MB. I'm running 32 bit 6.06 with everything up to date (kernel 2.6.15-25-386) and using the open source ATI/radeon drivers with DRI enabled - NOT fglrx.

Hibernate doesn't work for me. It suspends to disk OK. But when I restart, I get the brown pinstripe lines. The hard disk light is permanently on and I can't switch to other consoles etc. I guess that means it's hung.... 

I also tried playing with some acpi-support options as outlined [here](http://ubuntuforums.org/showthread.php?t=201960), but they didn't help. :cry:

---

### Post by fast1 on 2006-07-03
I have to correct myself. Suspend does have some problems: after suspend I cannot see my cdrom anymore; I cannot even mount it.
```
$ mount /media/cdrom0 
mount: special device /dev/scd0 does not exist

```

---

### Post by rohan! on 2006-07-03
fujitso siemens amilo pro v8010d

works out of the box with both ubuntu and kubuntu (gnome and kde desktops) though i can only get kde suspends when i close the lid (not really a problem)

what i want to know is how to get suspend to work in fluxbox -- especially when i close the lid. i really just don't know where to start with this. if anyone could give us a clue then that's great :)

---

### Post by nanotube on 2006-07-03
[QUOTE=rohan!]fujitso siemens amilo pro v8010d

works out of the box with both ubuntu and kubuntu (gnome and kde desktops) though i can only get kde suspends when i close the lid (not really a problem)

what i want to know is how to get suspend to work in fluxbox -- especially when i close the lid. i really just don't know where to start with this. if anyone could give us a clue then that's great :)[/QUOTE]

hmm, i'd look at /etc/acpi/sleep.sh
when you execute that script, it should suspend. so you could suspend "manually" by making a shortcut to that script, maybe (possibly have to add argument "force" to it)

---

### Post by andrewabc on 2006-07-03
Suspend doesn't work on my HP pavilion 7966 desktop computer. It works fine in Windows most of the time.
When I try to suspend, it shuts down like it should, but then boots back into ubuntu, and gives me a popup that says it did not work right and directs me to [http://www.gnome.org/projects/gnome-power-manager/faq.html](http://www.gnome.org/projects/gnome-power-manager/faq.html)

---

### Post by vinodis on 2006-07-04
Yes. Both Suspend and Hibernate works well on my ubuntu. Mine is not a branded PC, its an assembled one with Via Motherboard and AMD 1.8ghz processor + 512 mb ram.

---

### Post by djdicbob on 2006-07-04
Suspend worked great on my Gateway Solo 9000, but with Dapper the usb craps out after resurrection.  Hibernate has never worked for me on any laptop..ubuntu or no

---

### Post by padangbond on 2006-07-04
Suspend and Hibernate worked flawlessly on my NEC Versa E400, and it had worked since Breezy. Interestingly also, this is the first ubuntu that successfully allows my computer to be rebooted (before it only stops at the end of reboot without actually rebooting)

---

### Post by rohan! on 2006-07-04
[QUOTE=nanotube]hmm, i'd look at /etc/acpi/sleep.sh
when you execute that script, it should suspend. so you could suspend "manually" by making a shortcut to that script, maybe (possibly have to add argument "force" to it)[/QUOTE]

I tried to execute by doing ```
. /etc/acpi/sleep.sh
``` and all it did was close the terminal that i was in, nothing else. any more clues?

cheers :)

---

### Post by nanotube on 2006-07-04
[QUOTE=rohan!]I tried to execute by doing ```
. /etc/acpi/sleep.sh
``` and all it did was close the terminal that i was in, nothing else. any more clues?

cheers :)[/QUOTE]
why put a dot in there? try instead:
```
/etc/acpi/sleep.sh force
```
and if that doesn't work, maybe the same thing with sudo:
```
sudo /etc/acpi/sleep.sh force
```

---

### Post by rohan! on 2006-07-04
[QUOTE=nanotube]why put a dot in there? try instead:
```
/etc/acpi/sleep.sh force
```
and if that doesn't work, maybe the same thing with sudo:
```
sudo /etc/acpi/sleep.sh force
```[/QUOTE]

haha, cheers -- i new i was doing something wrong!! :oops: 
when i sudo it works fine.

now the real issue is how do i assign this to a keybinding? or make it run when i close the lid?

---

### Post by nanotube on 2006-07-04
[QUOTE=rohan!]haha, cheers -- i new i was doing something wrong!! :oops: 
when i sudo it works fine.

now the real issue is how do i assign this to a keybinding? or make it run when i close the lid?[/QUOTE]
well, first thing to try is to run System>preferences>power management
and there to set the action for "when i close the lid" to be "suspend" and see if that works. :)

if it doesn't, then you can go to system>preferences>keyboard shortcuts and set a custom keybinding to run that sleep script.

---

### Post by rohan! on 2006-07-04
[QUOTE=nanotube]well, first thing to try is to run System>preferences>power management
and there to set the action for "when i close the lid" to be "suspend" and see if that works. :)

if it doesn't, then you can go to system>preferences>keyboard shortcuts and set a custom keybinding to run that sleep script.[/QUOTE]

Massive thanks again for the reply, but i'm sorry i don't think i made myself clear... i'm running Fluxbox not Gnome.

Don't worry if you don't know what to do in flux, i am able to assign the keybinding by editing the keys file in .fluxbox to run the command...it's not worked yet, but i'll get there :)

edit::
I want it not to ask for a password when i run it, because otherwise it doesn't work with the shortcut key, is there a way of getting past the password at all??

---

### Post by scottwill on 2006-07-04
alienware area 51 5500M

suspend/hibernate do not work whatsoever for either 5.10 or 6.06

It's really a bother as I do not want to leave it on all the time so I must shut down whenever I go somewhere. :?

---

### Post by nanotube on 2006-07-04
[QUOTE=rohan!]Massive thanks again for the reply, but i'm sorry i don't think i made myself clear... i'm running Fluxbox not Gnome.

Don't worry if you don't know what to do in flux, i am able to assign the keybinding by editing the keys file in .fluxbox to run the command...it's not worked yet, but i'll get there :)

edit::
I want it not to ask for a password when i run it, because otherwise it doesn't work with the shortcut key, is there a way of getting past the password at all??[/QUOTE]

heh no, you made yourself clear, i just didn't pay attention :)

to run that without entering password, you have to edit your sudoers file with "sudo visudo", and add a NOPASSWD entry for the sleep.sh command. search around about sudoers and nopasswd to find out the proper syntax.

---

### Post by examancer on 2006-07-04
Both hibernate and suspend work well after latest ACPI updates. Acer Aspire 3623WXMi. Hibernate sure does take a while though...

---

### Post by gn2 on 2006-08-08
Suspend works for me after enabling it in power management.

Standby from closing lid, resume on opening. Works flawlessly.

Toshiba Portege 3440CT Pentium3 500 192Mb RAM 40Gb HDD, Ubuntu Dapper.

I'm a linux noob, and I have to say that fault finding and fixing is easier than with any incarnation of Windows.

---

### Post by s0lar on 2006-08-08
Works out of the box, like almost everything. I am using a Dell Inspiron 9300.

---

### Post by audacity on 2006-08-11
I'm on a T20, and suspend starts, HDD spins down, and then nothing, mouse still works but when I click on something everything freezes. I am forced to poweroff and reboot. I believe it is similar if not the same to this bug:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50031](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50031)
It used to work just fine. I will try to regress to an earlier kernel and test.

---

### Post by audacity on 2006-08-11
Et voila! Writing this from the 2.6.15-23 kernel after a successful resume from suspend. So... something broke between 24 and 25/26(both are broken here). This older kernel is using APM.

---

### Post by allhope on 2006-08-11
I have an HP dv8000 and hibernate and suspend work perfectly for me with no manual configuration. :)

---

### Post by UltraMathMan on 2006-08-11
I needed to add the dependencies of usbcore to the list of modules to be shut down before suspend. Other then the occasional missuspend it has been working fine (I haven't tested hibernate yet.

I have a Inspiron E1505.

---

### Post by Lasborg on 2006-08-12
on my Compaq Presario 2169EA i have Hibernation but no Suspend.

:? 

Ill see if I can make it work

---

### Post by Melcar on 2006-08-12
On my Compaq V2000Z suspend seems to work fine (just got the laptop two days ago).  Haven't tried with hiberation.

Edit: Hibernate screws up my wireless connection.  I have to restart to get it to work again.

---

### Post by marin.r on 2006-08-12
Just tried suspend on my Thinkpad T23 and it goes to sleep well but on resume seems like the LCD doesn't switch on. I managed to shut it down with Alt+F4 and Enter, so it "almost resumes", only I can't get visual confirmation :D
Hibernation was OK though, 2 months ago when I tried DD for the 1st time.

---

### Post by williamgjames on 2006-08-12
My Toshiba Qosmio hibernates and suspends afer some tweaks ([http://www.ubuntuforums.org/showthread.php?p=1119601#post1119601](http://www.ubuntuforums.org/showthread.php?p=1119601#post1119601))

Only small issue is that it comes up locked and I have to enter password to resume.

---

### Post by k1773r37f on 2006-08-12
Compaq Presario v5125NR Hibernate works about half the time.  Suspend, still fighting with it.

---

### Post by SonWon on 2006-08-12
Mitac 8355 - AMD64, 1GB RAM, ATI Mobility 9600 with 128MB. I'm running 32 bit 6.06.

Hibernate and suspend doesn't work for me.

---

### Post by Cartwheels4amile on 2006-08-13
I'm running Xubuntu 6.06.1 on a Toshiba Portege 7140ct... neither suspend nor hibernate work yet. I'm trying to find out how to fix this as we speak :)

---

### Post by threethirty on 2006-08-13
I've had some serious problems you can read about them [here]("http://ubuntuforums.org/showthread.php?t=235365")

---

### Post by Dieter Komendera on 2006-08-13
I have a HP Compaq nc8230. Suspend didn't work out of the box with Dapper.
Then I found this thread:
[http://ubuntuforums.org/showthread.php?t=201960](http://ubuntuforums.org/showthread.php?t=201960)
after applying the changes suggested there, supend works!:D

---

### Post by mariner09 on 2006-08-13
I have a T41, I'm using the suspend2 kernel now and it works great.

Everything worked before, but I think suspend2 is much faster.

---

### Post by declanmullen on 2006-08-14
> Does hibernate and suspend work for you?

Suspend does not work and I realy realy wish it did  :(

The system tries but fails to restore from suspend (ie end up with a black screen and no system activity).

BTW, it is a Dell Inspiron 8100 with ATI graphics running "Ubuntu 6.06".

Update: :p 
Disabling DRI seems to have solved the suspend problems. See [http://www.ubuntuforums.org/showthread.php?p=1385579#post1385579](http://www.ubuntuforums.org/showthread.php?p=1385579#post1385579)

---

### Post by tibiker1966 on 2006-08-14
HP Pavilion ze4325, Dapper 6.06 (fully patched - no 3rd party drivers)
Dual-boot with Windows XP.

Neither Suspend nor hibernate work for Dapper, but both do work from XP :-({|= 

Haven't dug too deeply into hibernate.

Suspend: appears to put the system into the suspend state - everything powers down, and the activity LED "pulses" just as it does when suspending in XP.  However, when I attempt to resume from suspend, the laptop shuts down!  It appears to be a clean shutdown - not a crash.  This happens regardless of the method I use to resume (hit power button, hit "special function" button, etc).  

To be specific: when I attempt to resume, the power LED comes on solid, the disk starts to spin up, then "click" - the laptop powers off.  Nothing weird in the logs.  Pressing the power button again causes a normal boot.

Any tips on how to debug this?

thanks,

-K

---

### Post by gotthardt on 2006-08-14
I have a Thinkpad a22p running 6.06 with latest patches - I can make it suspend every time - but I have to remove the battery and powersupply so that I can wake it up! Shutdown works about a third of the time - Everything worked fine in one of the beta versions of dapper.
Steve

---

### Post by lexxonnet on 2006-08-14
I'm on a Dell Inspiron 8600, with an Ati 9600 Pro on fglrx drivers.

Suspend never quite worked for me.. It always suspended fine, but usually when resuming from suspend, there were roughly four scenarios:
1) My fglrx drivers would stop working well(MESA issue) - This is almost nonexistant now. Was mostly with an older kernel.
2) My Mouse scroll wheel, would simply stop working until I restarted X. - Happens quite often, and is most annoying
3) The computer wouldn't resume at all, and simply stay blank - Improved once again, but does happen once in a while, especially if suspended for a couple of hours or more
4) The computer would just get laggy, harddisk would be on a perpetual write/read cycle, and things would become close to unworkable - Started to happen with this kernel(quite often), and after mysteriously losing my previous harddisk to a boot sector error, I'm not too keen on trying it again.

Most of the time, it was a combination of 1,2 and 3... but of late, scenario 4 has been happening too often.

As for hibernate, it was always a hit and a miss. fglrx drivers and all resumed perfectly, but things like the mouse scroll wheel not working still were annoying.
Also, some times it just refuses to resume from hibernate(blank screen).

Of late, I've taken to using a suspend2 patched kernel, and hibernate(suspend2's hibernate) is working like a charm so far. Quite honestly, I dont see why suspend2 isn't already in ubuntu. Its definitely the most reliable hibernation I've ever had.

---

### Post by e00878 on 2006-08-14
On ASUS A6J T2400 hibernate works. Problem persist only when something like usbdisk or TV-OUT during hibernation is attached or detached. Sometimes after logout and login fglrx driver dissapeart and glxgears won't work :)

---

### Post by kleedrac on 2006-08-15
> **examancer said:**
> Both hibernate and suspend work well after latest ACPI updates. Acer Aspire 3623WXMi. Hibernate sure does take a while though...

Same for me ... is there any way to speed up the hibernate?  Also my wireless network cuts out after resuming from hibernate.

---

### Post by ken_no on 2006-08-23
Neither sleep nor hibernate works on my Thinkpad t22.

---

### Post by xp_newbie on 2006-08-24
Suspend works - but only the first time after a machine restart... That is, if I close my laptop's cover (Lenovo 3000 N100), let it suspend by itself and come back an hour later - I will find it in the same exact state. However ,if I repeat the same thing again without shutting the laptop first, it returns with a completely dead system (except that for some reason the power LED is on and I need to shut it down in order to reboot again).

Hibernate seems to work - although I have not tested it yet in the above described scenario.

---

### Post by garrye on 2006-08-24
Actually yes!
Acer Aspire 3003 WLCI
Just got back from a service call and brought it out of hibernation.  While the process is a bit cheezy, it does work.  On power up the bios splash displays, followed by the boot manager and the first part of the normal startup.  When it gets to the "mounting root filesystem" there is a sizeable pause while the image is loaded, the display goes to this crappy looking series of vertical brown bars separated by black lines, then the bios splash is displayed squeezed into the upper half of the display with the colors all screwy (4 bit display?) and the bottom half black (blank?).  Then the display resets and the login prompt is displayed.  On login the session with all things I had going is still there.  Things like login to this forum have expired which is normal.  The wireless connection comes up working and I am now typing this post!!!

Yee Hawwwww.  This is sweeeeeet!

Only the wireless is somewhat flakey with loss of connectivity from time to time which requires that I code "sudo ifdown ath0" followed by "sudo ifup ath0"

Oh and once in a while when I pull the AC adapter off the lappy, ubuntu determines that the battery is nearly dead and promptly goes to shut down even though the front panel indicator says the battery is fully charged.

Everything **(EVERYTHING)** else works perfectly

Need to look at redoing the DSDT maybe.  Dunno

---

### Post by ghettobilly on 2006-08-27
hp xf328

suspend and hibernate work , hibernate has a few problems ... after power back on have to alt-F7 for login also all sound mixer settings dont get restored (all mutted) have to open volume panel raise vol and unmute them all

---

### Post by CSMatt on 2006-09-04
Sony VAIO VGN-FE660G:

Suspend and hibernate work.  Hibernate causes wireless and trackpad scrolling problems upon revival; Suspend causes sound and stability issues upon revival, often times not even recognizing the keyboard and thusly making it impossible to enter the password.

---

### Post by SonWon on 2006-09-04
I have a question for the developers.  Why are they working on Edgy while there are problems with Dapper?

~SonWon

---

### Post by rohan! on 2006-09-04
> **SonWon said:**
> I have a question for the developers.  Why are they working on Edgy while there are problems with Dapper?

~SonWon

I think that the issues aren't actually with ubuntu, but with the suspend/hibernate program itself, there is little that ubuntu developers can really do about this.

As for developers working on edgy, not all of them are, there are still developers working on dapper, for example backports etc.

maybe i'm wrong with all of that, am a bit clueless, but that's the impression that i get :)

---

### Post by SonWon on 2006-09-04
Hmm, that makes sense.  Does anyone have a url for the developers who are working on the suspend/hibernate program.

---

### Post by Mimsy on 2006-09-04
Compaq Evo N410c - hibernate works almost all the time.The one time it didn't it shut down as I was trying to get it out of hibernation. Not a crash, I think, it went through the entire list of things to shut down, just as it does when you close it down normally. I haven't tried suspend yet, but I might, some time soon. I have battery life issues right now, that are far more important to me. I logged on to search the forums for answers to those issues when I found this thread...

/Mimsy

---

### Post by twowheeler on 2006-09-04
Suspend works great after some tweaking.  My BIOS is supposed to resume from a keypress but that doesn't work.  There are other special functions in this BIOS (instant music, etc) that also don't work, so I don't believe it is ubuntu's fault.  Anyway, pressing the power butter causes resume to occur normally.  One odd thing is that LOCK_SCREEN=false makes no difference -- it insists on a password regardless.  No biggie.

Hibernation is a different story.  With HIBERNATE_MODE=shutdown, the system appears to hibernate but just reboots instead of performing a resume.  With HIBERNATE_MODE=platform, the system tries but fails to enter hibernation and reports a HAL problem, please read the FAQs.

Still experimenting and reading the forums.  It "should" work since:

> dan@ubuntu:~$ cat /sys/power/state
standby mem disk


System is an ASUS P4S800 motherboard and Nvidia Geforce4 Mx4000 video, 1GB SDRAM, and 120GB EIDE disk.  There is a 3GB swap partition.

Edit: There is a BIOS update available from ASUS that has something to do with sleep states.  I plan to try it out next.

Edit2:  Flashed BIOS, now neither suspend nor hibernate works!  ](*,)   Back to fiddling.

---

### Post by insyzygy on 2006-09-05
I have used dapper on three laptops

Inspiron 8500-neither suspend nor hibernate work.

Thinkpad X20-suspend works but only outside of gnome (I use fluxbox)

ibook g3 -suspend works flawlessly.

Ironically the ibook which is sort oddball running linux had suspend and wifi
work out of the box (then again mac hardware is all exactly the same so if they get it working on one of them it works on all of them).

---

### Post by littleiffel on 2006-09-05
On my Thinkpad x60, suspend/hibernate both work. First it was quite hard to get it working, but with the latest kernel(o almost the latest) suspend/hibernate works perfectly well.

---

### Post by bgg71 on 2006-09-05
If you have dell true mobile you need to install either the bcm43xx or ndiswrapper. It will not work out of the box. You probably have intel wireless and intel GMA. On my D600 I have ATI Radion 9000 mobility 32Mb graphics card/Dell true mobile 1300 wireless card. Now everything works but I had to do some twiking.

---

### Post by David Gerard on 2006-09-07
Compaq Evo N410c - hibernate and suspend both work, though not as reliably as I'd like. I blame the W200 wireless card, as the orinoco_usb driver is so early-beta it's only available from CVS ...

---

### Post by Mimsy on 2006-09-07
Now that I have used Ubuntu on the Evo N410c for a little longer, and frequently used the hibernate option, I'm forced to agree with David. It wors, but not as reliably as I would like. I often get a crash when I try to leave hibernation mode, and have to do a forced reboot with the help of the little blue power button in the upperleft corner. I have found myself grateful for OpenOffice's restore function.

But it crashes a lot less than XP ever did, so I'm happy anyway. I'm so tempted to get one of those pretty new supersleek laptops, buy it free of software, and install Ubuntu....

Ubuntu on a Macbook would be so cool. \\:D/ 

/Mimsy

---

### Post by garrye on 2006-09-07
> **garrye said:**
> Actually yes!
Acer Aspire 3003 WLCI
Just got back from a service call and brought it out of hibernation.  While the process is a bit cheezy, it does work.  On power up the bios splash displays, followed by the boot manager and the first part of the normal startup.  When it gets to the "mounting root filesystem" there is a sizeable pause while the image is loaded, the display goes to this crappy looking series of vertical brown bars separated by black lines, then the bios splash is displayed squeezed into the upper half of the display with the colors all screwy (4 bit display?) and the bottom half black (blank?).  Then the display resets and the login prompt is displayed.  On login the session with all things I had going is still there.  Things like login to this forum have expired which is normal.  The wireless connection comes up working and I am now typing this post!!!

Yee Hawwwww.  This is sweeeeeet!

Only the wireless is somewhat flakey with loss of connectivity from time to time which requires that I code "sudo ifdown ath0" followed by "sudo ifup ath0"

Oh and once in a while when I pull the AC adapter off the lappy, ubuntu determines that the battery is nearly dead and promptly goes to shut down even though the front panel indicator says the battery is fully charged.

Everything **(EVERYTHING)** else works perfectly

Need to look at redoing the DSDT maybe.  Dunno


Further on the hiberation thing, I neglected to mention one other thing that I did observe.  There are two instances of "hald-addon-storage" running under "hald-runner" which is running under "hald".  From time to time system monitor shows the status of one, other, or both instances of "hald-addon-storage" changing from "sleeping" to "uninterruptible".  The status usually changes back to "sleeping" in short order.  Once in a while the status goes to "uninterruptible" and stays there.  When in the "uninterruptible" state they cannot be ended or killed.  If I insert a CD at this time it does not mount.  An attempt to suspend when this happens will fail with a message about processes that cannot be ended or something to that affect, and I'm returned to the login prompt.  I can log in and continue with the session still all there and fully functional.

I noticed this behavior while I was testing a replacement built in Mini PCI wireless adapter.  This laptop shipped with Broadcom 4318 wireless silicon.  I removed this, sold it, and replaced it with an XG-621 which shows up in lspci as: 0000:00:0b.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01).  I was testing wpa_supplicant's behavior by running it in a terminal in debug mode.  The wireless connection kept dropping at extreme range as well.  Finally I did the dumb thing and turned wpa_supplicant loose as a daemon.  Lo and behold the wireless connection is now only rarely susceptible to drops and this is every bit as good as in the co-installed winxp.  Since I turned wpa_supplicant loose as a daemon I no longer see instances of "hald-addon-storage" assuming an "uninterruptible" state,  CD's always mount properly, and suspend and hibernate work almost all of the time.

This would suggest some sort of inter-action between processes that causes grief with power management among other things. Huh?  Comments??

BTW kudos to the Ubuntu team.  This is one cheep crappy laptop. Look at this!

lspci | grep SiS
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter

and yet other than the occasional hiccup it just trucks along, keeping on keeping on!!!!

Makes me proud to be an Ubuntu user!!!

Hope this helps somebody along the way.

---

### Post by Nathaniel on 2006-09-07
ThinkPad T43 1871:

Both suspend and hibernate are broken in Dapper. It seems it always works the VERY FIRST time I try it, and after that it'w broken forever. Suspend worked perfectly in breezy, used to work in the first dapper kernel, and is now broken most everywhere.

Seems they're making some progress in Edgy, but it's still higly unstable. It's pure chance if it wakes up from suspending (but it always does suspend... it's the waking that rarely works :()

---

### Post by reedatschool on 2006-09-08
Installed Edgy Knot 2 a few days ago on my Presario V3000 (V3018CL Dual AMD TL-50 and Nvidia Graphics).  

Suspend works great and it is really fast.

Hibernate does not work correctly.

---

### Post by proselyte on 2006-10-17
> **allhope said:**
> I have an HP dv8000 and hibernate and suspend work perfectly for me with no manual configuration. :)

as do i, but i am not so lucky, what are your specs? are you using the binary nvidia driver?

---

### Post by raincoat on 2007-04-09
Hi there,

I am running Ubuntu Edgy 6.10 on Asus A6J - Q 001H with ATI Mobility Radeon x1600 using the proprietary driver Version 8.35.5 from ATI  because I want big desktop support ([http://ati.amd.com/support/drivers/linux/linux-radeon.html)](http://ati.amd.com/support/drivers/linux/linux-radeon.html)).
Suspend to ram and disk worked after changes in /etc/default/acpi-support but broke up mouse and network in 25% of my tests.

So I installed suspend2 from [http://3v1n0.tuxfamily.org/dists/edgy/suspend2/](http://3v1n0.tuxfamily.org/dists/edgy/suspend2/) (thanks for your contribution, Treviño!)

hibernate-disk and hibernate-ram work fast and reliable! Resuming breaks up the network-manager so I have to reconnect. No proplem to me because I often switch office-locations anyway.

My config:
/boot/grub/menu.lst:
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro acpi_sleep=s3_bios,s3_mode splash vga=791 resume2=swap:/dev/hda5 apm=off
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
..

/etc/default/acpi-support:
bootACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=s3_bios
MODULES=""
MODULES_WHITELIST="usbhid hiddev ehci_hcd uhci_hcd"
VBESTATE=/var/lib/acpi-support/vbestate
POST_VIDEO=false
SAVE_VIDEO_PCI_STATE=false
USE_DPMS=false
HIBERNATE_MODE=shutdown
STOP_SERVICES="mysql "
RESTART_IRDA=false
ENABLE_LAPTOP_MODE=false
# end /etc/default/acpi-support #

/etc/hibernate/suspend2.conf:
UseSuspend2 yes
Reboot no
EnableEscape yes
DefaultConsoleLevel 1
Compressor lzf
PowerdownMethod 5
ProcSetting userui_program /usr/bin/suspend2ui_usplash
FullSpeedCPU yes
## ATi Card suspend hack - Read more here: [http://wiki.cchtml.com/index.php/Suspend2](http://wiki.cchtml.com/index.php/Suspend2)
########
ProcSetting extra_pages_allowance 9000 
Include common.conf
# end /etc/hibernate/suspend2.conf #

/etc/hibernate/common.conf:
Verbosity 0
LogFile /var/log/hibernate.log
LogVerbosity 1
Distribution debian
Bootsplash on
BootsplashConfig /etc/bootsplash/default/config/bootsplash-1024x768.cfg
SaveClock restore-only
FBSplash on
FBSplashTheme suspend2
UnmountFSTypes smbfs nfs
UnloadBlacklistedModules yes
LoadModules auto
SwitchToTextMode yes
XStatus gnome
XSuspendText Preparing to suspend...
XResumeText Resuming from suspend...
# end /etc/hibernate/common.conf

/etc/hibernate/ram.conf
UseSysfsPowerState mem
Include common.con
# end /etc/hibernate/common.conf

/etc/hibernate/blacklisted-modules:
added 
wlan_scan_sta
wlan

The other config files are left unchanged.

Good luck!

   Steffen

[http://www.ed-media.org](http://www.ed-media.org)

---

### Post by CSMatt on 2007-04-10
I use an ASUS V6Va.  Hibernation worked in Dapper, although it was no faster than a normal boot upon awakening.  Suspend worked, but the screen would not turn on upon revival.  Hibernation does not work at all on Edgy, any attempts to boot from the hibernated state result in a normal boot.  The V6Va has an ATI Mobility Radeon x700 and I am using the free driver.  I have not edited any major settings, with the exception of any recommended [here](https://help.ubuntu.com/community/SuspendHowto).

---

### Post by scholzilla on 2007-07-05
I'm using a Gateway MT6452 laptop and hibernation used to work for me, but doesn't any more. My power settings are set so that the machine should hibernate when the lid is shut, and it used to work but now it doesn't. Also, I've noticed that my network connection won't work any more after closing the lid unless I restart the machine.

---

### Post by phenest on 2007-10-10
I have a HP TC1100 tablet pc. I have both Feisty and Gutsy installed. Feisty kernel: 2.6.20-16-generic and Gutsy kernel: 2.6.22-14-generic

Both installs have the same setup. Suspend and hibernate work in both installs. Sleep, however, is a different story. Sleep works fine in Feisty, but here's what happens in Gutsy:

I wait for the computer to enter sleep with the power light flashing. So far, so good. I press the power button and the computer wakes up fine. It then gives an error about the computer failed to suspend. :confused: It then then goes into hibernation and switches off. I then turn the computer back on, and it wakes from hibernation without any problem.

Weird, eh?

---

### Post by trudgiad on 2007-10-17
> I wait for the computer to enter sleep with the power light flashing. So far, so good. I press the power button and the computer wakes up fine. It then gives an error about the computer failed to suspend. It then then goes into hibernation and switches off. I then turn the computer back on, and it wakes from hibernation without any problem.

I am getting exactly the same problem, identical sequence of events, on a Dell Inspiron 640m. Just upgraded to Gutsy RC, used to work fine on Feisty.

---

### Post by ubunt22rock on 2007-10-27
no doesn work for me either
ubuntu 7.10..
acer TM3282

---

### Post by dmz17 on 2007-10-27
Nope. T61p

---

### Post by LordThundering on 2007-11-20
My suspend & hibernate stoped working on gutsy. can somebody give me any hints as to how to debug suspend?

What happens exactly: is this: machine goes into suspend (it doesn't go into hibernate, but i don't care for that) and comes up - but then freezes up completly, i never get any password -screen or simliar - it seems to do some work, but then freezes up completely. 
Very very annoying ;(

---

### Post by corte123 on 2007-11-25
had problems with feisty, but both work 100% with gutsy an my thinkpad x60 tablet :)

---

### Post by idefixuk on 2007-12-07
just joined the forum, main problem being my laptop doesn't hibernate. It's a Toshiba Portege R500 and I have Ubuntu 7.10. Is there a solution?

---

### Post by CSMatt on 2007-12-10
Not a simple one, I'm afraid.

BTW, neither suspend nor hibernate work on my ASUS V6Va in Gutsy.  Hibernate fails, while suspend won't wake up,

---

### Post by freonchill on 2007-12-26
dell inspiron 1150
p-4 2.8ghz mobile
855pm chipset
intel built-in video
1gb pc2700
30gb
dell 1390 (broadcom 4403)
ubuntu gutsy 7.10

suspend and hibernate work
but when come back from hibernate / suspend - video all screwed up
have to ctrl+alt+backspace to restart X

suggestions?

---

### Post by molom on 2007-12-30
This is one major problem for laptops.

---

### Post by XP-FREAK on 2007-12-30
Using Ubuntu Gusty 64bit und my Dell Vostro 1500

Suspend works out of the box, hibernate makes problem.
The system hangs up on hibernating.

---

### Post by steveneddy on 2007-12-30
I was having suspend issues with my Gutsy installed laptop. Also startup issues related to the hwclock.

Installing a 32 bit version of util-linux from packages.ubuntu.com solved my issues.

My hwclock stopped working due to a bug in the 64 bit Ubuntu OS.

It goes to suspend to RAM in about 5-7 seconds and takes 5 seconds to wake fully.

Intel Core 2 Duo @ 2 Ghz - Gutsy 64 bit - nVidia

:popcorn:

---

### Post by snakeeyes on 2007-12-30
For hibernate and suspend I think u should turn off compiz fusion and use kpowersave to suspend and hibernate.

---

