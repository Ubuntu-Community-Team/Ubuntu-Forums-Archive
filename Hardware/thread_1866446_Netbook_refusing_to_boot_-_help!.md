---
title: "Netbook refusing to boot - help!"
date: 2011-10-21
forum: Hardware
---

### Post by interacter on 2011-10-21
Hi all

Have got an Acer Aspire One that had Jolicloud on it.  I upgraded to Ubuntu 11.04 happily enough.

Then it died when 11.10 was released.  Just refused to boot into 11.10.  No idea why.

Not a problem, I thought. 11.10 probably a but heavy, so I'll go back to Jolicloud.

Installed Jolicloud.  Wouldn't boot.  Just stayed on a black screen.

Tried to reinstall, wouldn't get past the Pick A Timezone splash.

Hey ho.  So I thought I'd try Mint.  Note - each reinstall came with a reformatting of the hard-drive (never been a problem in the past).

Now Mint won't boot.  Just leaves a black screen.

Each install has just about worked on the "Try Me" option from the USB key, but no more.

Any ideas?  I can't see why the Netbook would be refusing to boot anything...

Help!

---

### Post by 2F4U on 2011-10-21
Are you saying that running the respective liveCD of those distributions works, while once they are installed, the netbook doesn't boot?
Can you get to a console while the netbook boots (Ctrl-Alt-F1)?

---

### Post by interacter on 2011-10-21
I'll try the Ctrl+Alt later - running a memory test.

Yes, the Try Me option from USB works (or seems to) but as for an actual install, no joy :(

---

### Post by interacter on 2011-10-22
Morning!

Tried Ctrl-Alt-F1 - nothing.  Just the same black screen with a cursor top let (which doesn't do anything if you try to type)...

N

---

### Post by goldshirt9 on 2011-10-22
have you tried the memory test the live o/s comes with 
has your bios changed by chance.
mine had the option of 
xp / vista
other.
if i tried to run linux under xp/vista , it wouldn't work .
should be found in the bios set up .if it is a problem

---

### Post by interacter on 2011-10-22
Hiya

BIOS settings don't give me the open - just which physical device to boot from.

Just tried again with Jolicloud - gets to the end and says that it can't configure the Grub and that I would have to manually install a bootloader.

What does that mean?

---

### Post by interacter on 2011-10-22
I've restarted at the end of the failed installation and have got the following:

GNU GRUB version 1.98-2jolicloud5

Minimal BASH-like line editting is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible device or file completions.

grub>_




What's that all about? what should I do?

Thanks

---

### Post by interacter on 2011-10-22
Hi all

Quick update: managed to get the netbook to boot using the Try Joliclould option.

While I was in, had a look around the system and the partition for the file system didn't look quite right.  So I told it to reformat the HDD using FAT encoding.  Out of the 16gb I gave it 15g for HDD storage and 1132mb for Swap (seems like a reasonable split).

With that done, then reinstalled the Joli OS.  It restarted once, asked me for a password to access the system, then started complaining that something had crashed.  

Clicked the "Learn more" link and it quite happily loaded Chromium and toodled around the web. 

So I figured it could be a networking issue, so got the netbook to restart.

Trouble is, all that it's doing now is displaying the Joli OS splash (with the scrolling clouds) but getting no further.

I'm pretty much fresh out of ideas.  It's obvious something isn't right - could it be swap partition size?  If anyone has any great ideas, please could you let me know?

Thanks!
Neil

---

### Post by masgeeks on 2011-10-22
Did you try wiping the drive clean...???  When I do a clean install I totally wipe the drive before I even try to install new OS... I use partedmagic easy to use and fast - loads to  RAM...

---

### Post by interacter on 2011-10-22
Hey Masgeeks

Yeah, each time I've used the installer's option to erase the entire drive and start again.

This time, I'm going for 13gb storage and 3.8gb as the swap area.  See if that makes a difference...

---

### Post by interacter on 2011-10-23
Hi y'all

Bit of an update - got into Jolicloud via the USB and ran various commands in terminal (given to me to fix a broken 11.10 desktop upgrade - exciting things like apt get, install, mount and so on.  ).

Lots of different packages updated/graded, which is good.  Speed is also improved.

HOWEVER... (You knew there would be a 'but')

I can run everything perfectly fine after logging into the local machine as a guest.  Network's good, documents open and so on.

However, if I try to log in with my username/password, all I get is a black screen that goes nowhere.

I feel comfortable that I've established the netbook isn't completely dead (because I can run everything OK as a guest), so that's a start.

But if you could suggest something to help with this last problem, I would be really grateful!

Neil

---

