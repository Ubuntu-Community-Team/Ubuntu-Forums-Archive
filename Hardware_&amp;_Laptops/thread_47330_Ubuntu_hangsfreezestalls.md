---
title: "Ubuntu hangs/freeze/stalls"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by LagoniX on 2005-07-08
Hi,

I don't know if its a ubuntu, hardware or kernel problem, so here goes..

I have a running ubuntu machine which stalls from tine to time. :(
The machine can run from 20 min. to 20 hours before it hangs.
There are no special user event that make it stalls.

When I call it 'stalls', it is not true, the system is still running, just very very slow. 
It takes about 30 seconds to update the system clock by one second, a shutdown takes about 20-30 minutes.
The logs files doesn't give any clues too why this happens.(I be happy to apply them, if needed)

I have run memtest86+, no problems found here.
Tried different RAM blocks.
I have tried to reinstall ubuntu selves times, even a base setup stalls
Added diffent acpi paramteres to the grub.
Build own kernel without apm/apci.
I have tried to remove some of the hardware.
Updated firmware/bios on the system.
Tried different kernels both i386 and i686.
Stopped GDM/Gnome, leaving the system at tty1.
Stopped powernowd.
Stopped acpid.
Tried without vmware installed

But nothings helps, it still stalls.

Any help are welcome..

Hardware:
IBM Netvista 8309-72G
1280 MB RAM (1* 1024 & 1* 256)
Matrox G400 AGP
Adaptec 2940UW
1 * HDS722525VLAT80 HD
1 * IC35L060AVV207-0 HD
1 * BTC DVD-RW IDE1008

---

### Post by jspyro on 2005-07-12
I'm thrilled to hear that I'm not alone. I have the exact same problem.

Just like you said, nothing shows up in the logs. I ran "tail -f " on a whole bunch of logs, got some music playing and simply waited for it to stop. When it did the entire system was all syrup-ish, even switching to console-mode or killing X took ages, still the logs were untouched. A simple system beep would continue for about 3-4 minutes. That's not even funny.

What I find most annoying is not being able to reproduce the problem, other than  turning it on and keep working until it hits the wall.

IBM NetVista 8305-21G
P4 2 GHz   512+256 MB RAM
IDE drives 40+160 GB
Nvidia fx5200
Soundblaster live 5.1

At least it's not your/my imagination  :)

---

### Post by varunus on 2005-07-12
Can you open the gnome-system-monitor from applications->system tools and watch if any app takes a large amount of CPU or RAM when the stalling occurs?

---

### Post by LagoniX on 2005-07-12
Hi jspyro (and others)

I am happy to hear that i am not the only one with this problem.
The symptoms you describe(beeps, empty logs and no idea how to reproduce the problem), are the same as I have. 

[QUOTE=varunus]Can you open the gnome-system-monitor from applications->system tools and watch if any app takes a large amount of CPU or RAM when the stalling occurs?[/QUOTE]

I give it a try, the next the system stalls.
But I run 'top' one time when it 'stalled' and there was no app. that took a large amount of the CPU.
I can't remember anything about the RAM usages.

To me it looks more like a kernel, subsystem or IBM problem(but I only guessing ;) )

---

### Post by harryf on 2005-07-15
Had what sounds like the same problem on a very old PC (P2, 128Mb RAM etc) running Hoary (upgraded from Warty), to the point where it was so bad I basically couldn't capture any useful information about what was happening - could hardly do anything from the moment Gnome (slowly) started.

Just about managed to get top running once which showed nothing useful.

The only real indication was the hard disk was spinning like crazy the entire time, like it was trying to read or write to swap and seemingly (how it sounded) in very small "chunks".

What's disturbing was I'd been running Ubuntu for about six months on that box, no problems, then, overnight, it starts acting up. It coincided with a bunch of updates around the recent zlib security update (about 2 weeks ago I think) although whether that was the trigger or something else that had been growing over time, I don't know. Made no significant changes to anything around that time.

Finally gave up and reinstalled - no problems for now.

Would be interested in hearing recommendations for tools to monitor disk io and which processes are doing so.

---

### Post by jspyro on 2005-07-15
Hm, that was interesting harryf. As you said, such an app should exist.

Also I'd like to add that I had the same problem when running Slackware with swaret and dropline on the same machine. Think I'll try some other dists when I find the time.

---

### Post by ariel on 2005-11-03
Same problem here! Same Netvista machine. Googling around i found a number of other people all having the same problem with debian-based distros, mostly ubuntu. but no hint!! 
any clue, anyone??

thanks!

---

### Post by ariel on 2005-11-03
12

---

### Post by mwillems on 2005-11-03
Same problem here. And nothing is happening after it locks: see the log below.

