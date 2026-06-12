---
title: "Does GRUB replace MBR or tweak it?"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2009-06-08
I want to replace the 240GB 5400 rpm drive in a laptop with a new 320GB 7200 rpm drive.  The original drive is a typical Vista/Ubuntu dual boot.  The so-called plan is to transfer Vista but install 9.10 in order to replace 8.04.

I used GParted LiveCD and a Vantec NextStar dock to copy/paste the Vista partition to the new drive.  GParted reported that the task was completed successfully.

I haven't unbolted the original HDD from the laptop and popped in the new one, but I'm sure Vista won't boot because GRUB did its thing to create the original dual boot and there's only Vista on the new drive.  Pretty sure I can fix the MBR but thinking about just moving on to the Ubuntu install instead.

So, here's the question: if I install Ubuntu to the free space on the new HDD, and let GRUB install to the default "hd0", does GRUB need to see the original Windows MBR?  Or will it just rewrite the existing GRUB and everything should work?

---

### Post by dandnsmith on 2009-06-08
GRUB doesn't need to see the original MBR, but you will have had a problem trying to transfer Vista with gparted because of the way Vista boots.
If you had transferred XP, then you could expect to make it work.

Have a look at [this site](http://www.multibooters.co.uk), to get a feel for the problem. Then decide what you can try next.

---

### Post by Keith Hedger on 2009-06-08
As I understand it grub will rewrite the MBR completely.

---

### Post by sendblink23 on 2009-06-08
Just wondering in the first post of the thread you mentioned 9.10 ...  where did you get it? All I see around available is 9.04

---

### Post by Bartender on 2009-06-08
Well, I tuned up the flux core capacitor, slapped some new tires on the DeLorean, and got the jump on you guys.  I could tell you some of the new features included in 9.10, but Doc Brown says I gotta keep my mouth shut.

Or it could be that I goofed up.

Urgh, I'm on dial-up but will try to find the info on that link regarding Vista multi-booting problems.  You're saying that what I described won't work?

---

### Post by NilsE on 2009-06-08
> **Keith Hedger said:**
> As I understand it grub will rewrite the MBR completely.

Definitely...

It bit me once since my XP drive is encrypted with WinMagic and is dependent on the MBR to trigger the WinMagic logon before the Windows boot.  It re-wrote the MBR and I could not boot XP.  Had to rebuild the MBR with the WinMagic recovery to get it working again.  Until WinMagic comes out with a Linux version I have to remove the XP disk every time I do a clean install of Ubuntu so it does not get me again. I just use the BIOS boot options to select which I want to boot into.  I have it set to default to Ubuntu and need to hit F12 to select XP drive when at work.

---

### Post by dandnsmith on 2009-06-08
> **Bartender said:**
>  You're saying that what I described won't work?

That's about the size of it - nothing to do with GRUB installation, mostly the difficulty of moving Vista to a new environment.

---

