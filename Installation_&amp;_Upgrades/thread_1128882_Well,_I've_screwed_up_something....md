---
title: "Well, I've screwed up something..."
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by bogiestl on 2009-04-18
Last week, I bought a "new" computer... A HP P4 with a gig and 40 gigs of HD... Neck, not bad for $96, including XP Pro... 
 
So, this is going to be a business 'puter and a surf stupid stuff 'puter.
 
So I whipped out the CD, and it ran it. So I did an install, splitting into two partitions, so that my girlfriend will still have her windoze apps.
 
And I had the XP configured for some weird-size 16x9 monitor, instead of 1024x768 or 800x600 or somesuch... 
 
(at least I think that's the problem...)
 
Anywho, it seems to boot, and then I get a nice featureless tan screen that then does absolutely nothing. We're talking "dead parrot" nothing. I've tried the old "do things with the keyboard and braille" bit that I've done before with Windoze, etc., to no avail...
 
Now, I really don't wanna chance nuking the XP partition... It's set up for the girlfriend, and she's happy, so... I gotta mess with the Ubuntu side... Loaded the CD, and everything is nice and visible... tried running the install program, and it wants to further split partitions, etc... 
 
Can I install it over the original install? Most of the directions I've found are for "fresh" installs... Or is there a way to edit (like with the DOS/windoze autoexec or sys files) to plug in the right monitor info?

---

### Post by Partyboi2 on 2009-04-18
You can reinstall ubuntu by choosing "manual' at the partitioning stage and ticking the box to format your / partition and making sure that the mount point for it is set to /
Make sure you backup important stuff before working on partitions. 
If you are getting a brown screen when you boot Ubuntu a reinstall will probably produce the same outcome. What graphics card are you using?

---

### Post by bogiestl on 2009-04-18
> **Partyboi2 said:**
> What graphics card are you using?
 
It's whatever crappy thing that's in the box - IIRC (machine is at my shop right now) the thing is built into the mommyboard. The machine is a HP/Compaq, and I can probably figure more out tomorrow... I had the Windoze (XP Pro) configged for a 22" 16x9 monitor (with some moderately strange numbers), and IIRC, the install could copy my windoze settings, and maybe that flaked on me... If I try reinstall, I'd like to switch the windoze to 800x600 before I do it, see if that works.
 
Or maybe buy el-cheapo aftermarket vid card offa da 'bay and stick it in a slot? What would you guys recommend? Monitor for the shop is just an old Dell Sony Trinitron CRT... Windoze side is gonna run Word and Excel and some fax software, Ubuntu side is Firefox and OO... 
 
Booted with CD, and I could see both partitions (and what I can assume are all the files) just fine... Also, not sure what I'm doing with them, but I also tried the various other boot choices that are "standard" with the grub install. I'm new to Unix, but I've been playing with these infernal machines since CP/M, so I'm not shy about whipping out a text editor to change settings...
 
Read something in a different thread, and I'm wondering if I do something like "vga=800" at the end of one of the bootup strings... Do you guys think that'd work? IIRC, the resolution was set for something like 1580x853 or some other strange number....

---

