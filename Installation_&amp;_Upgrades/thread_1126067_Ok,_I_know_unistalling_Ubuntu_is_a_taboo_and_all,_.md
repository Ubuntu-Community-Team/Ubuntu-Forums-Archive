---
title: "Ok, I know unistalling Ubuntu is a taboo and all, but.."
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by Plastic Dinosaur on 2009-04-15
Hello all,

I just got this laptop a few weeks ago, and like an idiot I did the full Ubuntu installation instead of the dual installation. To cut to the chase I want to put vista back on..yeah I know like broken glass to your ears/eyes...but if someone could get past the fact that I want to take Ubuntu off, and put Vista back, and just help me, I'd appreciate it.

Here's the low down.

It's an Acer Aspire 5735-6694

But the recovery discs won't run on ubuntu. It just brings up the .dat files and such. :(

Is there anyway I can do a full system restore, and installing vista? I'm pulling my hair out!

Please..I don't know where else to turn.

- Hayley

---

### Post by Michael.Godawski on 2009-04-15
hi,

have you tried to boot with the Vista disc? and just let Windows override the Ubuntu partitions?

---

### Post by Bakon Jarser on 2009-04-15
You have to boot from the cd.  Make sure that the disk is in the drive when you boot the computer and it should say something about booting from cd while the bios is loading.  If not you may have to change some bios boot order settings to make it check the cd-rom before checking the hard drive.

---

### Post by |Mitch| on 2009-04-15
If your computer is set to boot from the DVD first, then it should give you the option. After that you just follow directions from the Vista disk.

If not, then you will have to enter the bios and change the boot order setting. It should say to hit delete to enter setup, hitting delete or whatever key it says will get you in the bios.

---

### Post by Cope57 on 2009-04-15
If you made the 16 back up CD's, or 6 DVD's as required, then use them.
Just insert disc #1 and reboot, you will be prompted when to insert the next disc.

---

### Post by Plastic Dinosaur on 2009-04-15
For me it was 3 discs actually. And I know they work, because I restored everything to test them.

Anyway..I just tried rebooting with the disc in and it didn't boot from the disc. :(

Is there a way to change the setting for that?

Thanks all of you for your help too. I really appreciate it.

---

### Post by Bakon Jarser on 2009-04-15
Like I said, go into the bios and change the boot options.

---

### Post by Plastic Dinosaur on 2009-04-15
I hate to be such a dunderhead, but I just tried going into the BIOS and editing it, but I still don't know how to make the command. I hit esc to go to the boot menu..or I guess that's the bios. But I don't really know what to do after that. It's Ubuntu 9.04 if that's any consolation.

---

### Post by MaindotC on 2009-04-15
It doesn't have anything to do with Ubuntu - they are talking about a function of your BIOS.  When your machine boots it should say something like "Press F12 for BIOS menu" or "Esc" or mine says the "DEL" key to enter the BIOS.  Once you get into the BIOS, you should look for a setting called "Boot Order".  Make sure the CD/DVD drive is selected to be the first boot device.  Here's a generic guide but the key you have to press my vary depending on what kind of machine you have: [http://www.hiren.info/pages/bios-boot-cdrom](http://www.hiren.info/pages/bios-boot-cdrom)

---

### Post by Plastic Dinosaur on 2009-04-15
Thank you. The problem now being, when it very first starts It says hit <F12> for Setup...I hit that, and it went to the ubuntu start up where it gives me 3 seconds to hit Esc to enter menu, which gives me boot options, but nothing about booting from disc.

I'm about to loose my head. It's making me feel if I ever get this off, I don't know if I want it back if it's this much trouble.

It doesn't respond to F12 at all. I mean I tried holding the key down and everything. Do i have to hold shift down at the same time or something?

---

### Post by benmoran on 2009-04-15
> **Plastic Dinosaur said:**
> 
It doesn't respond to F12 at all. I mean I tried holding the key down and everything. Do i have to hold shift down at the same time or something?

Try repeatedly pressing F12 as soon as you see the message, and keep tapping it. Some computers are like that.

---

### Post by Plastic Dinosaur on 2009-04-15
> **benmoran said:**
> Try repeatedly pressing F12 as soon as you see the message, and keep tapping it. Some computers are like that.

*sigh* Just tried that. No dice. AUGH! Well I'm giving up for tonight. I need to get at least a couple of hours of sleep. I have to get up early for work. I can't be bothered with this anymore tonight/morning.

---

### Post by MaindotC on 2009-04-15
Remove the hard drive and try hitting f12 on boot again.

---

### Post by Plastic Dinosaur on 2009-04-15
Ok, I got to it, but was given an error on the second recovery disc.

Windows cannot find':\Windows\PLaunch.exe'. Make sure you typed the name
correctly, and then try again.

then when windows starts. I get this:

autochk program not found - skipping AUTOCHECK

And it never goes to windows. Should I just put linux back on?

I heard I'd have to reformat the hard drive in order to run windows again. How would i do that?

---

### Post by xbartolo on 2010-07-28
I had the same problem with my Acer. The problem is that when you installed Ubuntu you probably changed the partitions configuration. I mean, you probably removed the previous partition and created a new one not NTFS.
 
To solve it, remove all the partitions and then run the recovery software again. It worked for me.
 
Hope it helps!

---

