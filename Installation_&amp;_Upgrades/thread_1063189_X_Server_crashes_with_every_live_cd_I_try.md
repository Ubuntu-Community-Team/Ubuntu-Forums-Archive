---
title: "X Server crashes with every live cd I try"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by Troop116rules on 2009-02-07
I am trying to install Linux on my desktop. It is already installed on my laptop fine, but this desktop is having a little trouble. I had installed OpenSuSe about 3 years ago on it, and it worked great. Problem is I then found a kernel module for a camera I wanted to use, but with my old skills I sucked at Linux, and I installed it, basically overwriting the kernel. With Linux not working, I booted into XP, and tried to delete the Linux partitions with my partition manager. No luck, cause I rebooted and Grub had that fatal error #15. Ouch.
Well, it's been a while, and I got XP back on the computer, and it's running great. (for XP that is :P) Here's the deal, I want to install Linux again (Fedora or Ubuntu are both fine), but I can't. Every time I boot a live cd using the X.org server, it freezes after it loads. I can't even restart it using CTRL+ALT+Backspace/F1. I've tried multiple discs, including GParted Live. This is ridiculous. I have an nVidia 7800 GT OC. Any tips? I can't give much info, because it crashes every time. I don't want to install using text mode, because I figured an installed X server will do the same thing as the live.
Thanks in advance.

---

### Post by taurus on 2009-02-07
How much RAM does it have?  By the way, don't confuse the alternate CD, text based installer, with the server version.  Even if you use the alternate CD to install Ubuntu on your machine, you still get the full Gnome DE when the installation is done.

---

### Post by avtolle on 2009-02-07
Have you tried installing from the Live CD using Safe Graphics (although, I concur in the suggestion to use the alternate CD to get around the problem with the nVidia card during installation).

---

### Post by Troop116rules on 2009-02-07
I have 2gb of ram, but I will try the safe graphics mode. Thanks. I'll let you know how that goes.
btw, i wasn't trying to confuse CDs. I was just trying to say that I don't want to install, because the X server might still crash after it's installed.

---

### Post by Troop116rules on 2009-02-08
Ok, I believe I found the problem. I wondered if it had to do with my video card, so I took out the card and tried installing using my integrated video. The install ran fine, so I believe that live CDs aren't liking the DVI video connection (which my nVidia requires), as I found in a separate post. Do we have any idea when the X.org developers will try and fix this?

On a side note, I'm going to try to reboot with my new installation, but with my nVidia plugged in. (The card's DVI connection overrides my integrated card, as you should know, so I have to take out the card every time, or I get no video out of the VGA. It stinks that my nVidia doesn't have VGA. Oh well.)

I'll let you know how that goes, although it should work fine.

---

### Post by taurus on 2009-02-08
When you plug in an add-on graphic card, you need to go into the BIOS and turn off the onboard graphic card.  I don't have any problem with my add-on nvidia card with a DVI connection to my 22" LCD monitor.

---

### Post by Troop116rules on 2009-02-08
> **taurus said:**
> When you plug in an add-on graphic card, you need to go into the BIOS and turn off the onboard graphic card.  I don't have any problem with my add-on nvidia card with a DVI connection to my 22" LCD monitor.

lol, I forgot that my friend told me to do that. I'll try that out. (if my bios supports it. Mine's a junky bios compared to what I've seen.)

---

### Post by Troop116rules on 2009-02-08
well, apparently I forgot...what i forgot. ?? What I forget that I tried to turn off that feature in the bios before, but there was no option to do so, same as last time. Apparently that's what I need, too, because I tried to boot my new installation of Fedora up, and it had a IO-APIC error, causing it to freeze at load I presume. So, I added the kernel arg noapic, and it seemed to run fine. Only until I booted the NEXT time did it mess up. Now I can't even get the X server to start up automatically. (I've always hated X, because I can never seem to understand how to start it from the terminal...always get an error telling me to delete a file. I delete it, and try startx command...no luck)

I'd like some help on this.

I'd like to note that this new problem happened after I put my nVidia card back in. I need that card, because like all integrated junk, my integrated sucks! I can take out the nVidia, and it should start up ok, but how can I install the drivers for a card that's not plugged in?
*sigh* I'm tired of computers. Wish they could be more of a breeze, not hours a day of work.

---

### Post by dougalkerr on 2009-02-08
I know you have probably tried this already but... does your motherboard have a jumper to disable the integrated graphics in favour of the add on card?

---

### Post by Troop116rules on 2009-02-08
> **dougalkerr said:**
> I know you have probably tried this already but... does your motherboard have a jumper to disable the integrated graphics in favour of the add on card?

I may sound like an idiot. No I have not tried that. Is there something I should look for? I can find where the integrated card is on the motherboard, but do you have example pics I could look at?

---