Nov  2 22:38:01 ws-office gconfd (root-3527): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Nov  2 22:46:01 ws-office gconfd (root-3527): GConf server is not in use, shutting down.
Nov  2 22:46:01 ws-office gconfd (root-3527): Exiting
Nov  2 23:05:41 ws-office -- MARK --
Nov  2 23:25:41 ws-office -- MARK --
Nov  2 23:45:41 ws-office -- MARK --
Nov  3 00:05:41 ws-office -- MARK --
Nov  3 00:25:41 ws-office -- MARK --
Nov  3 00:45:41 ws-office -- MARK --
Nov  3 01:05:41 ws-office -- MARK --
Nov  3 01:25:41 ws-office -- MARK --
Nov  3 01:45:41 ws-office -- MARK --
Nov  3 02:05:41 ws-office -- MARK --
Nov  3 02:25:41 ws-office -- MARK --
Nov  3 02:45:41 ws-office -- MARK --
Nov  3 03:05:41 ws-office -- MARK --
Nov  3 03:25:41 ws-office -- MARK --
Nov  3 03:45:41 ws-office -- MARK --
Nov  3 04:05:41 ws-office -- MARK --
Nov  3 04:25:41 ws-office -- MARK --
Nov  3 04:45:41 ws-office -- MARK --
Nov  3 05:05:41 ws-office -- MARK --
Nov  3 05:25:41 ws-office -- MARK --
Nov  3 05:45:41 ws-office -- MARK --
Nov  3 21:50:13 ws-office syslogd 1.4.1#17ubuntu3: restart.

...that means it locks after 5:45 and until I reset it at 9:50, nothing happens in the logs.

My PC is a modern one that works perfectly fine with XP.

---

### Post by ariel on 2005-11-14
any news on this issue? i am having the same problem with my netvista machine i tried lots of stuff (changing video drivers, different kernels, even built my own 2.6.14, etc). the machine runs from somewhere between 20 minutes and 2 days, then it comes this strange "quasi freeze" thing....

any clue anyone??

Thanks!

---

### Post by ariel on 2005-11-16
Solution: install the kubuntu-desktop package, and use kdm instead of gdm. Weird, but it seems to work fine...

---

### Post by LagoniX on 2005-11-17
Hi ariel,

I am sorry but I don't believe in that Kbuntu sovels the problem..  :(

My computer also 'stalls' when its running in single user mode(init 3), so I don't think gnome/gdm/X etc. is the problem, but more likely the kernel or some kernel module(and a series of IBM netvista machines).

So if there is someone out there, who would help me figure out the problem is or give me a hint howto get more kernel messages.

Thanks....

---

### Post by LagoniX on 2005-11-18
This could be the problem..

