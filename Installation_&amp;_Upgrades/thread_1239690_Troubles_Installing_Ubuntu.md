---
title: "Troubles Installing Ubuntu"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by BananasInPajamas on 2009-08-13
I am using an older Windows XP Professional. I burned LinuxMint onto a disk and when I try to boot it, it takes me to a screen that says:

GRUB4DOS O.4.4 2009-04-21, MEMORY:640K/765M, MENU END: 0x43456 [Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completion. Anywhere else TAB lists the possible completions of a device/filename. ESC at any time exits.]


I burned two different disks and they do the same, so I don't know if there is something I just need to do at this screen?

Edit: Same problem with other versions.

**--Additional Problems--**
I got mint to install on my other computer, but when I try logging on I get a black screen.

And now on my older comp, I cant log onto my Windows XP account anymore. It gives me an error (Auto Check can't be found and so the comp constantly restarts.)

---

### Post by BananasInPajamas on 2009-08-13
No one has seen anything like this, or has a solution?

---

### Post by hansdown on 2009-08-13
Hi BananasInPajamas.



Did you by any chance download the server version of mint?

---

### Post by BananasInPajamas on 2009-08-13
I got it from the LinuxMint site

would I need to do anything with that Grub thing to fix it, or would the ISO's im burning end up corrupting?

---

### Post by hansdown on 2009-08-13
Not to add to your frustration, but I would download a new one from here.

[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

Make sure you burn it at the slowest possible speed. Hope this helps.

---

### Post by BananasInPajamas on 2009-08-13
I'll try it, I only have 2 disks left though.

---

### Post by BananasInPajamas on 2009-08-13
Got the same thing, takes me to GRUB and idk what to do there

---

### Post by hansdown on 2009-08-13
I've never encountered that, and when I googled it, the only link is your thread. 

Ummm, sorry?

*slinks away*

*comes back filled with renewed strength*

I have had trouble installing some distros, when other ones load great.

Are you looking for mint because of the extras?

I can help with the multi-media things if you would like to install ubuntu 9.04.

---

### Post by BananasInPajamas on 2009-08-13
I got mint to install on my other computer with Windows Vista, but when I restart and try logging on, the screen turns black :(

And now on my older comp, I cant log onto my Windows XP account anymore.

---

### Post by presence1960 on 2009-08-13
what graphics card do you have? If you have an ATI or Nvidia  at GRUB boot into recovery mode and choose command prompt with networking. Log in and run this command ```
envyng -t
``` make sure your num lock is on and follow the prompts. This will install your driver for your ATI or Nvidia card.

---

### Post by BananasInPajamas on 2009-08-14
My friend told me the reason is because my comp is AMD(?) not Intel. So I needed a different version of Mint. I tried x64 and when I tried booting it, I didn't have enough disk space and I couldn't get to the login screen, then when I REBOOTED, I got to the login screen but my mouse and keyboard stopped working.

---

### Post by presence1960 on 2009-08-14
> **BananasInPajamas said:**
> My friend told me the reason is because my comp is AMD(?) not Intel. So I needed a different version of Mint. I tried x64 and when I tried booting it, I didn't have enough disk space and I couldn't get to the login screen, then when I REBOOTED, I got to the login screen but my mouse and keyboard stopped working.

Sorry to say but your friend is incorrect. 32 bit and 64 bit Mint work on both Intel & AMD CPUs. 64 bit is labeled AMD64 basically because AMD was first to implement it, but it does work on Intel 64 bit CPUs.

---

### Post by BananasInPajamas on 2009-08-14
So that wasn't my problem, and now I have 2 different Linux versions on my comp lol. One that goes to a black screen and one that freezes at login.

---

### Post by presence1960 on 2009-08-14
I would get rid of one of those Linux partitions and reinstall. Go [here]("https://help.ubuntu.com/community/BootOptions") for boot options. you may want to look at one or more of the top 3 options for F6

---

### Post by BananasInPajamas on 2009-08-14
By the way, my graphics card is Nvidia, I tried that code you gave me, I did the recommended settings, and the Main Edition still gives me a black screen.

---

### Post by presence1960 on 2009-08-14
> **BananasInPajamas said:**
> By the way, my graphics card is Nvidia, I tried that code you gave me, I did the recommended settings, and the Main Edition still gives me a black screen.

check out the link in post #14

---

### Post by BananasInPajamas on 2009-08-14
I can't press F6 at the menu, and which partition am I to delete from the list? It reads:

[B]Partition     |   File System 
[/B]/dev/sda1        ntfs                
/dev/sda2       extended
   /dev/sda7    ext3
   /dev/sda8    linux-swap
   /dev/sda5    ext3
   /dev/sda6    linuxswap
/dev/sda3      ntfs

---

### Post by BananasInPajamas on 2009-08-14
I deleted x64, so scrap that one.

---

