---
title: "no boot at all (even live-cd fails)"
date: 2012-06-22
forum: Hardware
---

### Post by U202E on 2012-06-22
**the story:**
because my ubuntu-partition got a bit... sort of damaged yesterday I copied my /home and /usr to another partition (because I wanted to reinstall ubuntu-precise).
when it was finished I opened a site with firefox, and my laptop got slower and slower and totally stuck, so I just shut it down and when I turned it on again it kept rebooting, (sounds like a typical win-XP problem) I then tried to boot up several live cd's but they all just gave a black screen. (with a small cursor blinking)
the only thing I can start up it the bios-setup. :cry:
**the problem:**
I can't fix my laptop if it doesn't boot up **at all**. (whether I'm booting the hdd or live-cd)
*edit* And the HDD was in excellent condition yesterday.
if it's not GRUB2 (live-cd doesn't work to) then[COLOR=Red] it must be the hardware[/COLOR] let me down, but which part is it?
*edit* ^no, I don't mean the cd doesn't continue booting, it doesn't start **at all**!
**some information about my laptop:**
Packard-bell easynote 2GB ram (probably DDR2); 160GB hdd; CPU=intel-dual-core (I like AMD more); Intel GPU;
some phoenix bios that doesn't allow any kind of overclocking;
according to win7 speed check the graphics performance is not so good, and the overall performance is below average.
and according to the **ubuntu harddisk check** the hdd is **in excellent condition**.

sda1=emty ext4 partition with a backup of /home and /usr.
sda2=system reserved (for windows)
sda3=the ******* windows7 ultimate (it was pre-installed)
sda4=extended partition
sda5=ext2 partition inside the extended containing ubu-12.04 and grub2

I tried to boot the hdd; ubuntu-secured remix 12.04 (both x64 and x86); ubuntu-hardy-heron (x64); all those cd's work just fine on other pc's;
**help:**
what's happened? what can I do? what needs to be replaced/reset/checked/tweaked?
while typing this I am using my older x86 Packard-Bell-laptop, with ubuntu12.04.
(English it not my native language, but I understand it pretty well)

---

### Post by jskinner1724 on 2012-06-22
Hi, sounds like a hard drive problem to me. If the live cd starts but does not continue to load the environment, usually there's no place for it to load. I would suggest trying another known-good drive and repeat your live cd boot. I'm dealing with the same issue with a damaged drive.

If you have another system that you can attach the drive to, run diagnostics on the drive. Good luck

---

### Post by U202E on 2012-06-22
are you sure?
yesterday the hdd was in **excellent condition**!
I** didn't** say the live-cd starts and then has a problem, the live cd doesn't load** at all**, **not **even a menu to chose a language.
so that's kindda impossible.

**thanks** for your reply, but no it's not the hard drive.
that's why I asked it here, because I can't really find a solution with google, they all say reinstall win-XP (which is totally not my problem)
and the live cd's don't use the HDD, right, that's why they call it  a **live**-cd.

if there is no place for the cd to load maybe it's the memory, however It's strange if both memory cards failed.

---

### Post by QIII on 2012-06-22
A hard disk check yesterday does not mean a good disk today.  There are many modes of failure.  But that likely has nothing to do with it anyway, since a live disk fulfills the role of the hard drive.

My first guess is memory.  Try reseating the modules.  If that doesn't work, try taking one module out and see what happens.  Try the other module.

Remember that one of the memory slots is likely the primary, so whichever module is in will have to fill that slot.

Give that a try since it is easy and we'll move on from there.

---

### Post by ahallubuntu on 2012-06-22
> **U202E said:**
> are you sure?
yesterday the hdd was in **excellent condition**!
I** didn't** say the live-cd starts and then has a problem, the live cd doesn't load** at al**l, **not **even a menu showing a language.
so that's kindda impossible

Every hard drive that fails was in "excellent condition" the day before it started to fail.

Unplug/remove your hard drive completely and try booting a live CD.  If it boots, you know the hard drive had something to do with it.   If it doesn't boot, then the hard drive has nothing to do with it.  Easy to try.

