---
title: "shrinking a partition?"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by bilmas on 2009-02-18
i got the ubuntu disc and i have been running the live session and i love what i see
as tempted as i am to make the switch instantly from windows i would like to run both at first but each time i try to install it on a second partition the install says i only have 8 mb  with which to do so

i defragmented the drive and tried shriking the partition separately in gparted but no luck

any ideas of what might work?

---

### Post by Partyboi2 on 2009-02-19
If you are using Vista then use the resize tool in vista to shrink down your vista partition. If you are using xp you should be able to use gparted to shrink down your xp partition. When you say you had no success with gparted what happened?

---

### Post by staf0048 on 2009-02-19
> **Partyboi2 said:**
> If you are using Vista then use the resize tool in vista to shrink down your vista partition.

Careful with this.  When I was trying to get Ubuntu to dual boot with Vista on my laptop I had to do this and it broke the MBR for some reason - not sure why.  So I just installed Ubuntu and have not looked back.

So, my advice if you're just looking to try it out is back-up all your irreplaceable files to USB or DVD (you should do this regardless), then use the entire disk to install Ubuntu.  If you find you don't like it, just re-install windows (if you must).

---

### Post by bilmas on 2009-02-19
i'm using XP
when i run gparted to try to shrink the partition it doesn't give me the option.  it only offers 8 mb worth of play.  most everything i care about is already on an external and i really am considering making the switch completely

just a few questions:
will i still be able to update my ipod?
can i do this without reformatting?
what about a program that backs up dvds like dvdfab?
does miranda run on ubuntu?

---

### Post by staf0048 on 2009-02-19
iPod - yes.  It works on my 2nd Gen Nano with Rhythmbox (default music player), I was even able to copy all the songs I had on the iPod already directly over to Ubuntu without any trouble.  Although my music folder has files name NAOP, QPDL, etc, because of the way the songs are encryped on the iPod, but Rhythmbox can read them just fine.  I"m sure there's an easy way to fix it, but I'm not that picky.  You're mileage may very, so I'd try plugging in your iPod while you're running the live CD - it should recognize it and you can see if it will really work for you.

As for reformatting - I assume you're still talking about the iPod or are you talking about the hard drive?  You will not "need" to reformat the iPod, but you may want to check out RockBox which is an open source alternative to the propietary Apple software.  However, it doesn't work on all iPods as Apple seems to have made that more difficult.  Let me know if you're concerned about your hard drive . . .

Backing up DVD's . . . depends.  If they're not encoded you can easily rip .iso images onto your computer and either keep them there or burn them onto a blank DVD.  If you're talking about ripping hollywood style movies . . . that's a bit touchy.  I will tell you that you can do it (it's not hard), but you're on your own there.

Not sure about Miranda, but Ubuntu does come with Pidgen (at least mine does) that can use many different IM formats.

As a side note, you are supposed to be able to install iTunes for Windows on Ubuntu (which is the strangest thing I ever heard of) with a program called Wine.  You can install it (along with most other programs you'll need) under System, Administration, Synaptic.  Click search and type Wine and you'll find it.  However, I have not tried it.

Hope this helps!!

---

