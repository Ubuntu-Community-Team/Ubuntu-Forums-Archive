---
title: "Live cd 8.10. Stops loading ..."
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by kuabba82 on 2009-01-22
Hello to all. I'm italian, so sorry if my English is not very well. I decided to try the live cd of 8.10, but first I tried it with VirtualBox, but since I have only 512MB of RAM was too slow to load, but started.

So I decided to start it normally, and after selecting the language I click on the first option. It starts loading with the orange bar that goes back and forth for a couple of minutes, then starts to load fixed.
Here it blocks loading...it loads up to 3 squares and then the light of the CD player turns off.

I tried to wait more than 5 minutes, but it is always off. I also tried the recorder, the same thing. I also tried in safe graphics mode, the same, and made the search for errors on the cd without finding anything obviously (because with virtualbox it starts, slow, but it starts).
Then there I discovered that if I press a CTRL + ALT + DELETE buttons, the bar continues loading, but then it hangs back to 1 square from the end.

And if I try the same combination of keys, the cd is ejected and I can not continue.

May depend on what?

---

### Post by kuabba82 on 2009-01-22
Up!

---

### Post by gcracker on 2009-01-22
Did you start installing from a burned ISO or from an offical Ubuntu disc?

Sometimes burned ISOs are corrupt and sometimes the download itself is no good.

Can you verify the integrity of the file?

---

### Post by 67GTA on 2009-01-22
Try holding down any key on your keyboard. I had to do this on my laptop to get it to boot. Once I done that, the progress bar would continue. It turned out to be a buggy DSDT file.

---

