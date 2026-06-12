---
title: "Dell Inspiron 1100"
date: 2008-09-27
forum: Hardware
---

### Post by El Rogueo on 2008-09-27
Hi all,

I'm working on a Dell Inspiron 1100, but it's been giving me trouble:

On a clean installation, the computer boots, installs, reboots, updates, nothing special, and with no problems, errors, or any other sign of fault. However, when I restart the computer to apply the updates, the computer will boot up through GRUB and then hang. The screen stays black and unresponsive, and I never hear the Ubuntu login drums. However, via a contrivance of shutting down and restarting the computer repeatedly (using the start button, I can't elicit so much as a beep from it using the keyboard) it will eventually, on one of the repetitions, boot up just fine as though nothing were wrong.

For a while there was a pattern, where you could turn on the computer, hang it, turn it off manually, turn it back on, and it would work (turning on every other time) but now it just more or less does not boot properly every time.

Any ideas? I thought it might be ACPI related but I can't imagine what I'd do to fix that.

---

### Post by gossrock on 2008-09-27
Intermitant problems are a pain.  This has never happened to me but the first thing that I would look for would be a hardware problem.  Check to see if all the conectors in the case are seated proprely.  

If it still doesn't work try running fsck (file system check) on the disk to see if your disk is okay. I use a distro called finux to do this but there may be a way to useing the Ubuntu CD.  It's been a wile since I've needed to do it so I would have to get back to you for detailed instructions (after testing it out myself).

---

### Post by El Rogueo on 2008-09-27
disk check reports nothing wrong

I didn't identify very well, my bad; this computer is a laptop, and I haven't ripped it open, so I can only assume the connection is okay.

I've also had a similar problem on another laptop of mine, but that was due to hibernating with too little space to save state to, so it doesn't exactly apply here very well.

I also did a memory test for the heck of it, and finished my updates, but ubu says everything's fine. The broadcom drivers for the wireless card took just fine, and my prediction that it could be a graphics problem isn't going anywhere, since I'm not using any proprietary drivers and it looks just fine.

AND I checked the system logs, but it looks like it shuts down normally (without incident).

---

### Post by snowpine on 2008-09-27
I had a similar problem with my old Dell Latitude Cpx laptop that I believe was caused by the swappable cd/floppy drive bay. If your laptop has this same feature, the following may work for you:

Try adding 'all-generic-ide' (without the quotes) to your Grub kernel boot line (press e to edit it). If that works, you can make the change permanent with 'gksu gedit /boot/grub/menu.lst', scroll down until you find the kernel boot line for Ubuntu, then add 'all-generic-ide' to the end of that line and save the file.

---

### Post by gossrock on 2008-09-27
Did you have another operating system on the laptop (read windows) and was it having problems too or did it run as expected?

---

### Post by El Rogueo on 2008-09-27
I have the feature, and I added the line, but it didn't work. The sequence of events goes like this:

Boot up, installation (restart)
Computer hangs (forum post created)
(your advice)
Computer starts fine (restart)
Computer hangs (restart)
Computer starts fine

*now*

so adding the line didn't hurt, but it only booted because it's been working every other time.

No problems with Windows, and the only other OS I've used on this computer besides Windows and Ubuntu is SLAX, but I only do that liveCD, so I've never had the opportunity to encounter a restart problem when every boot is a new boot, as far as SLAX is concerned.

Could it be something due to whether or not the computer identifies that it shut down (im)properly?

And what would I do about that?

---

### Post by gossrock on 2008-09-27
Okay, not having expeariances like this and the easy answers don't work ... I begin googleing.


This may not have the answer but there seems to be a lot of good stuff. Seems like there is a bios update that is need for proper oporations.  
[http://www.geocities.com/randomnumbergenerator2001/](http://www.geocities.com/randomnumbergenerator2001/)

I will continue to look around.

---

### Post by gossrock on 2008-09-27
Here there is a discription of a problem similar to yours I think:
[http://ge.ubuntuforums.com/showthread.php?t=819541](http://ge.ubuntuforums.com/showthread.php?t=819541)

Here is the updated solution:
[http://ubuntuforums.org/showthread.php?t=822192](http://ubuntuforums.org/showthread.php?t=822192)

seem 8.04 and this laptop don't mix

---

### Post by El Rogueo on 2008-09-27
good call on the BIOS thing, I'll look into it
checking out the links now

---

### Post by El Rogueo on 2008-09-27
Unfortunately for that tutorial, I already have the A32 BIOS, so that's not the problem.

Similarly, I already have acpi and acpid, so that entire guide looks like it's already been applied.

Going to go through the logs again, and try to figure out this every-other business

---

### Post by gossrock on 2008-09-27
What version of Ubuntu are you working with?  If it is Hardy then it may be the problem.  The guy that wrote [http://ubuntuforums.org/showthread.php?t=822192](http://ubuntuforums.org/showthread.php?t=822192) found that using Gutsy worked for him.

---

### Post by jbrax on 2008-10-20
These are the steps you have to take to get Ubuntu-8.04 installed into Dell Inspiron 1100: 

[B]1. Upgrade your laptops bios to A32
2. Change the video memory from 1MB to 8MB in BIOS setup
3. Install Ubuntu-8.04 
4. Add sync-lines and resolution to /etc/X11/xorg.conf to get 1024x768 resolution
5. Change splash to nosplash, line 89 in /boot/grub/menu.lst [/B]
   This last one fixes the "Blank screen after every other boot" -error. 

For more detals see my comment at [http://ubuntuforums.org/showthread.php?t=819541](http://ubuntuforums.org/showthread.php?t=819541)

---

