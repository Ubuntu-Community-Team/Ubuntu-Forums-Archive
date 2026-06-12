---
title: "Very complicated booting problem"
date: 2008-10-19
forum: General Help
---

### Post by Shockz on 2008-10-19
Please bear with me a bit; this is going to take a while to explain.

One of my RAM sticks (2x 1GB OCZ Platinum PC2-6400) is bad. I'm not sure exactly what's wrong with it, but it runs slightly underclocked, and it requires a CMOS clear every time I reboot. (This would be much more irritating if my mobo--Abit IP35 Pro--didn't have an easy CMOS clear switch on the back panel.) However, it otherwise works fine, and since the warranty was long expired by the time I figured out what was wrong with it (and I'm currently too broke to replace it), I use it anyway--having 2 gigs of RAM is worth the occasional glitch.

Fast forward about a year to today, when I decide to install Ubuntu on my second hard drive. (I have XP Pro on my primary drive.) I remove the Cursed RAM Stick, because I know I'm going to have to do a lot of rebooting. I run the Ubuntu Live CD, then find out, to my horror, that the installer can't find either hard drive. A little googling reveals that some people with a similar problem have solved it by going into the BIOS and changing the SATA mode from "IDE" to "AHCI". Now, I have no idea whatsoever what that actually does, but I try it anyway, and lo and behold--Ubuntu picks up the drives, installs perfectly, and even imports my sweet-*** Evangelion wallpaper from Windows. After a couple reboots to test whether the bootloader is working, I put the Cursed RAM Stick back in, clear the CMOS (resetting the BIOS to default settings), and reboot again.

Oops.

Ubuntu proceeds to get stuck on the initial loading screen, bouncing the little loading bar back and forth for about ten minutes or so before I get fed up with it. I take the Cursed RAM stick back out, go back into the BIOS, and change the SATA mode to AHCI again; Ubuntu loads perfectly this time, and that's where I am now.

Now that I've provided all the backstory, here's the actual question: If I'm using the Cursed RAM Stick, I'm going to have to depend solely on default BIOS settings--which means SATA mode is set permanently to IDE instead of AHCI. (Again, I don't have the faintest idea what that actually means.) So is there any way to get Ubuntu to work with this, or should I just go back to Windows and/or trash the Cursed Stick?

Many thanks if anyone can help me out on this.

---

### Post by Dayo6 on 2008-10-19
I guess it would depend on your wealth.  If you are super rich, ditch the stick.  If not, go back to XP.

Those are what I think you should do... But then again I'm pretty nooby to this kind of stuffs.

---

### Post by bodhi.zazen on 2008-10-19
Well, 1 Gb RAM should be more then enough for the average Ubuntu user. Ubuntu does not use RAM the same way as Windows nor does it need as much to run efficiently.

I would use 2 Gb when booting windows and 1 gb when booting Ubuntu.

---

### Post by Shockz on 2008-10-19
> **bodhi.zazen said:**
> Well, 1 Gb RAM should be more then enough for the average Ubuntu user. Ubuntu does not use RAM the same way as Windows nor does it need as much to run efficiently.

I would use 2 Gb when booting windows and 1 gb when booting Ubuntu.

Might work. Except I can't really think of a good place to store the Cursed Stick when I'm not using it...Still, I'd really like to know if there's any way to get Ubuntu to boot with SATA in IDE mode (again, whatever that actually means).

---

### Post by bodhi.zazen on 2008-10-19
> **Dayo6 said:**
> If you are super rich, ditch the stick.  If not, go back to XP.

Well, although I do not know the exact RAM, 1 Gb RAM can go for $25 or less these days and I would not qualify that as "super rich".

---