You may have some other hardware issue like RAM or motherboard.  Rule out the easy stuff first.  If it is not your hard drive, try removing and re-seating the RAM.  If you have two sticks of RAM, try installing one at a time and try to boot the live CD.

---

### Post by Dragonbite on 2012-06-22
> **U202E said:**
> **the story:**
because my ubuntu-partition got a bit... sort of damaged yesterday I copied my /home and /usr to another partition (because I wanted to reinstall ubuntu-precise).
when it was finished I opened a site with firefox, and my laptop got slower and slower and totally stuck, so I just shut it down and when I turned it on again it kept rebooting, (sounds like a typical win-XP problem) I then tried to boot up several live cd's but they all just gave a black screen. (with a small cursor blinking)
the only thing I can start up it the bios-setup. :cry:
**the problem:**
I can't fix my laptop if it doesn't boot up **at all**. (whether I'm booting the hdd or live-cd)
*edit* And the HDD was in excellent condition yesterday.
if it's not GRUB2 (live-cd doesn't work to) then[COLOR=Red] it must be the hardware[/COLOR] let me down, but which part is it?
*edit* ^no, I don't mean the cd doesn't continue booting, it doesn't start **at all**!
**some information about my laptop:**
Packard-bell easynote 2GB ram (probably DDR2); 160GB hdd; CPU=intel-dual-core (I like AMD more); Intel GPU;
some phoenix bios that doesn't allow any kind of overclocking;
according to win7 speed check the graphics performance is not so good, and the overall performance is below average.
and according to the **ubuntu harddisk check** the hdd is **in excellent condition**.

sda1=emty ext4 partition with a backup of /home and /usr.
sda2=system reserved (for windows)
sda3=the ******* windows7 ultimate (it was pre-installed)
sda4=extended partition
sda5=ext2 partition inside the extended containing ubu-12.04 and grub2

I tried to boot the hdd; ubuntu-secured remix 12.04 (both x64 and x86); ubuntu-hardy-heron (x64); all those cd's work just fine on other pc's;
**help:**
what's happened? what can I do? what needs to be replaced/reset/checked/tweaked?
while typing this I am using my older x86 Packard-Bell-laptop, with ubuntu12.04.
(English it not my native language, but I understand it pretty well)

Have you tried disconnecting everything (all USB, etc.) except the monitor, keyboard and mouse and booting up to an pre-12.04 LiveCD?  Can also try disconnecting the hard drive and see if your system will boot up (and that the HD is not preventing the system from doing so?

Checked that everything is seated right, and dust isn't killing your system?

Check the clock in your BIOS?  (Just thinking of the CMOS battery)

Are you hearing the disk drive spin up?

---

### Post by U202E on 2012-06-22
^^yeah nice idea, this bios can't change the clock-speed, so that should be fine.
disconnecting would be a lot easier if it's a normal desk-PC,  but I'll definitely try this out.
if I disconnect the monitor (that does work), I can't see whether it's booting, and it has no system-beep.

I don't normally hear/notice the HDD, was always quiet but I can hear the fan and I hear the cd-spinning. 
the bios-settings look good, just like they were before.

@[ahallubuntu]("http://ubuntuforums.org/member.php?u=32392"), do HDD's crash because you visit a web page??? hmm...   it's not realistic.

---

### Post by Dragonbite on 2012-06-22
> **U202E said:**
> ^^yeah nice idea, this bios can't change the clock-speed, so that should be fine.

I meant, is it holding the correct time?  If not, then maybe the CMOS battery is dying or not seated.

---

### Post by QIII on 2012-06-22
Don't think that the drive would crash because you visited a website.  That assumption is called Post Hoc Ergo Propter Hoc (after this, therefore because of this) and assumes causality between the two.  Simple coincidence is more likely.  

Again, hard drive failure is not on the top of the list of possible problems at this point.

---

### Post by |{urse on 2012-06-22
A couple things.

1. Take it down to one stick of ram.
2. Reset bios to defaults (check to see if the time is correct while in the bios. reset cmos or replace cmos battery if necessary)
3. Download and burn a new .iso (do the md5 just to be certain).
4. Try it again.

I want to say bad stick of ram or corrupted image/scratched disk, worst case scenario bad cd drive or controller on the motherboard.

---

