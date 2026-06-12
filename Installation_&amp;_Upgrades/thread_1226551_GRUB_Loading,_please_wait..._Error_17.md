---
title: "GRUB Loading, please wait... Error 17"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by stealthbt on 2009-07-29
I just tried installing my very first linux distro and....it looks like I'm off to a rough start!  I'm trying to set up a media box using a Gateway Media Center PC.

I burned the live Ubuntu 9 disk to a cd, booted from it on the PC, installed the Ubuntu OS, ejected the disk and hit enter when it was finished.  Everything seemed to be working until the computer restarted and the first thing I see is this screen.  

I tried booting from the CD and repeating the process but I received the same result upon reinstall and reboot.

Any help would be greatly appreciated! Thanks!

[IMG]http://files.getdropbox.com/u/746243/Ubuntu%20Error.jpg[/IMG]

---

### Post by merlinus on 2009-07-29
Whilst running from the live cd, open a terminal and post results of

```
sudo fdisk -l
```

---

### Post by stealthbt on 2009-07-29
> **merlinus said:**
> Whilst running from the live cd, open a terminal and post results of

```
sudo fdisk -l
```

I'll go do that right now.  But one additional piece of info that may or may not help.  When I ran the installer, I told it to use the entire start disk instead of running side by side with the windows 7 I had installed on that drive.  I assumed it would simply erase the drive and repartition it with Ubuntu as the only OS.

---

### Post by merlinus on 2009-07-29
Do you have more than one hdd?

---

### Post by stealthbt on 2009-07-29
> **merlinus said:**
> Do you have more than one hdd?

I have three HD's installed.  One 320gb set as the primary for OS and small storage.  Then I have two other larger HD's, 1TB & 1.5TB, that store all of my movies.  I'm setting this box up as a HTPC.

As a side note, I'm planning on installing a PCI firewire 800 card so I can hook up my drobo.  (I'm scared of a disk dying and all the movies and data I'd lose!).  Will I have any issues with firewire 800 or the drobo within ubuntu?

Here is a picture of what I saw when I ran the command you gave me in your first reply:

[IMG]http://files.getdropbox.com/u/746243/Ubuntu%20Error2.jpg[/IMG]

---

### Post by philcamlin on 2009-07-29
the letter L  not the number 1 one :D :popcorn:

---

### Post by stealthbt on 2009-07-29
> **philcamlin said:**
> the letter L  not the number 1 one :D :popcorn:
Haha!  Can you say ubuntu newbie ten times fast?   Brb....

---

### Post by stealthbt on 2009-07-29
> **philcamlin said:**
> the letter L  not the number 1 one :D :popcorn:
Ok...let's try this again.  Here's what I got when I ran sudo fdisk -l

[IMG]http://files.getdropbox.com/u/746243/Ubuntu%20Error3.jpg[/IMG]

---

### Post by merlinus on 2009-07-29
What is the boot order of your hdds in bios?

---

### Post by stealthbt on 2009-07-29
> **merlinus said:**
> What is the boot order of your hdds in bios?

