---
title: "[SOLVED] Please help - Ubuntu takes 10 minutes to boot"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by Damien Kane on 2008-01-11
Hi all - I'm hoping you can help. I've had a lot of problems with Ubuntu v7.10

I really enjoy the system and wanted to replace my Windows ME on a laptop:

IBM Thinkpad X23
866 Intel P3-M
384MB RAM
40GB HDD

I have to CD or floppy drive, so installed the laptop drive as a USB in a desktop and detatched all other hard drives. Install wasn't an issue. I then took it out and put it in the laptop. It took about five minutes to boot. That was yesterday, and today, it takes 10 minutes to boot, even when connected to the mains.

I found a lot of useful info on the internet which reduced the time to five minutes for the next reboot, but the reboot after that, it went back to taking 10-15 minutes.

I use the laptop mainly to write and would like to watch Avi (XVid) movies, which Windows ME doesn't do. Any help in reducing the boot time would be great, as I intend to use it for the train!!

Best regards

---

### Post by Damien Kane on 2008-01-11
Erk - I mean I have no CD or floppy drive! hehaehe

---

### Post by Z_o-s-o on 2008-01-11
You've physically installed Ubuntu to hard disk and are not running it off the live cd correct?

---

### Post by K.Mandla on 2008-01-11
Assuming you're using a straight Ubuntu installation, you might want to look for lighter desktop environments. Fluxbuntu should be speedy on that machine, or Xubuntu, but that's a matter of opinion there. :)

---

### Post by Damien Kane on 2008-01-11
Ubuntu runs fast on the laptop - it's just the boot time that's a problem. I'm using the laptop with the hard drive installed and not the LiveCD. I may not have explained that correctly, so I do apologise.

I don't have a CD or floppy on the laptop, so used an external USB caddy and attached the laptop hard drive with it to a desktop. I removed the desktop's hard drives so it didn't install GRUB to them, and launched LiveCD. In LiveCD, I installed Ubuntu to the external hard drive (ie, the laptop drive). After installation, I put the hard drive back in the laptop, then booted it up.

Hope that makes sense! In a nutshell, Ubuntu works great. It's just the booting.

---

### Post by Darkhack on 2008-01-11
It sounds like the kernel freaks out for a bit while trying to detect hardware.  I had this happen before.  When you boot into GRUB, highlight the Ubuntu install and then press the letter 'e'.  This will display the details.  Next, go to the second line (should begin with the word "kernel") and press 'e' again to actually edit that line.

Now use the arrow keys to go over to the very end of the line (if it's not already there).  Remove the word "quiet" and change "splash" to "nosplash".  Then add the word "verbose" to the end.

The kernel will then tell you what it is doing as it is booting and it will give messages as to what is going on.  In my situation when I had this problem there was an issue with assigning an IRQ to USB devices so it had to sit and think for a while and try a bunch of different IRQs for 10 minutes before giving up and continuing on with the boot process.

Paste the output of the kernel booting on verbose and maybe we can find the issue.

---

### Post by jocko on 2008-01-11
One way to see what's taking time during boot is to install bootchart.
Search for it in synaptic, or type 'sudo apt-get install bootchart' in a terminal.
On every boot, it will produce a chart showing the entire boot process (placed in /var/log/bootchart).
If you post a bootchart here, I'm sure someone will have an idea on how to fix it.

---

### Post by Damien Kane on 2008-01-11
I tried the nosplash thingy and also did it in a terminal window because it was supposed to make the change permanent, and it took around 5 minutes to boot, but it suddenly stopped working. I'll do the bootchart. Might take a while ...!

Thanks for all your help by the way. I did try install through a 2GB USB stick, but the instructions were too complicated for me to follow.

Ok - bootchart ...

---

### Post by Damien Kane on 2008-01-11
That's really weird - it took 10 minutes when I turned it on after that last post, then I installed bootchart and rebooted, and it took 23 seconds to boot again.

I'll turn the computer off for a bit and try again later. 23 seconds though - that'd be good!

I'll be back ...

---

### Post by Damien Kane on 2008-01-11
For some reason, since installing bootchart, I've noticed the following on the laptop and don't understand why:

1. I've tried booting up four times and each time has been under 45 seconds.
2. The screen with the Ubuntu logo and boot progress indicator is back. Before, it used to scroll a list of what it was doing (I think that was from the ro quiet splash edit).
3. Even shutting down takes just 15 seconds instead of a couple of minutes.

Crikey it's fast now.

So I'm sorry for posting. I don't know why or how it's been fixed but I'm a happy Aussie.

---

### Post by Darkhack on 2008-01-11
Yay!  I'm glad you got it working.  Let me throw in a nice little bonus tip to improve performance even faster on boot.

Edit the GRUB entry like I talked about before but this time just add the word "profile" to the end.  Do this only once.  Do not make this change perminant or add the word profile to each and every boot.  What this will do is create a profile of the boot process and create a kind of index file for reference.  When booting with "profile" it will be slow as it takes time to scan and create the profile, but the next time you reboot your machine (sans "profile") it will automatically read the profile and be able to boot faster than it would if it had to scan and locate all the necessary boot files on its own.

---

### Post by nbitting on 2008-01-31
I'm getting the same issue...i tried all of the fixes presented in this thread but it still takes a while to boot up.  It's also not showing the Ubuntu loading bar before you get to the login screen.  I'm also see blue lines scroll on the screen just before it gets to the login page...what's that???

I am seeing something right after the text "Starting up..." pops up on the screen during bootup...it says something like BIOS 8254 Timer not connected....something like that.

Any help would be greatly appreciated!

Thanks!

---

