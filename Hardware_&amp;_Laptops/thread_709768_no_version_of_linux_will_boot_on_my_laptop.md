---
title: "no version of linux will boot on my laptop"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by craftsmenerock on 2008-02-27
Hello, i recently jumped into the Linux world.  I have ubuntu 7.10 on a Dell pent 4 @ 1.7ghz with 1 gig mem ram.  After an Amarok install to listen to mp3's, its an awesome desktop machine to surf the web and use open office.org for various spreadsheets.  I love it so much, I need a portable machine like a laptop to take into the field to enter data and then bring back to the office.  I have a free IBM 600 thinkpad.  I think its a 300 mhz processor with 128 mb ram. 2GB hard drive.  I did lots of reading about version requirements, and then started downloading and burning cd's.  I have yet to get a version booted.  I have entered BIOS and set to boot from cd-rom.  1 version gave the hard drive and cd rom a work out for 21 hours with a blank screen.  At this point I have puppy linux, Xubuntu, damn small linux, and ubuntu live cd's.  I am heading to IBM web site to see about a BIOS upgarde after posting this.  If I hadn't fallin in love with ubuntu, I would give up and keep the stinking win98 on it.  If no Linux, its going back in the stack in the closet, and I'll carry my number 2 lead pencil and clip board.  Please help me!  I live in Kansas and wind blows the sheets from my clipboard! Thankx in advance.

---

### Post by Sef on 2008-02-28
1) Have you md5summed the downloads?

2) Did you burn the iso at 4x or less?  

3) Have you downloaded a GNU/Linux version made for older laptops?

---

### Post by craftsmenerock on 2008-02-28
Yes, I burned the discs with the NTI software a 4x.  I tested my boot cd's on a newer machine to make sure they boot, and they do.  Its my understanding that DSL, Puppy, and Xubuntu are the versions used on older laptops.  Xubuntu boots from the CD and brings up Xubuntu screen with the progress indicator for some time, then goes into a dark screen with hard drive and cd rom activity.  I let it do this for 21 hours and gave up.  I am going to try the Xubuntu boot cd again and post any and all messages I get along the way.  Thankx

---

### Post by Circus-Killer on 2008-02-28
when you are booting from the live cd, the first thing you should be presented with is a menu with several options. one of them is to "start or install ubuntu", the one right underneath that option is something like "start in safe graphics mode".

first try boot in "safe graphics mode".

if that doesn't work, try restart and go to the boot menu. go down to the "safe graphics mode option" so that it is highlighted, but dont press enter to start the boot. first push F6. that will bring up a line of code which starts the kernel. at the end of the line, just before the "--" you can try add "noapic irqpoll noirqdebug" to that line. press enter and try booting.

if this solution works, remember that straight after the install, you will need to do a smilar thing when your machine reboots. that is, when it comes up with grub, you push esc. and edit the second line of the grub thingum.

once you fully boot into your newly installed system, you can go edit /boot/grub/menu.lst and add those commands to the kernel line. just remember that whenever you update the kernel or some part there-of, you will need to redo the editing of the grub menu as just mentioned.

good luck.

---

### Post by craftsmenerock on 2008-02-28
ok circus-killer, i am presented with the menu.  after trying safe grahics mode: this message appears on the screen
[0.000000] ACPI: BIOS age (1998) fails cutoff (2000) acpi=force is required to enable acpi.
then this goes on to something else like:
setting primary keymap    OK
preparing restricted drivers     OK
starting basic networking    OK
starting kernel event manager    OK
loading hardware drivers     OK

and on and on and on and on

saving VESA state     OK
start hardware abstraction layer hold      OK

then nice blue screen with mouse pointer and i can move it around on the screen

goes on for hours and hours with hard drive activity and cd rom activity for hours and hours and hours.

I did the F6 with safe graphics mode highlighted and added the additional code and then enter.  Get the nice blue screen again with mose pointer on screen and can move it around.

hard drive and cdrom are pounding away.  I will let this run for an hour or two and see what happens.  I think the key to the problem may be in that ACPI BIOS age, fails cutoff, force is required to enable acpi statement.

If that is a clue of what I need to do, I thank you in advance for your time and effort to help me.

---

### Post by Circus-Killer on 2008-02-29
hmmm.....
must say, i havent the foggiest. i only suggested what i suggested because it was what worked for me and many others when our laptops wouldn't boot. but if what i suggested didnt work, then i dont know what else to suggest.

---

### Post by SeaQiyas on 2008-02-29
I am new to the linux world too, and had all sorts of problems getting things going. 

What others suggested, which DID help in my case:

-Ck the md5sums. My first 2 downloads were no good.

- Burn the CDs to a HIGH QUALITY CD-R (CD-RW not as good) at slow speed.

- Run the "CD integrity test" to see if there was any corruption while burning. I found corrupted files in all 4 copies I burned, until I went out & bought better quality CD-Rs.  After that the first burn was fine, passed the integrity test, and loaded easily. (I also spent hours & hours stuck trying to install... the install on the "good" CD took about an hour.)

Try using any available alternative CDs available.  For Ubuntu, I could not install with the Live CD bc I only have 256MB ram on my laptop.  So I ended up downloading the alternative CD for Ubuntu 7.10 instead.

I loaded Puppy Linux on the laptop while waiting to get some good CD-Rs, and it loaded easily.  And the internet surfing was FAST on there, I couldn't believe it for such a slow machine!

I hope you get your problems resolved.

---

### Post by eriqjaffe on 2008-02-29
SeaQiyas is right on about the alternate CDs, especially with only 128mb of RAM.

You may also consider doing a command-line install and building from the ground up.  It's what I did with my old, similar-spec laptop.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

The 2gb drive is going to be the other big sticking point, that's not a lot of space.

---

### Post by craftsmenerock on 2008-03-10
I have given up on the ol'thinkpad for now and went back to enjoying my desktop install which works like a dream. Fighting wireless network cards now.  Thanks for all the help! I really enjoy the Ubuntu Forums, and the Linux experience.  Thanks

---