[http://bugzilla.kernel.org/show_bug.cgi?id=4235]("http://bugzilla.kernel.org/show_bug.cgi?id=4235")

There are more info at : [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=284477]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=284477")

---

### Post by doitashimashite on 2005-11-18
I had spontaneous lockups too (5.10 running on new fancy hardware).
What helped me, was a re-installation, and boot the CD with this parameter at the boot prompt:

linux noapic nolapic

You might give this a try. It saved me a lot of frustration!

---

### Post by ariel on 2005-11-19
[QUOTE=LagoniX]Hi ariel,

I am sorry but I don't believe in that Kbuntu sovels the problem..  :(

My computer also 'stalls' when its running in single user mode(init 3), so I don't think gnome/gdm/X etc. is the problem, but more likely the kernel or some kernel module(and a series of IBM netvista machines).

So if there is someone out there, who would help me figure out the problem is or give me a hint howto get more kernel messages.

Thanks....[/QUOTE]

You are totally right.... it didn't solve the problem, only it took longer (3 days) to show up.  It was very frustrating looking at kde's clock showing 3:45AM time when I got to the office at 8:30. In summary i tried:
          - different video drivers (the machine has onboard i810 chipset) including vesa
          - disabling acpi and powermanager and actually  removing all power mgmt related modules
          - built a vanilla 2.6.14 kernel; also tried many other stock kernels
          - disabling all power management in the machine's bios
          - upgrading machine bios to latest release

So guys, I downloaded and installed Kanotix @the office, so far so good (3 days, I am approaching my record uptime :-). @Home I have ubuntu breeze and now I can further appreciate how great breeze is. Both distros are debian derivatives so I do feel comfortable with Kanotix as well. However I hope someone at IBM will notice this problem (I have found  several similar reports on Netvista desktop machines same model as mine) and help the ubuntu community get this fixed. My company has hundreds of these machines and with the current issue they would never be able to migrate the desktops to ubuntu...

---

### Post by ariel on 2005-11-19
[QUOTE=LagoniX]This could be the problem..

[http://bugzilla.kernel.org/show_bug.cgi?id=4235]("http://bugzilla.kernel.org/show_bug.cgi?id=4235")

There are more info at : [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=284477]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=284477")[/QUOTE]

doesn't look like the same issue. my display is still alive, i can move the mouse and click the icons, only e.g. if you click the terminal applet icon, it takes about five minutes to open the new window. then you press a key and it will show up a few minutes later. And curiously gnome or kde clock shows a bizarre time, not the computer clock time; maybe they show the hour everything went wrong.

---

### Post by LagoniX on 2005-11-21
[QUOTE=ariel]doesn't look like the same issue. my display is still alive, i can move the mouse and click the icons, only e.g. if you click the terminal applet icon, it takes about five minutes to open the new window. then you press a key and it will show up a few minutes later. And curiously gnome or kde clock shows a bizarre time, not the computer clock time; maybe they show the hour everything went wrong.[/QUOTE]

The kernel.org bugreport could still have something to do with the problem, but i will agree that the disscription in the bugreport doesnt looks like our problem.

I found the link to the kernel bugreport in debian bugreport #284477, which describe a problem similar to ours.

Right now i am testing a custom build kernel with X86_UP_IOAPIC=n
I will report if it works.

---

### Post by LagoniX on 2005-11-27
[QUOTE=LagoniX]Right now i am testing a custom build kernel with X86_UP_IOAPIC=n
I will report if it works.[/QUOTE]

Well my machine is still running at full speed, so this could be a workaround??

---

### Post by onur on 2005-11-28
I got the same problem with ThinkCentre S50!
So far (I am still testing) the bios update worked as stated in Debian Bug Report Logs [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=284477]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=284477")


Bios Update Link: [http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=TCTR-ERRN91]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=TCTR-ERRN91")

Ubuntu Rocks!

---

### Post by LagoniX on 2005-12-12
[QUOTE=onur]I got the same problem with ThinkCentre S50!
So far (I am still testing) the bios update worked as stated in Debian Bug Report Logs .....
[/QUOTE]

New BIOS didn't work for me, but my own kernel i still running.. 
Uptime about 14 days, so disable the X86_UP_IOAPIC in the kernel solve my problem..

Hope if this is any help to others then me..

---

### Post by kenweill on 2005-12-23
I too had the same problem with IBM ThinkCentre A50, before.

Solved my problem after adding the "noapic" and "apic=off" in the kernel parameter.

Just do:
sudo gedit /boot/grub/menu.lst

From there you can edit the kernel parameter.

---

### Post by LagoniX on 2005-12-23
[QUOTE=kenweill]I too had the same problem with IBM ThinkCentre A50, before.

Solved my problem after adding the "noapic" and "apic=off" in the kernel parameter.

Just do:
sudo gedit /boot/grub/menu.lst

From there you can edit the kernel parameter.[/QUOTE]

Hi, kenweill

I have tried diffcent kernel parameters in the grub.
Their dont work i my case.

/LagoniX

---

### Post by jspyro on 2006-02-06
I tried the bootparams, and they solved the problem for me. 
It's been running smoothly for about two weeks now.

Using IBM NetVista type 8305-21G / Breezy

---

### Post by inkpassion on 2006-02-16
[QUOTE=kenweill]I too had the same problem with IBM ThinkCentre A50, before.

Solved my problem after adding the "noapic" and "apic=off" in the kernel parameter.

Just do:
sudo gedit /boot/grub/menu.lst

From there you can edit the kernel parameter.[/QUOTE]


This fixed my NetVista issue.

---

### Post by RCRedneck on 2006-02-25
Tried adding the no apic stuff too but it didn't work for my 8310. Where in the file do I add the params?

Thanks..

Mike

---

### Post by Bruce Adams on 2006-02-25
Half way down this page, [https://wiki.ubuntu.com/GrubHowto](https://wiki.ubuntu.com/GrubHowto), describes it pretty well.

[QUOTE=RCRedneck]Tried adding the no apic stuff too but it didn't work for my 8310. Where in the file do I add the params?

Thanks..

Mike[/QUOTE]

---

### Post by RCRedneck on 2006-02-25
Perfect. Thanks!

[QUOTE=Bruce Adams]Half way down this page, [https://wiki.ubuntu.com/GrubHowto](https://wiki.ubuntu.com/GrubHowto), describes it pretty well.[/QUOTE]

---

### Post by bfbay315 on 2006-03-22
running kubuntu breezy
Ibm netvista <-- huge part of problem
P4 2.4ghz
256mb ram
ati radeon 7000 <- get an nvidia card!


I had the same problem as everyone else here.. System didn't freeze, but became very slow and seemingly unresponsive....The clock made the phrase "minutes seemed like hours" into a literal expression, as it would come to a stand still.

I put the noapic stuff in my boot params and it still became slow..I tried diffrent distro's, diffrent video cards/drivers, diffrent memory, diffrent kernels, ran without X, none of these fixed the problem.

SOLUTION: apt-get remove powernd
or in synaptic search for powernd and remove it

I also disabled any power managment settings in my bios..including fan control

Hope this helps someone.

Brian

---

### Post by bfbay315 on 2006-03-23
well I thought i was good, but hangs continue..

Is it possible that a dead or almost dead cmos battery could be causing the hangs and cause the clock to become very slow??



Thanks
Brian

---

### Post by telepathetic on 2006-04-04
i'm so glad i found this thread.  I had this EXACT same problem on my Breezy NetVista install-- then upgraded to Dapper and still had the same problem.  Then I updated the BIOS and still the same problem.  Then i reinstalled Dapper Flight 6 with noapic and nolapic flags and wala!  no more hanging.  thank you everyone for sharing!!

i'm happy again
:D

---

### Post by ariel on 2006-04-10
[QUOTE=telepathetic]i'm so glad i found this thread.  I had this EXACT same problem on my Breezy NetVista install-- then upgraded to Dapper and still had the same problem.  Then I updated the BIOS and still the same problem.  Then i reinstalled Dapper Flight 6 with noapic and nolapic flags and wala!  no more hanging.  thank you everyone for sharing!!

i'm happy again
:D[/QUOTE]

This sounds good! Can you be a bit more specific: did you overwrite your old install with Dapper F6 and the edited grub/menu.lst and threw in "noapic" and "apic=off" ? or did you some special flags with dapper's installer?
More important: is your machine still running? :-)

Thanks!

---

### Post by bfbay315 on 2006-04-20
You can do either...

in /boot/grub/menu.lst look for this...

```
title      Ubuntu, kernel 2.6.12-10-386
root       (hd0,0)
kernel     /vmlinuz-2.6.12-10-386 root=/dev/mapper/Ubuntu-root ro quiet splash
initrd     /initrd.img-2.6.12-10-386
savedefault
boot
```

and add 


```
title      Ubuntu, kernel 2.6.12-10-386
root       (hd0,0)
kernel     /vmlinuz-2.6.12-10-386 root=/dev/mapper/Ubuntu-root ro quiet splash [COLOR="Red"]nolapic acip=off[/COLOR]
initrd     /initrd.img-2.6.12-10-386
savedefault
boot
```


or when your are installing you can type
```
linux nolapic acip=off
```

This will automatically add those two options in your kernel parameters..That being said I'm sure there's other ways.:rolleyes: .but those should work for you.


Brian

---

### Post by Thruston on 2006-09-26
This problem is still with us (well with me) on my IBM A50 and kernel  2.6.15-27-686 under Dapper 6.06.

Before I start messing with kernel parms can any tell us *exactly* what we are trying to turn off here? acpi? apic? lapic? or all three?

For the acronym-blind out there (and that includes me)
ACPI == Advanced Config and Power Interface
APIC == Advanced Programmable Interrupt Controller
(thank you to the teams at Intel that invented those two)

I think there are three things I could turn off:

 acpi=off  (disables whole ACPI system)
 noapic    (tells kernel not to use the APIC)
 nolapic   (disables "local" APIC even if it is on in BIOS)

Should I set all three?  Shall I experiment and find out?
What on earth does "local" mean in this context?

Do we think that the problem with the A50 is in the ACPI or the APIC?

And while I am at it, is there a neat way to have Grub's menu.lst automatically updated with these parms?  I mean can I put them in a config file somewhere and have some system updating script apply them so that they get applied next time those nice people at Ubuntu release a new kernel.

Thanks, Toby

---

### Post by Thruston on 2006-09-26
Looking back through the thread to

>  Re: Ubuntu hangs/freeze/stalls
This could be the problem..

[http://bugzilla.kernel.org/show_bug.cgi?id=4235](http://bugzilla.kernel.org/show_bug.cgi?id=4235)

There are more info at : [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=284477](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=284477)

... seems to indicate that the problem is in acpi and not in the APIC.

I'm going to try with just acpi=off to begin with.

---

### Post by rushcamera on 2007-01-24
hi
I had the same problem (hangs, freezes, stalls, lockup) on my IBM NetVista under both Ubuntu and Debian. Adding the "noapic nolapic" flags to the end of the "kernel" parameter line in /boot/grub/menu.lst fixed the problem.

This issue is addressed by both the Debian and Ubuntu installers. If you have a Debian 3.1 or Ubuntu 6.06 CD (the Live or the Alternate Install versions), press F1 (for help) when booting. Then press F5 for "Special boot parameters for special machines". The instructions note that "If you experience lockups or other hardware failures, disable buggy APIC interrupt routing", add the "noapic nolapic" boot parameter.

-- your pal, Rush

---

