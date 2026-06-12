---
title: "Not sure if I have hardware (electrical) or software (kernel panic) problem"
date: 2012-11-04
forum: Hardware
---

### Post by venom104 on 2012-11-04
I was getting really bad performance from black ops under WINE so I decided to give it a try under windows.

Well, when I booted to windows 7, I noticed alot of my stuff was out of  date (I haven't booted into windows in at LEAST 6 months), so i started  downloading steam, black ops, and the binary nvidia driver for my video  card.

The thing that I noticed when I first booted into windows is that it  said it didn't shut down properly the last time I used it. I didn't  really care so I booted into the regular mode.

Well...10 minutes later my system shut off. NONE of the other stuff in my room went out, so I HIGHLY doubt it was a brown out. 

When I got back into windows, i got a bunch of notices that some files  on my system were corrupted and that I should run chkdsk. I just ignored  them and went to download my stuff.

15 minutes later...my system just turns itself off again. At this point,  I checked all the cables to my computer for damage, and replugged  everything back in and just thought it might be something as simple as  that.

So I start downloading my stuff again, and 20 minutes later it just randomly shuts itself off.

Now I'm not windows expert and its been ages since I did any real  computer tech work, but how are kernel panics handled in windows 7 now a  days? Do they still give you the blue screen of death?

I'm guessing that it's not a software problem since the entire system just turns itself off without any given notice.

I'm running chkdisk right now and it's taking forever. When I get back  into windows 7, I'm going to check the event viewer for anything funny. I  also turned on all my BIOS overheating and fan failing warnings.

The thing I find kind of odd is that I BARELY use windows at all on my  computer and this has never happened to be before under linux. The ONLY  time I ever boot into it, is when I need to run some engineering  software or compile something in visual studio.

My brother is an electrician, so I was thinking I could get a multimeter and test the power supply to see if it's failing.

Anyway, my questions are...

1) This sounds like a  hardware problem despite not happening in linux right?
2) I don't really run that many services on my computer (under windows).  I do have a firewall and an anti-virus enabled, but that's pretty much  it (aside from whatever services windows runs by defualt)
3) What else should I do to find out what the problem is?
4) What do you think the problem is?
5) Why would this not happen for years under linux, but when I boot into windows it does this?

Thanks for any attempt to help

---

### Post by 2F4U on 2012-11-05
The things I would do:
1. Check the event viewer
2. Do a complete virus scan
3. Run memtest, preferably more than one iteration
4. Check temperature in Windows, maybe the machine is overheating

---

### Post by varunendra on 2012-11-07
> **2F4U said:**
> The things I would do:
1. Check the event viewer
2. Do a complete virus scan
3. Run memtest, preferably more than one iteration
4. Check temperature in Windows, maybe the machine is overheating
+
5. Maybe one of the 'improper' shutdowns actually corrupted some critical system files ?

> **venom104 said:**
> (I haven't booted into windows in at LEAST 6 months)Oops! I lost to you..! I committed the crime at least twice or thrice in the last 6 months.. and for more than 30 minutes.. :(

However, you seem to have either really good or very little experience with windows if you could ignore these warnings so many times :
> **venom104 said:**
> 10 minutes later my system shut off.
..
..
When I got back into windows, i got a bunch of notices that some files   on my system were corrupted and that I should run chkdsk. I just **ignored**   them and went to download my stuff.

15 minutes later...my system just turns itself off again... thought it **might be something as simple** as   that.

So I start downloading my stuff again, and 20 minutes later it just randomly shuts itself off.
..and still you think it CAN't be a software problem:confused:
> **venom104 said:**
> I'm guessing that it's [COLOR=Red]**not a software problem**[/COLOR] since the entire system just turns itself off without any given notice.

> **venom104 said:**
> 1) This sounds like a  hardware problem despite not happening in linux right?
2) I don't really run that many services on my computer (under windows).   I do have a firewall and an anti-virus enabled, but that's pretty much   it (aside from whatever services windows runs by defualt)
3) What else should I do to find out what the problem is?
4) What do you think the problem is?
5) Why would this not happen for years under linux, but when I boot into windows it does this?
1) I STRONGLY believe it is a 'software' problem (corrupt or missing system files - either due to crash or the usual excuse - Virus ;))
3) Suggested by 2F4U and me above
4) Could be hardware, but a software problem is more probable in the given circumstances.
5) Perhaps because windows is more fragile ?? :)