the two optical drives boot first, then the 320gb drive (that ubuntu was supposed to be installed on), then the other two (I'm not sure which order--if it matters I will restart and find out)

---

### Post by merlinus on 2009-07-29
It definitely matters.

---

### Post by stealthbt on 2009-07-29
> **merlinus said:**
> What is the boot order of your hdds in bios?
I just checked and it's the 320gb, then 1.5TB, then 1TB.

---

### Post by merlinus on 2009-07-29
You may have to unplug all but the linux hdd in order to reinstall grub, but we can try this first:

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

---

### Post by stealthbt on 2009-07-29
> **merlinus said:**
> You may have to unplug all but the linux hdd in order to reinstall grub, but we can try this first:

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

Am I supposed to enter these in order with an ENTER between each command or just type it all in at once?

I tried it both ways and when I got to setup (hd0) it said: Error 17: Cannot mount selected partition

---

### Post by stealthbt on 2009-07-29
> **merlinus said:**
> You may have to unplug all but the linux hdd in order to reinstall grub, but we can try this first:

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

I can just open the case and unplug the other two HD's for the time being if that will make it easier.  I wish I understood more about Ubuntu in general to know why this is necessary.  I don't understand why the mere presence of the other HD's is causing an issue.

---

### Post by merlinus on 2009-07-29
One command at a time.

I did not think this would work because of the boot order of your hdds, and the order might have been different when you installed ubuntu.

Try this:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```

---

### Post by stealthbt on 2009-07-29
> **merlinus said:**
> One command at a time.

I did not think this would work because of the boot order of your hdds, and the order might have been different when you installed ubuntu.

Try this:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```
 
The boot order was the same when I installed Ubuntu the first time.  I haven't changed anything.

Here are the results from the commands you told me to enter.  Did I enter it correctly?  I wasn't sure.

[IMG]http://files.getdropbox.com/u/746243/Ubuntu%20Error4.jpg[/IMG]

---

### Post by merlinus on 2009-07-29
Looks like it worked.  Try restarting without the cd.

---

### Post by stealthbt on 2009-07-29
> **merlinus said:**
> Looks like it worked.  Try restarting without the cd.
You got me all excited....then I rebooted....same original error message.  GURB loading, please wait....
Error 17

:(

---

### Post by merlinus on 2009-07-29
Here is the problem.  (hd2) is sdc1, the linux drive.  That is where grub is installed.  But it is first in booting order, which would be (hd0), and we know that didn't work.

What if you change the booting order so it is third?

---

### Post by stealthbt on 2009-07-29
> **merlinus said:**
> Here is the problem.  (hd2) is sdc1, the linux drive.  That is where grub is installed.  But it is first in booting order, which would be (hd0), and we know that didn't work.

What if you change the booting order so it is third?

Just change the boot order in the bios is what you're saying to do?  I just want to make sure I don't lose any data on my 1TB or 1.5TB drives.  Please verify that putting those first in the boot order won't screw things up.

Also, let me know exactly what order you would like them in.  320gb, 1.5tb, and 1tb.

Thanks for all your help!  I can't believe how fast and responsive you have been in this forum.

---

### Post by merlinus on 2009-07-29
You won't lose data by changing boot order.  Put the linux hdd third, after the 1T and 1.5T, and see if that works.

---

### Post by stealthbt on 2009-07-29
> **merlinus said:**
> You won't lose data by changing boot order.  Put the linux hdd third, after the 1T and 1.5T, and see if that works.
Wow that's some crazy ****.  Coming from a Mac and Windows world this just doesn't make any sense to me!  How in the world does it make sense to move your primary drive to the 3rd slot in boot order to make it work!?  

Regardless, my machine booted up into Ubuntu without a problem when I changed the boot order as you suggested.  I'm so confused...haha!

---

### Post by merlinus on 2009-07-29
It may have to do with the way it was installed.  Quien sabe?

But hey, if it works, then be grateful!  And happy!!!

---

### Post by stealthbt on 2009-07-29
> **merlinus said:**
> It may have to do with the way it was installed.  Quien sabe?

But hey, if it works, then be grateful!  And happy!!!

Thank you so much for all of your help.  I really appreciate it.  I definitely wouldn't have figured that out and I probably would have bailed on the whole idea of running ubuntu for my media center.

I'm off to read up on the documentation and figure out how to get all of my drivers installed.  The default video resolution is terrible!

---

### Post by merlinus on 2009-07-29
You might look in System/Administration/Hardware Drivers.

---

### Post by stealthbt on 2009-07-29
> **merlinus said:**
> You might look in System/Administration/Hardware Drivers.

Alright...one more help question if you don't mind. :)

How do you get the windows to shink to the size of your actual screen?  I obviously need to install a video driver because the only resolution I can select is 640 X 480.

I can't see the entire window so I don't know what my options are at the bottom of the window!  Also--I'm taking these pictures on a 19" Samsung LCD, which is hooked up via DVI cable.  However, in the top left corner of the screen, as you'll see, it says Samsung 50".  That's my big screen dlp tv that I have hooked up via the HDMI cable coming out of the ATI 4350 that I recently put in the machine.

[IMG]http://files.getdropbox.com/u/746243/Ubuntu%20Error5.jpg[/IMG]

---

### Post by merlinus on 2009-07-29
ATI drivers are often a problem with ubuntu because they no longer support older models.  If you do a forum search, you may find a way to install the correct one via a CLI.

Or post a new thread in the multimedia forum.

---

### Post by stealthbt on 2009-07-29
> **merlinus said:**
> ATI drivers are often a problem with ubuntu because they no longer support older models.  If you do a forum search, you may find a way to install the correct one via a CLI.

Or post a new thread in the multimedia forum.
First I gotta go figure out what a CLI is! haha

I downloaded the linux driver files from ati's website which says it works in ubuntu but when I double click the .run file....it won't run.  What program do you open .run files with?

I will go post about the display driver stuff in the multimedia forum.  If you could answer the question about the .run files I promise I won't bug you anymore!

Thanks again for all your help!

---

### Post by merlinus on 2009-07-29
CLI = command line interface.  The terminal is one example.

Installing a downloaded video driver using run can be complicated -- more than one command is involved, and sometimes even adding a kernel patch.

I think you can get better assistance in the multimedia forum than I can offer for your video card and monitor.

If not, then post back.

---

### Post by iain_thornton on 2009-07-30
similar problem here but I can boot from NO boot CD for some reason.I've tried 6 or 7 known good boot CDs (Windows XP, Vista.....partition managing software...Ubuntu...everything) but whatever I put in it goes straight to that page!
anyone have any ideas?
computer is an HP Compaq NX7400
sorry for hijacking thread but this seems similar!

---

