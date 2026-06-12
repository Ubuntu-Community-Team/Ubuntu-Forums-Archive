---
title: "WTF just happened to my computer??"
date: 2009-01-27
forum: Hardware
---

### Post by grndslm on 2009-01-27
Everything was working fine with Hardy, but I decided to upgrade to a fresh install of Intrepid.  I did make a lot of changes to the Sessions (Personal settings) & Services (System-wide settings) found in the GNOME menus.

Upon reboot, I got a an error about using the Driver "nvidia" line like I'd heard somebody complain about on IRC.  Never had a problem with prior releases.  Then my memory is real hazy as this happened early yesterday and I got drunk last night in memory of my box... but I think it shut itself of, but I might have done it myself.

After that last poweroff, I get no more video.  The fans are running, but it doesn't sound like the hard drive's trying to do it's thing.  I've reset the CMOS several times, by unplugging everything from the mobo and leaving the battery out.  To be extra sure, I used some scissors to short out the CMOS reset switch.

I've never had something like this happen before, and I'm not sure what to troubleshoot first, if there's anything?  How would you guys troubleshoot this?

Background:  I have a Q6600 in a Gigabyte GA-G33M-DS2R I've been overclocking off and on with the auto-OC feature in the mobo.  I've got the G0 stepping version of the Q6600 and a Zalman fan... the thing has been pretty cool even OCed to 3.2 GHz.  The lame part is that I've only OCed it for no more than 2 or 3 weeks total.

---

### Post by Therion on 2009-01-27
Okay, I *think* I have a grip on what happened and what you've done.  Not sure why you reset your CMOS but we'll just start from where you are.

Now then... When you cold-boot your PC, what happens exactly?

Also, can you boot to a LiveCD session?

---

### Post by cariboo on 2009-01-27
There was a problem with your driver installation, start up in recovery mode and select xfix at the menu, once xfix is finished select resume and you should be back at the default desktop.

Jim

---

### Post by konradpiskorz on 2009-01-27
Well, some more information would be nice.

Was Intrepid working before you messed with the settings?

You said a clean install?  So format and install from live cd?

When you say no video, do you mean just on OS boot or do you not see your bios data on boot either?

If you have a spare computer sitting around, Swap out the parts one by one to see what is working and whats broken.

Your a little unclear but it just sounds like hardware failure to me.  It happens fairly frequently with electronics, over clocking helps with that too :)

---

### Post by carolinason on 2009-01-27
I used to do drunk computing, but now prefer ginger ale. I have to laugh sorry. I'm not sure what you mean by fresh install by upgrading, but typically a fresh install is from scratch and an upgrade is to upgrade an older version to a new one.

You shouldn't have to reset the CMOS.

Try and use the "nv" driver instead. Boot into single mode, ehem Maintenance Mode to do this. The line is in /etc/X/xorg.conf and replace "nvidia" with "nv".

---

### Post by grndslm on 2009-01-27
When I cold boot my PC, nothing comes on the screen... nothing from the BIOS, and there's no POST beeps that notify me of something being wrong.  And the fans are running, but the HDD and DVD aren't spinning... so a LiveCD won't do me any good.

---

### Post by grndslm on 2009-01-27
> **konradpiskorz said:**
> Well, some more information would be nice.

Was Intrepid working before you messed with the settings?

You said a clean install?  So format and install from live cd?

When you say no video, do you mean just on OS boot or do you not see your bios data on boot either?

If you have a spare computer sitting around, Swap out the parts one by one to see what is working and whats broken.

Your a little unclear but it just sounds like hardware failure to me.  It happens fairly frequently with electronics, over clocking helps with that too :)Yes, Intrepid was working fine before the last poweroff.

Yes, I said a clean install, formatted and isntalled from live cd

No video from BIOS, No beeps from POST.  Read above about fans spinning, but not HDD and DVD.

Sure I've got tons of computers sitting around, but none of the parts are interchangeable.... other than HDD and monitor, which aren't the problems.

I'm very clear.  I speaka good Engrish!  It seems like I'm gonna have to buy a new mobo or CPU... but I don't know which would be a better starting point.  And I don't see how overclocking could be the problem, when I've only done it for such a short period of time, and I know it wasn't overheating at all.