If the number or size of files found in "FOUND*" directories created after chkdisk is fairly large, it would strongly suggest a file-corruption problem as I doubt.
Accordingly, a "System Restore" may be able to fix the problem, but be prepared to reinstall grub if you try that.

---

### Post by venom104 on 2012-11-07
***********************************

UPDATE

***********************************

I turned on the BIOS warnings for the system and CPU temps going over 90 degrees Celsius...went off over and over again after about 5 minutes. Turned off the system temp warning...CPU temp warning still going off.

I called cyberpower and they are shipping me some replacement thermal paste, a heatsink, and a fan.

Since I turned off Aero (not that my computer couldn't handle it), and it still happened, I really doubt that this is a software error...although the thing about it only happening in windows bothers me.

I'll probably update the thread again once I install everything and can actually use visual studio at my home again.

Although I STRONGLY believe it's a hardware problem...I am not dismissing the possibility of some bad BIOS code....I am really scared to update it, and I probably wont...but if this persists then I might not have any other choice.

EDIT...

Forgot to add a response to the above thread...it wont finish the chkdsk program without turning off. I'll give it another try once I install the stuff, but if it doesn't fix it then I'll probably format the partition and reinstall windows...god I hope I can get a CD from someone...the key is on the computer, but I don't know if those work with every version of windows 7...anyone know for sure?

---

### Post by venom104 on 2012-11-07
> **varunendra said:**
> +

Accordingly, a "System Restore" may be able to fix the problem, but be prepared to reinstall grub if you try that.

I would have to reinstall grub? Why? I'm not changing the location of the GRUB bootloader, and I'm not SUPER sure but I don't believe that doing a system restore doesn't clear the bootloader...think i remember having to do a command to do that with the format command when I was running windows 95 in class to get rid of a virus on a machine...NADAS was it?

---

### Post by varunendra on 2012-11-07
> **venom104 said:**
> I hope I can get a CD from someone...the key is on the computer, but I don't know if those work with every version of windows 7...anyone know for sure?Win7 image won't fit on a cd, you'll need a dvd. Much better, use [WinToFlash]("http://wintoflash.com/home/en/") or a similar tool to create a win7 bootable usb and install from there.

Also, keys are different for different Win7 versions. Your key will only be valid for the version (& perhaps even the product id) it was originally meant for.

> **venom104 said:**
> I would have to reinstall grub? Why?IIRC, the win7 'System Restore' program has the capability (& default behaviour) to detect and 'repair' MBR if found tampered. But I'm not super sure either ;)

---

### Post by venom104 on 2012-11-14
**********UPDATE******** 11/14/2012

Well, I got my replacement fan + heatsink and thermal paste in the mail (I guess they pre-apply them now to prevent user error...).

I'm actually using my computer now and it's running about 10 degrees cooler than it did before.

Been half an hour now since I turned it on (which shows some improvement), and I haven't heard any of the BIOS overheating errors.

I'm going to leave it on for a while and see if this problem is solved.

I will run chkdisk when I can.

EDIT:::

WOW! I was wrong, I had the temp monitor set to ferinheight when it should have been to Celsius (which makes me wonder why they don't measure it in kelvins..) and it's not just 10 degrees cooler. It went from 79 C (just downloading stuff) to <29 C.

---

### Post by venom104 on 2012-11-17
*********************UPDATE 11/17/12************

Well, I've been running my computer every night (just having it download stuff and idle), and it seems nothing went wrong.

I have a temperature monitor program going for windows that records the temp when it gets over 90 C, and also I have every bios warning for dying fans, system/cpu temp enabled.

I have not heard anything in days. 

However, when I first did my system on and boot into widows, my screen kept resizing and then it would freeze in a random array of colors. I tried to update the video driver before I installed the heatsink and I'm guessing it didn't go all the way though. Reinstalled the driver, ran chkdsk (only took about 30 minutes) and everything has been fine ever sense

Call of the Dead rules! 

Thread Closed!

---

