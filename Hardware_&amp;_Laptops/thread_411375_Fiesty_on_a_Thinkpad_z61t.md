---
title: "Fiesty on a Thinkpad z61t"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by ghetto2ivy on 2007-04-16
Running Feisty on a brand new Thinkpad z61t.  He're the good, the bad, and the ugly

**Good:**
Lenovo wireless card (atheros) works fine after install (though disconnects bout every 2 hours)
WXGA+ screen worked flawlessly
Intel GMA 950 Works great (But haven't gotten it to output & display simul or xinemera successfully)
Most Think pad buttons work  (volume, power, suspend, hibernate, screen dim/brighten)
sound output works
Hardware is sweet (Awesome keyboard)
Suspend/Resume work great (really surprising! SATA hard drive set to compatibility mode in bios)
Battery life is about 4h 15 minutes from the 7 cell battery. (within 15 mins of windows).
Beryl runs great. Better than on my much more powerful desktop (running edgy)

**Bad:**
Some think pad buttons do diddly... have not gotten back forward buttons working
The internal card reader works like 10% of the time (Please fix!)
Built in Web cam is not working (no surprise, but would be nice)
Haven't gotten stereo mic to work either.
Must enable bluetooth in windows first (lenovo's fault)
Can't get bluetooth sync working with treo 650 yet (feels like i'm close...but most instructions are dated)
Annoying need to unlock keyring to get onto my default wireless network (yes I tried pam to no avail, worked for 2 days then mysteriously stopped)

**The Ugly:**
Problem No. 1:
Something is slowing my system to a crawl about 2 hours into usage. Everything becomes non-responsive in about 45 seconds and the hard drive churns away. I thought it was beagle, but even after removing beagle it continues. 

Problem No. 2:
Similar and probably related to #1, after some time of inactivity the screen goes blank (not suspend) and does not ever resume from it. I actually have to power cycle (what is this windows?) Again, the hard drive is usually churning when this happens.
[B]
Not tested:[/B]
firewire, pccard, sound jacks up front, biometric scanner (havent bothered with bioapi yet).

Any help getting this system running flawless would be greatly appreciated.

---

### Post by raja on 2007-04-16
I have Ubuntu running on my thinkpad X40 for more than a year now and am running Feisty now. Thinkpad seems almost to be made for Linux! Couple of suggestions - 
1. The forward and back keys dont do anything by default. But I have mapped them to rotate the desktop cube right or left (instead of Ctrl-Alt-left, etc). That make is really comfortable navigating your workspaces. 
2. When your system starts crawling, check with top to see what is causing the load.

---

### Post by ghetto2ivy on 2007-04-17
Thanks for the post. I think I got the problem licked -- I think Its a beagle bug. I found it was still running and even though I had tried removing it (its linked to the ubuntu-desktop now). So instead I've uesd BUM (Boot up manager to disable it from running at start up.)

So 1/2 day and so far so good.

Gotta work on xmod map -- mapping the forward back buttons to the cubes sounds really useful.

---

### Post by kapputu on 2007-04-20
Well, I have a Z61t too but it was nowhere near as flawless.

1. Wireless card (Atheros) was detected out of the box but wouldn't connect to any wireless network. I've been using another card since then.

2. If I hibernate and turn it on again, it doesn't reconnect to the network and resets the time to GMT.

---

### Post by steve k on 2007-04-20
> **raja said:**
> I have Ubuntu running on my thinkpad X40 for more than a year now and am running Feisty now. Thinkpad seems almost to be made for Linux! Couple of suggestions - 
1. The forward and back keys dont do anything by default. But I have mapped them to rotate the desktop cube right or left (instead of Ctrl-Alt-left, etc). That make is really comfortable navigating your workspaces. 
2. When your system starts crawling, check with top to see what is causing the load.


Hey,

I'm also an X40 user, I've been using Ubuntu since forever ago, like Breezy i think, i dunno, that' snot really that long ago really.  But anyway, Suspend/Resume are broken now that I've updated to Feisty.  I've been muckng around with different things: the gconf, various changes to the /etc/default/acpi-support various other things.  Is your computer suspending normally?  Mine's taking an awfully long time, also, it refuses to come back from being suspended.  If yours is working normally could you PM me with copies of some of your config files for me to look over?

---

### Post by raja on 2007-04-21
Hi steve,
I have been having just a little bit of trouble with suspend in Feisty compared to Edgy. But the problem is only that the lid close event doesnt seem to get picked up about once in 5-10 times. Otherwise suspend and resume work perfectly. I have not changed any of the acpi configuration files from the default installation. I had upgraded from edgy into Feisty alpha, but did a clean install of Fiesty beta.

---

### Post by rrwo on 2007-04-21
You can use Fn-F5 to enable/disable bluetooth. At least that's what I do on my ThinkPad Z60m.

---

### Post by moixa on 2007-04-21
Feisty is nearly flawless on my T60
except that the battery drain seems kind of high, being 19w the lowest I can go.
I accidentally had a 16w drain before, but I don't know how I got that, and it never appera again ever

This post may help some of you
[http://ubuntuforums.org/showthread.php?t=416148](http://ubuntuforums.org/showthread.php?t=416148)

---

### Post by cprsize on 2007-04-21
I've got  a z60t and having some similar problems:

- suspend works, but resume doesn't; this seems to be a known issue on a lot of machines
- hibernate stalls (using Feisty's built-in or suspend2) right after X stops
- madwifi-ng + gnome net manager "low signal quality" issue

I upgraded to Feisty b/c I needed power management support for my ultra-bay battery -- I was tired of Edgy hibernating when the extra battery got low, even though main battery was at 100%.

Any tips?

thx,
--dwf

---

### Post by raja on 2007-04-21
> **cprsize said:**
> I was tired of Edgy hibernating when the extra battery got low, even though main battery was at 100%.

Any tips?

thx,
--dwf

I dont have any experience with the extra battery, but why dont you go to system>preferences>power and set it to 'do nothing' when battery is critically low? Then atleast you wont have the problem of it hibernating when you dont want it to.

---

### Post by cprsize on 2007-04-22
Sorry.  I meant tips with Feisty and hibernate not finishing.

The issue with Edgy was a known bug in the gnome power manager which is fixed in Feisty.  But now hibernate isn't working.

--dwf

---

### Post by hsjC on 2007-04-22
Did you try and get active protection to work?

---

### Post by raja on 2007-04-22
There is a driver to read the motion sensor in linux. But noone has implemented a way to read it and park the hard drive. Atleast as far as I know.

---

### Post by ghetto2ivy on 2007-04-29
I'm going to give thinkfinger a try next. the hard drive stuff I'm less into since I'm usaully wireless and on a desktop.

---

### Post by steve k on 2007-05-27
hey guys,

so i solved my suspend/resume problems by just typing ```
sudo laptop_mode start 
``` into a terminal and then resetting the what to do when the lid closes dialogues that appear when you click on the power management icon.  However, i do have to re-load laptop_mode every time i reboot the computer.   Any ideas?  How can i make that permanent?

also:

> **raja said:**
> 
1. The forward and back keys dont do anything by default. But I have mapped them to rotate the desktop cube right or left (instead of Ctrl-Alt-left, etc). That make is really comfortable navigating your workspaces. 


how did you do that?  that sounds awesome.  I'd love to have those buttons do something.  what are they even called? do i need to update my keyboard layout?

---

### Post by niclane on 2007-06-10
[QUOTE=ghetto2ivy;2465388]Running Feisty on a brand new Thinkpad z61t.  He're the good, the bad, and the ugly

**Good:**
Beryl runs great. Better than on my much more powerful desktop (running edgy)

Hey how did you get Beryl to work? I have a x60s and beryl keeps coming up with that missing
windows decorator problem I have heard about. I haven't found a solution as of yet.

Any thoughts?

Cheers,

Nicholas

---

### Post by moixa on 2007-06-15
> **raja said:**
> There is a driver to read the motion sensor in linux. But noone has implemented a way to read it and park the hard drive. Atleast as far as I know.

there is a patch available for handling this

here is the patched kernel:
[http://axiomatization.googlepages.com/ubuntufeistydebpackagesforthinkpads](http://axiomatization.googlepages.com/ubuntufeistydebpackagesforthinkpads)

---