---

### Post by Therion on 2009-01-27
> **grndslm said:**
> When I cold boot my PC, nothing comes on the screen... nothing from the BIOS, and there's no POST beeps that notify me of something being wrong.  And the fans are running, but the HDD and DVD aren't spinning... so a LiveCD won't do me any good.
Yeeeeah... I was afraid you were going to come back with something along these lines.

Okay big boy, hope you're up for some fun.  Here's what I'd be doing in this case...

Crack the case and strip the mobo down to the bare essentials in hopes of getting some kind of bootstrap configuration that will at least pass POST and present the BIOS menu.  

Then you reset the BIOS to factory failsafe defaults and start adding back your hardware components one at a time, rebooting between each to make sure everything is still operational.  At some point you're gonna find a dead component.

Does your mobo have a power LED?  Most mobos released in the past few years have an LED on them that shows that the mobo itself is receiving power from the PSU.  If that's not glowing, you're not going.

---

### Post by Maheriano on 2009-01-27
And that component (I think) is the board. It should at least POST with nothing but a board plugged in.

---

### Post by bgerlich on 2009-01-27
Start gutting your PC, seriously. Take out RAM and check if you get POST beeps, if not then you are pretty much ... not in a good place.

If you do get some response, try booting without the graphics card, use the internal card.

---

### Post by Therion on 2009-01-27
> **Maheriano said:**
> And that component (I think) is the board. It should at least POST with nothing but a board plugged in.
Going by what you've told me, that's very possible.

Check for one of them power-LED's I mentioned.  

What about the CPU fan, does it spin-up when you turn on the box?  If the answer is "No..." then yeah, I'd say you're looking at a dead mobo or a dead PSU.

---

### Post by Gramps on 2009-01-27
It almost sound like there is an issue with the video card. Got another video card you and install and see what happens?

Remove the power and cables from the drives and see if you can see the boot up from CMOS 

If hook the CD back up and see if it will boot from a live CD

---

### Post by Squid Spectre on 2009-01-27
I've been in that place, take out everything but your RAM and video card and see if you can get an image. If that doesn't work start working your way from the power supply in (meaning swap it with another supply if you have one) then move onto the video card then RAM. Check for any LEDs going on or off during the process, most all motherboards have some sort of "receiving power" or "power on" signal. If it works after removing something specific, you've found your problem. If nothing works you may be looking at a blown motherboard or corrupt BIOS image, which would be a remarkable feat when just installing on OS.

---

### Post by grndslm on 2009-01-27
I've gotta do some stuff now, but I'll definitely get back to you guys with the results later today.

Just to let you know, tho... as I said in my first post... I've unplugged everything from the mobo and reset the CMOS.  That has solved 95% of the problems I've had with a computer, but not this time.  Of course, I was plugging everything back in, but I'll do the piece by piece plan tonight.

Can overclocking a cpu actually cause the mobo to fry?  And will the mobo load the BIOS without a cpu?

I'm guessing first boot should be with mobo, cpu, & video... then add 1 stick of ram.. then switch for the other stick.

---

### Post by Maheriano on 2009-01-27
> **grndslm said:**
> I've gotta do some stuff now, but I'll definitely get back to you guys with the results later today.

Just to let you know, tho... as I said in my first post... I've unplugged everything from the mobo and reset the CMOS.  That has solved 95% of the problems I've had with a computer, but not this time.  Of course, I was plugging everything back in, but I'll do the piece by piece plan tonight.

Can overclocking a cpu actually cause the mobo to fry?  And will the mobo load the BIOS without a cpu?

I'm guessing first boot should be with mobo, cpu, & video... then add 1 stick of ram.. then switch for the other stick.

In the past when I've burnt out CPU, it would POST, beep, reboot and cycle through forever. But yes, it did POST I believe (trying to remember from 10 years ago).

---

### Post by carolinason on 2009-01-27
[HTML]Can overclocking a cpu actually cause the mobo to fry?[/HTML]
yes, you can fry a mobo by overclocking.
```

And will the mobo load the BIOS without a cpu?
```
no, and an error tone shouldn't be confused with a POST. a successful POST gets you to the BIOS interface.

---

