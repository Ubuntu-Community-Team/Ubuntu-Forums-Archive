---
title: "Trident Cyberblade XP tv out problem"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by Jonked on 2007-08-27
I have an old laptap (Toshiba Satellite Pro 4600) running Xubuntu. Video etc all works fine except for the TV-out function. As I really want to use this laptop as a media player connected to my TV this is a pain to say the least. Video card is Trident Cyberblade XP and currently the 'trident' driver is installed.

The Geexbox distribution plays fine with the TV out, so I know it's possible. Unfortunately Geexbox won't recognise my wireless card... and anyway I'd really like to get it working in Xubuntu.

Any ideas?

---

### Post by zero_dgz on 2007-08-27
I hate to post "me too," but, uh... Me too. I actually just joined the forums to complain about this, and here it is, first thread on the page.

I've got a Toshiba Satellite 1805-S204 (corrected) which is pretty old dusty but otherwise runs just fine. I switched to Kubuntu from Gentoo after I hosed my Gentoo install for the last bloody time with an innocent emerge --update. It's (Kubuntu) been good to me so far. But my TV out doesn't work, as described above.

The machine has a Trident Cyberblade XP video adapter in it. When I try to switch to TV out (fn + F5) it switches on the hardware level (e.g. my laptop's screen goes blank) but the image on the TV is totally garbled, consisting of a maelstrom of white and light grey horizontal bars all flickering back and forth, looking rather like an old monitor that's given a signal out of its refresh range.

I tried noodling with the refresh rates in KDE, but had no luck. In most resolutions I only have the choice of 60hz, though in 832x624 (??) I also have the choice of 75hz. The machine's hardware resolution is 1024x768, which is what I usually left it on for TV out in the past. I tried in all of the other available resolutions: 640x480, 800x600, and that funky 832x624 in both refresh rates. No dice.

The interesting thing is that if I switch to TV out on bootup it *works* up until KDE loads. I can watch my bootup messages go by in text mode, and the blue "Kubuntu" graphical logo with progress bar is visible as well. As soon as KDE starts, whammo! Snowstorm of dancing bars.

I wonder if this is either a KDE issue or, more likely, something to do with the default driver that K/Ubuntu is using for X in general. My video card is identified in KDE only as 'trident' (which is the driver I used in Gentoo and everything worked). My monitor is just a 'Plug 'n' Play,' and otherwise seems to work normally. Paging through the list of manufacturers and specifications I was unable to find an entry for "actually works with TV out," so that avenue seems to be out.

(I kid, I kid.)

Is there maybe an alternate driver that'll work with these Trident cards? That's about the only thing I can think of.

---

### Post by zero_dgz on 2007-08-27
Additional fiddling:

I tried a couple of more 'generic' video drivers (framebuffer, VESA, et. all) and had no success. VESA provides *no* video under the Cyberblade, even in more reasonable resolutions (640x480) at any refresh rate or color depth. After messing with that I had to boot to recovery mode and change my xorg.conf's instances of 'vesa' back to 'trident' to get my display to work at all, after which it became stuck in 640x480 and I had to go through the conf again to get it going at 1024x768 again.

So far, no luck getting TV out to work.

---

### Post by CookieNinja on 2007-08-29
I don't have time to try this, on my toshiba 4600, but this might help someone who has the time.

Boot up with geexbox and then make a copy of the xorg config and save it somewhere. Then boot up with ubuntu and use the xorg config from geexbox to work out what you need to do to make tvout work on ubuntu as well.

That's not exactly a how-to, but it should go a long way towards helping to solve the problem.

I'm going to give it a go when I get the chance.

---

### Post by maj81 on 2007-10-09
I have the exact same problem with the same video card. there is no way to run it on 1024*768 or 800*600 you will only get very scrambled picture. 

I have tried to press F4 when booting and boot to the save VGA mode and I choosed 640*480 16bit, (by the way as you said if you switch to TV during the booting every thing will looks great on the TV but it will scramble again when it first load X) then here we go I have it there, the picture is clear but not perfectlly allign. I have tried to go for 1024*768 or 800*600 from there but there was a distourtion but less than with out safe VGA mode.

I'm Linux n00b but I think the problem that by pressing Fn+F4 we are using the hardware version of TV-out which is very limited. but we need to do it from software side. but I can't figure out what files to start play with but it seems like some thing just behind the corner.

---

### Post by maj81 on 2007-10-09
This is a tutorial to edit the xorg.conf file, which I believe the place to solve this issue.
[http://www.linux.com/feature/118108](http://www.linux.com/feature/118108)

I hope some one can try it out because I'm n00b :( but I'll do what I can.

---

### Post by nitestick on 2007-10-29
just decided to drop by to say "me too" as well. i desperately want to use this notebook (satellite pro 4600) as a mediabook but this is causing problems.

---

### Post by samborambo on 2007-11-08
This may help:

[http://forums.gentoo.org/viewtopic-p-4461887.html]("http://forums.gentoo.org/viewtopic-p-4461887.html")

make a backup of /etc/X11/xorg.conf and try the one on that page.

Particularly, you are changing:

```

Option     "CyberStretch" "True"
Option     "Display"    "Dual"
Option     "TVChipset"  "VT1621"   #  Options  are  CH7005  or  VT1621
Option     "TVSignal"   "1"               # "0" for NTSC, "1" for PAL
Driver      "trident"

```
in the device section.

type```
 man trident
``` to see a list of other options for this driver also.

Please post if you're successsful and hardware details.

Sam

---

### Post by Jonked on 2008-01-13
An update - still haven't got this working, but found a solution for the laptop if not for Xubuntu. The Zenwalk distro works both with the wireless and TV out on the Satellite Pro 4600 and also performs a touch faster than Xubuntu. The live CD of Antix also works.

I guess I could try copying the xorg.conf from Zenwalk but am happy with sticking with a working system for now.

---

### Post by brazso on 2008-01-17
Jonked, could you post here (or better to send me) the xorg.conf file used by Zenwalk? Thanks, Brazso

---

### Post by nitestick on 2008-02-03
cheers for the extra info and research. i'll give this zenwalk a try, break it down and see if i can't find what makes it work. i've been using Debian on the laptop for a while now (after Ubuntu kept borking my wifi, no idea why) and i really can't live without a Debian based distribution :p so i'd like to solve this.......well i could live without Debian, if you call that living.

---

### Post by anticapitalista on 2008-02-04
antiX is debian based.

---

### Post by nitestick on 2008-02-04
cheers for that :D i might check that out then. i did look at Zenwalk's site but never got to antix. i haven't downloaded Zenwalk yet (dialup). i'd much rather find the solution to the problem because you never know if you might run into it again.

i think the problem obviously lies in the Xserver. at the moment i can't be bothered going with a compile from source as theres probably a good chance i'd just miss a necessary switch anyway. so i'm now leaning towards looking at antiX's specific setup. theres a good chance we could just borrow the server from antiX.

---

### Post by anticapitalista on 2008-02-04
Maybe jonked could post the xorg.conf file from antiX when it worked for him/her.

---

### Post by Mike_T on 2008-03-20
I found a solution which worked for me:
Notebook Toshiba Satellite Pro 4600 with onboard Trident CyberbladeXP graphic adapter
Ubuntu Linux 7.10 "Gutsy"

Nothing concerning driver, xorg.conf etc. worked for a correct TVout. But I saw only snow, coloured snow, or a crashing XServer.

Then I found this thread (German): [http://forum.ubuntuusers.de/topic/124671/](http://forum.ubuntuusers.de/topic/124671/)

Thanks to bchristopeit and cmon1701 I did the following:

1. sudo nano /etc/initramfs-tools/modules
and add

fbcon
vesafb
tridentfb

2. sudo update-initramfs -u

3. sudo nano /etc/modprobe.d/blacklist-framebuffer

in lines vesafb and tridentfb set a # at the beginning

4. Reboot

And...
TVout works

---

### Post by niels_l on 2008-03-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/35794](https://bugs.launchpad.net/bugs/35794) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-driver-trident/+question/27214](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-driver-trident/+question/27214) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This solved it for me

there is a little bit of offset to the left, and the bottom panel isn't visible

my first instinct is to start editing the xorg.conf monitor settings

But this looks like its is for computer monitors not for tv

---

