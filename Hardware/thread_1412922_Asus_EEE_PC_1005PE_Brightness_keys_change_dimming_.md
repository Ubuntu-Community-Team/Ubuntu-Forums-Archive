---
title: "Asus EEE PC 1005PE Brightness keys change dimming randomly"
date: 2010-02-21
forum: Hardware
---

### Post by MilitantPotato on 2010-02-21
I'm using Karmic, non net-book remix.

I've looked around google for the past few hours and found nothing, sorry if I missed a fix.

When changing the brightness via Fn+f5/f6 the brightness changes randomly.  It does the same when moving the slider in gnome power manager.  Is there a fix for this somewhere? 

It makes the dim when idle feature completely useless, since the screen gets brighter.  

Thanks in advance, 
Jason

---

### Post by MilitantPotato on 2010-02-23
First as last bump.  If anyone has any ideas, let me know.

---

### Post by anaconda on 2010-02-23
Have you tried this:
[http://ubuntuforums.org/showthread.php?t=881241](http://ubuntuforums.org/showthread.php?t=881241)

---

### Post by finnk on 2010-02-24
[COLOR=#000000][FONT=Arial]this will make the brightness keys work:
sudo gedit /etc/default/grub

Find the line GRUB_CMDLINE_LINUX_DEFAULT and add "acpi_osi=Linux" so it looks like this GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux". Save the file. Now run update-grub2.

sudo update-grub2

But gnome power manager still randomly changes the backlight. I disabled it from startup, and start it from the command line when i want to suspend on closing the lid.
[/FONT][/COLOR]

---

### Post by anaconda on 2010-02-24
Thanks finnk!
That works in my asus eee 1005P too..

How did you figure that out? I googled for hours without finding a solution.

And I was researching a completely different approach, with using xbacklight and xgamma, which both work too..

---

### Post by MilitantPotato on 2010-02-24
Good stuff Finnk.

Gnome power manager is still sorta screwy, cycles through the brightness levels 3 times, but at least there _some_ order to it.   Thanks a lot! FN keys work perfectly though.

Other than having to manually make a fancontrol file and a network issue leaving standby, ubuntu has been nearly flawless on the EEEPC for me.  Great job all the devs out there.

---

### Post by finnk on 2010-02-24
@anaconda
I got it from this debian wiki:
[http://wiki.debian.org/DebianEeePC/Model/1005pe](http://wiki.debian.org/DebianEeePC/Model/1005pe) 

@MilitantPotato
I haven't thought about the fan control, does it by default run at constant speed? How does your fan control file look like, and where do you put it?

---

### Post by MilitantPotato on 2010-02-24
My fan ran at ~3950 rpm constantly, hovering around 54C.

here's my /etc/fancontrol
/etc/fancontrol:
INTERVAL=2

FCTEMPS=hwmon1/pwm1=hwmon0/temp1_input
FCFANS=hwmon1/pwm1=hwmon1/fan1_input
MINTEMP=hwmon1/pwm1=64
MAXTEMP=hwmon1/pwm1=80
MINSTART=hwmon1/pwm1=10
MINSTOP=hwmon1/pwm1=0

It's not perfect, but it idles with the fan off and saves a noticeable amount of battery.  Kicks up to full speed around 67C.

I had to make the settings myself since pwmconfig didn't detect any fans.

/etc/init.d/fancontrol setup: [http://pastebin.com/CRTBwbfe](http://pastebin.com/CRTBwbfe)
'sudo ln -s /etc/init.d/fancontrol /etc/rc3.d/S99fancontrol' for it to start at boot
'sudo chmod 0755 /etc/init.d/fancontrol' so it executes.

I'm not sure where I got all the scripting for that, found it on google after a few hours of searching.

---

### Post by petaramesh on 2010-03-01
Excellent ! It solved my 1005PE backlight issue as well :-)

---

### Post by ndrbvl on 2010-03-04
@MilitantPotato
You mentioned a network issue leaving standby. I probably have the same problem, but I couldn't find any info to solve it, nor anyone reporting the same issue (so far). In my case, ethernet does not resume correctly. After suspend, the wired network does not work, nor it does the wireless, if I try to turn it on. The ethernet hardware is not recognized any more and it does not show up on a "lshw -C network" command. On the contrary, if I turn the wireless on before suspend, then it is resumed correctly. Did you find any fix to this?

Thanks!

---

### Post by cherva on 2010-03-04
I have a 1005HA, ubuntu 9.10 and the only problem is with the wired network after resuming ... no other problems.

---

### Post by Paolo1959 on 2010-03-04
> **ndrbvl said:**
> @MilitantPotato
You mentioned a network issue leaving standby. I probably have the same problem, but I couldn't find any info to solve it, nor anyone reporting the same issue (so far). In my case, ethernet does not resume correctly. After suspend, the wired network does not work, nor it does the wireless, if I try to turn it on. The ethernet hardware is not recognized any more...

Thanks!

I have the same problem, and could not find a fix for it...

Paolo

---

### Post by MilitantPotato on 2010-03-10
My googling turned up that it's a kernel issue.  I tried modifying the acpi script, to kill and re-start networking, that did nothing. 
Unfortunately suspend and hibernate are completely broken for me now, not sure what I did.

---

### Post by ndrbvl on 2010-03-11
I tried to restart the network service from xterm after suspend, but it does not work. The only "fix" is to reboot. The other day the update manager popped up with a kernel update to version 2.6.31-20 (btw I run Ubuntu Remix 9.10). I hoped that that would fix the suspend issue, but unfortunately nothing changed. On the other hand, there's a new bug with the audio, but it's something I can live with (and it's another story).

---

### Post by dpwegener@gmail.com on 2010-03-31
> **finnk said:**
> [COLOR=#000000][FONT=Arial]this will make the brightness keys work:
sudo gedit /etc/default/grub

Find the line GRUB_CMDLINE_LINUX_DEFAULT and add "acpi_osi=Linux" so it looks like this GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux". Save the file. Now run update-grub2.

sudo update-grub2

But gnome power manager still randomly changes the backlight. I disabled it from startup, and start it from the command line when i want to suspend on closing the lid.
[/FONT][/COLOR]
After making this change, the brightness still wasn't completely consistent and there was never a popup showing the brightness level on the screen.  Adding "acpi_backlight=vendor" to grub solved the problem completely.  Now, the brightness changes as expected and you see the brightness level popup.

My GRUB_CMDLINE_LINUX_DEFAULT line now looks like this:

[COLOR=#000000][FONT=Arial]GRUB_CMDLINE_LINUX_DEFAULT="quiet  acpi_osi=Linux acpi_backlight=vendor splash"[/FONT][/COLOR]

---

### Post by isidoro on 2010-05-03
> **dpwegener@gmail.com said:**
> After making this change, the brightness still wasn't completely consistent and there was never a popup showing the brightness level on the screen.  Adding "acpi_backlight=vendor" to grub solved the problem completely.  Now, the brightness changes as expected and you see the brightness level popup.

My GRUB_CMDLINE_LINUX_DEFAULT line now looks like this:

[COLOR=#000000][FONT=Arial]GRUB_CMDLINE_LINUX_DEFAULT="quiet  acpi_osi=Linux acpi_backlight=vendor splash"[/FONT][/COLOR]
Thanks!! Really solved the problem.

---

### Post by vickoxy on 2010-05-22
I posted some threads but i will try also here. Anyone has fancontrol running under Ubuntu 10.04 and Asus 1005PE? If yes, how?

Thanks

---

### Post by jayantsr on 2010-06-02
Thanks It worked Perfectly

---

### Post by fbicknel on 2010-06-08
With 10.04, I noticed the same screwiness with the brightness.  I upgraded the BIOS to 1103 and it now works perfectly.  Fan seems more reasonable too.

Edit: Should have mentioned that this is 10.04 netbook edition

---

### Post by Autodave on 2010-06-08
> **MilitantPotato said:**
> Good stuff Finnk.

Gnome power manager is still sorta screwy, cycles through the brightness levels 3 times, but at least there _some_ order to it.   Thanks a lot! FN keys work perfectly though.

Other than having to manually make a fancontrol file and a network issue leaving standby, ubuntu has been nearly flawless on the EEEPC for me.  Great job all the devs out there.

Replying to you and all others with Asus netbooks and even notebooks........you might want to look into EEEBUNTU.  This was put together for Asus netbooks since there was so much trouble configuring everything like wi-fi, sound, function keys, etc.  Custom kernel that just seems to work on Asus machines with extremely little if any configuring.  On my 900 netbook, everything worked perfectly right from the install except for my sound which required moving the sliders to the proper position which took almost 30 seconds to figure out.  The EEEBUNTU uses Ubuntu 9.04.

---

### Post by jiaolu on 2010-06-16
> **dpwegener@gmail.com said:**
> After making this change, the brightness still wasn't completely consistent and there was never a popup showing the brightness level on the screen.  Adding "acpi_backlight=vendor" to grub solved the problem completely.  Now, the brightness changes as expected and you see the brightness level popup.

My GRUB_CMDLINE_LINUX_DEFAULT line now looks like this:

[COLOR=#000000][FONT=Arial]GRUB_CMDLINE_LINUX_DEFAULT="quiet  acpi_osi=Linux acpi_backlight=vendor splash"[/FONT][/COLOR]

Great,Solve my problem too. Thanks

---

### Post by drkages on 2010-07-13
> **dpwegener@gmail.com said:**
> After making this change, the brightness still wasn't completely consistent and there was never a popup showing the brightness level on the screen.  Adding "acpi_backlight=vendor" to grub solved the problem completely.  Now, the brightness changes as expected and you see the brightness level popup.

My GRUB_CMDLINE_LINUX_DEFAULT line now looks like this:

[COLOR=#000000][FONT=Arial]GRUB_CMDLINE_LINUX_DEFAULT="quiet  acpi_osi=Linux acpi_backlight=vendor splash"[/FONT][/COLOR]

Has anyone found a way to add this permanently to grub rather than adding every time the notebook starts
?

---

### Post by fbicknel on 2010-07-19
I'm curious to know if anyone else tried upgrading the BIOS to fix this problem.  (See my previous post.)

It's possible that this will only work with 10.04.  I haven't had any problems out of 10.04, so I can recommend both upgrades, especially together.

---

### Post by whit on 2010-07-24
> **drkages said:**
> Has anyone found a way to add this permanently to grub rather than adding every time the notebook starts
?

Add it to /etc/default/grub, then "update-grub".

---

### Post by utopi on 2010-11-20
> **finnk said:**
> [COLOR=#000000][FONT=Arial]this will make the brightness keys work:
sudo gedit /etc/default/grub

Find the line GRUB_CMDLINE_LINUX_DEFAULT and add "acpi_osi=Linux" so it looks like this GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux". Save the file. Now run update-grub2.

sudo update-grub2

But gnome power manager still randomly changes the backlight. I disabled it from startup, and start it from the command line when i want to suspend on closing the lid.
[/FONT][/COLOR]


Thank you :KS:KS:KS:KS:KS

---

### Post by NeoTheFox on 2011-01-12
> **fbicknel said:**
> I'm curious to know if anyone else tried upgrading the BIOS to fix this problem.  (See my previous post.)

It's possible that this will only work with 10.04.  I haven't had any problems out of 10.04, so I can recommend both upgrades, especially together.

Hi everyone! I'ne got 900AX, and the same problem
I tryed both BIOS upgrade and grub configuration - none work for me(

---

### Post by egay on 2011-01-13
Hello finnk :D

I am new and an novice in Linux/Ubuntu, having just migrated my desktop & 2 laptops from Win OS; having done so made me experience some difficult (for me) issues and one of that is this BRIGHTNESS thing.

Thank you very much for your excellent solution!

I'm starting to believe that Linux-people are geniuses:cool: - for how else can an ordinary mortal figure this things out?:confused:

May your tribe multiply!

regards from Manila,
egay
):P
**.e.**

PS: I am going to post this solution in my BLOG at http;//ezdapiton.wordpress.com/ 

 
> **finnk said:**
> [COLOR=#000000][FONT=Arial]this will make the brightness keys work:
sudo gedit /etc/default/grub

Find the line GRUB_CMDLINE_LINUX_DEFAULT and add "acpi_osi=Linux" so it looks like this GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux". Save the file. Now run update-grub2.

sudo update-grub2

But gnome power manager still randomly changes the backlight. I disabled it from startup, and start it from the command line when i want to suspend on closing the lid.
[/FONT][/COLOR]

---