### Post by gukid on 2009-01-22
My computer does the same thing with live cds since 8.10 (it's worse if you install it...).

Check out the thread here:
[http://ubuntuforums.org/showthread.php?p=6593988#post6593988](http://ubuntuforums.org/showthread.php?p=6593988#post6593988)

What kind of pc are you using? Do you know any of the hardware specs, like perhaps if it has Intel based onboard graphics?

Try an 8.04 Live cd and see what happens.

---

### Post by kuabba82 on 2009-01-23
> **gcracker said:**
> Did you start installing from a burned ISO or from an offical Ubuntu disc?

Sometimes burned ISOs are corrupt and sometimes the download itself is no good.

Can you verify the integrity of the file?

From a burned ISO, but I verified the integrity (MD5 and used the function integrated in the cd itself) but no errors.

> **67GTA said:**
> Try holding down any key on your keyboard. I had to do this on my laptop to get it to boot. Once I done that, the progress bar would continue. It turned out to be a buggy DSDT file.

When I have to do this? Any key is good?

> **gukid said:**
> My computer does the same thing with live cds since 8.10 (it's worse if you install it...).

Check out the thread here:
[http://ubuntuforums.org/showthread.php?p=6593988#post6593988](http://ubuntuforums.org/showthread.php?p=6593988#post6593988)

What kind of pc are you using? Do you know any of the hardware specs, like perhaps if it has Intel based onboard graphics?

Try an 8.04 Live cd and see what happens.

Well, I don't want to try 8.04 because I want to use the function USB creator integrated in 8.10 to install Ubuntu on an external USB hard disk.
My pc was bought in 2003, I have an ASUS P4S8X-X motherboard with no onboard graphics. But I don't understand why 8.04 should work if 8.10 is newer than it...I think everything works on previous version must works in newest ones...

---

### Post by linux_tech on 2009-01-23
What are the system specs?

From terminal pls post output of:
```
lshw
```

Have you tried the alternate cd?

---

### Post by kuabba82 on 2009-01-23
> **linux_tech said:**
> What are the system specs?

From terminal pls post output of:
```
lshw
```

Have you tried the alternate cd?

Ehm...I don't have ubuntu installed, I'm trying to start live cd, how can I have access to terminal?

---

### Post by 67GTA on 2009-01-23
> Originally Posted by **67GTA** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=6599113#post6599113") 				
 				[I]Try holding down any key on your keyboard. I had to do this on my laptop to get it to boot. Once I done that, the progress bar would continue. It turned out to be a buggy DSDT file.

[/I]
 			 		 	 	 When I have to do this? Any key is good?

In my case it was any key. I would hold down a key when the progress bar started loading. I could actually let go of the key and the bar would stop until I held a key back down.

---

### Post by Therion on 2009-01-23
> **67GTA said:**
> In my case it was any key. I would hold down a key when the progress bar started loading. I could actually let go of the key and the bar would stop until I held a key back down.
LOL!  Seriously?

That's one of the crazier things I've heard...

---

### Post by 67GTA on 2009-01-23
No kidding. It was because of a buggy BIOS DSDT file. I had to manually edit the DSDT to make it stop. This HP laptop came preinstalled with Vista. It seems that Microsoft has their own version of the AML compiler to build the DSDT. They won't use the standard one built by Intel/HP. This started with Vista machines. I guess they are in the BIOS manufactuerers pockets now ](*,) I wrote a how to here: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

### Post by Therion on 2009-01-23
> **67GTA said:**
> ... I had to manually edit the DSDT to make it stop. This HP laptop came preinstalled with Vista. It seems that Microsoft has their own version of the AML compiler to build the DSDT. They won't use the standard one built by Intel/HP. 

Thanks for the info, but...  Suddenly I'm not laughing any more.

---

### Post by 67GTA on 2009-01-23
You can look in your dmesg output and see what your BIOS DSDT was compiled with. Look for this:

[    0.000000] ACPI: RSDP 000FE020, 0024 (r2 TOSINV)
[    0.000000] ACPI: XSDT B7CFE120, 0064 (r1 TOSINV TOSINV00        1       1000013)
[    0.000000] ACPI: FACP B7CFD000, 00F4 (r4 TOSINV TOSINV00        1 MSFT  1000013)
[    0.000000] ACPI: DSDT B7CF1000, 763F (r1 TOSINV TOSINV00        1 MSFT  1000013)
[    0.000000] ACPI: FACS B7C93000, 0040
[    0.000000] ACPI: HPET B7CFC000, 0038 (r1 TOSINV TOSINV00        1 MSFT  1000013)
[    0.000000] ACPI: APIC B7CFB000, 006C (r2 TOSINV TOSINV00        1 MSFT  1000013)
[    0.000000] ACPI: MCFG B7CFA000, 003C (r1 TOSINV TOSINV00        1 MSFT  1000013)
[    0.000000] ACPI: ASF! B7CF9000, 00A5 (r32 TOSINV TOSINV00        1 MSFT  1000013)
[    0.000000] ACPI: SLIC B7CF0000, 0176 (r1 TOSINV TOSINV00        1 MSFT  1000013)
[    0.000000] ACPI: BOOT B7CEF000, 0028 (r1 TOSINV TOSINV00        1 MSFT  1000013)

The [COLOR=Red]"MSFT"[COLOR=Black] means it was made with the Microsoft compiler. [/COLOR][/COLOR]:D

---

### Post by kuabba82 on 2009-01-24
> **67GTA said:**
> In my case it was any key. I would hold down a key when the progress bar started loading. I could actually let go of the key and the bar would stop until I held a key back down.

Thanks, I've tried but nothing happened to me...

> **67GTA said:**
> You can look in your dmesg output and see what your BIOS DSDT was compiled with. Look for this:

[    0.000000] ACPI: RSDP 000FE020, 0024 (r2 TOSINV)
[    0.000000] ACPI: XSDT B7CFE120, 0064 (r1 TOSINV TOSINV00        1       1000013)
[    0.000000] ACPI: FACP B7CFD000, 00F4 (r4 TOSINV TOSINV00        1 MSFT  1000013)
[    0.000000] ACPI: DSDT B7CF1000, 763F (r1 TOSINV TOSINV00        1 MSFT  1000013)
[    0.000000] ACPI: FACS B7C93000, 0040
[    0.000000] ACPI: HPET B7CFC000, 0038 (r1 TOSINV TOSINV00        1 MSFT  1000013)
[    0.000000] ACPI: APIC B7CFB000, 006C (r2 TOSINV TOSINV00        1 MSFT  1000013)
[    0.000000] ACPI: MCFG B7CFA000, 003C (r1 TOSINV TOSINV00        1 MSFT  1000013)
[    0.000000] ACPI: ASF! B7CF9000, 00A5 (r32 TOSINV TOSINV00        1 MSFT  1000013)
[    0.000000] ACPI: SLIC B7CF0000, 0176 (r1 TOSINV TOSINV00        1 MSFT  1000013)
[    0.000000] ACPI: BOOT B7CEF000, 0028 (r1 TOSINV TOSINV00        1 MSFT  1000013)

The [COLOR=Red]"MSFT"[COLOR=Black] means it was made with the Microsoft compiler. [/COLOR][/COLOR]:D

Are you telling this to me? How can I see what kind of operation the cd is doing when it stops working?

---

### Post by 67GTA on 2009-01-24
I was talking to Therion, but it could apply to you. You could hit F6 at the grub screen and then delete the "quiet splash --" at the end of the line that just appeared. You might also want to try booting in safe mode. Hit F4 instead of F6 and choose "safe mode".

---

### Post by kuabba82 on 2009-01-28
> **67GTA said:**
> I was talking to Therion, but it could apply to you. You could hit F6 at the grub screen and then delete the "quiet splash --" at the end of the line that just appeared. You might also want to try booting in safe mode. Hit F4 instead of F6 and choose "safe mode".

Sorry, but I had some problems, so I could only try this morning this thing.

I deleted "quiet splash --" and I could see the operations the Live Cd was doing.
When the loading stops, the last thing is:

> [73.220224] Input: imexeps/2 Logitech Explorer Mouse as /devices/platform/I8042/serio1/input/input5

So I think there's a problem with my optical wireless mouse...but I don't have another one to try if it works. What can I do?

---

### Post by boof1988 on 2009-01-28
> **kuabba82 said:**
> Sorry, but I had some problems, so I could only try this morning this thing.

I deleted "quiet splash --" and I could see the operations the Live Cd was doing.
When the loading stops, the last thing is:



So I think there's a problem with my optical wireless mouse...but I don't have another one to try if it works. What can I do?

Maybe try booting without the mouse plugged in (use the keyboard for selecting etc).  Use the same options as before and see what happens.  I know it is a lot harder (maybe different) to use the keyboard to maneuver around and select things.  But maybe this will help troubleshoot the problem a little more.

HTH a little.

---

### Post by kuabba82 on 2009-01-28
> **boof1988 said:**
> Maybe try booting without the mouse plugged in (use the keyboard for selecting etc).  Use the same options as before and see what happens.  I know it is a lot harder (maybe different) to use the keyboard to maneuver around and select things.  But maybe this will help troubleshoot the problem a little more.

HTH a little.

But if it's so, I could have this problem even if I install Ubuntu on external USB Hd or you think it's a problem only with live cd?

---

### Post by irpayne on 2009-01-28
Interesting because I have been trying to install onto my newer laptop and it hangs on the splash screen. will try the keyboard trick when my daughter gets off it.
As an aside install onto older hpcompaq9010 was faultless and got it working with wifi and everything!

---

### Post by boof1988 on 2009-01-28
> **kuabba82 said:**
> But if it's so, I could have this problem even if I install Ubuntu on external USB Hd or you think it's a problem only with live cd?

I don't know... I was just thinking that if the computer can boot the LiveCD without the mouse attached than at least we know that the problem might have something to do with the mouse.  And then maybe someone else may have a solution to the mouse problem.

---

### Post by kuabba82 on 2009-01-28
> **boof1988 said:**
> I don't know... I was just thinking that if the computer can boot the LiveCD without the mouse attached than at least we know that the problem might have something to do with the mouse.  And then maybe someone else may have a solution to the mouse problem.

Ok, now I can't try until tomorrow, so I'd like to ask you another question. My mouse is not alone, it's a solution mouse-keyboard. Do you think it's possible that keyboard works and mouse not?

---

### Post by irpayne on 2009-01-28
I have tried installing via wubi which gives me a dual boot choice and have done the safeboot options thing. Also have tried from cd rom.
Basically hangs on about two and half bars of meter on splash screen.
If i select acpi safe choice from boot choices i get a console style cursor and can open the help files etc and do edits, but this is academic as i have not got a clue about linux command line stuff, hell i have been trying to get over dos for years and this stuff is a mind f**k  !!!!!
Only mouse is the touch pad

---

### Post by boof1988 on 2009-01-28
> **kuabba82 said:**
> Ok, now I can't try until tomorrow, so I'd like to ask you another question. My mouse is not alone, it's a solution mouse-keyboard. Do you think it's possible that keyboard works and mouse not?

Sorry... I don't know.  I wasn't thinking about the possibility of your mouse being on the same connector as your keyboard.  I don't have any other ideas.

I hope someone else can help more.

---

### Post by kuabba82 on 2009-01-29
I tried to start live cd without mouse and now it stops loading on another thing:

> [73.481896]EMU10K1_AUDIGY 0000:00:0a.0: PCI INT A ->GSI18 (Level, low) -> IRQ 18

It's known this?

---

### Post by boof1988 on 2009-01-29
> **kuabba82 said:**
> I tried to start live cd without mouse and now it stops loading on another thing:



It's known this?

I don't know the solution.  But it may help to include (if possible) a few lines before and after the line you posted.  Not sure if it's needed but I wanted to try to help a little and give your thread a bump as well.

EDIT:

You could try pressing some (any) key when it hangs and see if that will help it get past the error.  (I don't think this will work, but it could be worth a try if you have time)

---

### Post by kuabba82 on 2009-01-29
If you read my message in page 2 of this topic, you can read that I've already try to press any key, without results...

---

### Post by kuabba82 on 2009-01-29
I think the second line is for my sound blaster audio card, but I can't understand why the live cd stops loading...it's an old model...

---

