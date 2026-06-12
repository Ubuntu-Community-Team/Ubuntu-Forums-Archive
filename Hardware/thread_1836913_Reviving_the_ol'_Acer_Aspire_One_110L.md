---
title: "Reviving the ol' Acer Aspire One 110L"
date: 2011-08-31
forum: Hardware
---

### Post by squashpup on 2011-08-31
If someone else has posted this before, please forgive me, but there are questions in this thread that I'd like to have help with!

I love the convenience and portability of my old Acer Aspire 110L, plus with no moving parts, it's as rugged as they come.  I dropped a solid wood window shelf on mine accidentally.  Cracked the LCD and bent the USB plug on my wireless mouse, but didn't even cause the computer to shut down.  A replacement on eBay for $60 or so and I was back up and running.  Then, I dropped it (in it's case) on a paved parking lot with no damage.  It has always been my faithful companion, and you couldn't pry it out of my fingers even if you promised me an iPad. 

One area that I've never been satisfied with was the performance of the SSD.  It REALLY diminishes the enjoyment of using the little netbook. I bought an ultra-small jump drive and tried to run off of that, but keeping casper-rw from filling up was too much of a headache.  

What I really wanted to do was to replace the SSD with a real hard drive, but after reading about the procedure, I decided to relegate that to being my last-ditch effort.  Instead, I decided to focus my efforts on the SD card slot and put the operating system there.

The major hurdle I had to overcome was the fact that the 110 won't boot from the SD.  So, I decided to try to experiment a little. I got an 8GB class 6 MicroSD card in a full size SD adapter.  Since the card slot on the right can read a variety of formats, and I wanted to keep that open, I put the card in the left slot.  

I booted into Ubuntu via a USB drive and opened up Gparted.  I started with the 16 GB SSD that is built into the 110 and partitioned it with a 1 gb partition at the beginning, and the rest of it a 15 GB partition, both ext2.  I also formatted my MicroSD card as ext2. Then, I started the installation.  

When it offered the choice to install on the built in hard drive or to do something else, I chose "something else". Then I started making the assignments.  SDA1, the 1 GB partition, was to be /boot.  SDA2 was to be home.  mmcblk0, the MicroSD card, was to be /. It was not necessary to add a swap, but when I confirmed the above choices, the installer encouraged me to go back and create one.

Following my strict policy of ignoring anything that might be good advice, I proceeded without a swap.  The installation went off without a hitch and I was prompted to reboot.  

After the BIOS screen, I got some sinister looking GRUB messages.  I don't know whether or not they were a result of my unorthodox installation, or it was some other error, but it displayed these error messages for a few seconds and then proceeded to boot to the login screen.  

Logged in and I was looking at the Ubuntu desktop!  This is FULL Ubuntu Natty, too, with the Unity Desktop in all it's glory!  

I immediately logged out and selected Ubuntu Classic (Gnome) because I hate Unity and logged back in.  Then I ran gconf-editor to put the buttons back on the right side.

That was it.  I was surprised it was this easy and yet it worked.  And WOW, what a difference in performance.  It's not far off my full size HP DV6000 which also runs Natty.  Firefox, which was nearly unusable on the old Acer SSD, runs like a regular HD install from the Class 6 card.  Google Earth even runs just fine. Not perfectly smooth, but every bit as usable as it is on my HP with nVidia graphics. 

So far, the only hitch I've found is that suspend doesn't work correctly.  If I understood a little more about how suspend works, I might know where to start looking for a solution. 

Since I have the 9 cell battery, it's not a big deal to shutdown or reboot, so it's a tradeoff I can live with.  Still, if I could fix it, that would make the whole deal perfect.  

Summary:

Pros:

Not difficult to set up this way.

Inexpensive...an 8GB SD card can be had for under $15 and can be replaced easily.

Your home directory is safe during a reinstall as long as you don't check the "format" option

Speed increase is dramatic

Easy to undo...just remove the card and reformat it, and install Ubuntu to the SSD as before

You gain a giant 15GB home directory and still have 8GB for installing programs...total capacity increases from 16 GB to 24.  

Can be even more space if you're willing to buy a bigger SD card

Not obvious from looking that the 110 isn't running in factory configuration...no USB's sticking out of the side or anything like that. 

Cons:

Might wear the SD card with repeated writes.  Not too big of an issue, especially since your home directory is on a completely different drive, and SD cards are cheap.  You can be back up and running with a completely new SD card in less than an hour, and all your bookmarks and settings will be as you left them. I might experiment and see if I can copy system files from this SD to a different one, just to see if I can make a quick and dirty backup of my system that way.  I imagine you'd have to create an image, which would not be difficult to do, since you could put the SD in another computer and back it up on that hard drive. 

Most obviously, you lose an SD slot.  To be fair, you still have one open.  I can't recall a situation where I ABSOLUTELY needed to plug two SD's into my computer at once.  If I did, I still have a USB card reader I can plug into a USB slot. 

While inconsequential, I've used this method twice, and it does start with error messages on boot each time.  If you like things nice and tidy, you could try to fix it, but it doesn't bother me because it doesn't affect the functioning of the computer that I can tell (unless that's what's messing up the suspend and resume!). 

Suspend and resume doesn't work.  If anyone has any ideas about this, I'd be glad to hear them. Like I said, with the big battery, it's not a dealbreaker, but it would be handy not to go through the shutdown/reboot procedure each time. 

Any suggestions/advice would be greatly appreciated. 

If you have an old Aspire One with an SSD, this method might be worth a try.

---

