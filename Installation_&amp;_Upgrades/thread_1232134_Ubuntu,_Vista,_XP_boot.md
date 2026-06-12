---
title: "Ubuntu, Vista, XP boot"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by prickee on 2009-08-05
I have a 500G HD and I have all three installed.  I primarily use Ubuntu of course and my lady uses windows.  My question is I want to re-install XP and she wants win 7 over vista.  Can I do this without messing up my linux partition?  I know windows bootloader is agressive so I'm wondering if it will mess with grub.  thanks in advance

---

### Post by presence1960 on 2009-08-05
go ahead and install windows to the windows partitions. This will overwrite GRUB on MBR only with windows bootloader. Your Ubuntu install will still be intact. After installing and checking that windows will boot you will need to do this to restore GRUB to MBR:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

In #6 use setup (hd0) to install GRUB to MBR. This is assuming windows & Ubuntu are installed on hd0.

P.S. If you run into problems getting it going boot from Ubuntu Live CD and when the desktop loads download the [Boot Info Script 0.32]("http://sourceforge.net/projects/bootinfoscript/") to the desktop. Then open a terminal and run this command > sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file on the desktop. paste the entire contents of that file back here. this will show info on your setup & boot process.

---

### Post by Mark Phelps on 2009-08-05
> **prickee said:**
>  ... and she wants win 7 over vista ... 

Sorry if I'm telling you something you already know ... but you do realize that Seven is only available publicly as a Release Candidate (RC), that this is a pre-release version and not finalized yet, that it is NOT upgradable to the final (released version), and that it will expire early in 2010.

So, basically, you'll be replacing a long-term OS with a time-limited, functionality-limited "beta" -- yeah, I know an RC is not strictly the same as a "beta", but you get my point.

You sure that's what you want to do?

And, if you don't believe me about the no-upgrade part, just Google on any of the recent MS announcements about upgrade paths for Seven and read the part where they include the Beta and RC as "not supported".

---

### Post by presence1960 on 2009-08-05
> **Mark Phelps said:**
> Sorry if I'm telling you something you already know ... but you do realize that Seven is only available publicly as a Release Candidate (RC), that this is a pre-release version and not finalized yet, that it is NOT upgradable to the final (released version), and that it will expire early in 2010.

So, basically, you'll be replacing a long-term OS with a time-limited, functionality-limited "beta" -- yeah, I know an RC is not strictly the same as a "beta", but you get my point.

You sure that's what you want to do?

And, if you don't believe me about the no-upgrade part, just Google on any of the recent MS announcements about upgrade paths for Seven and read the part where they include the Beta and RC as "not supported".

I hear you Mark. I am running 7 RC not because I intend on using the final version, but to keep my knowledge up to date on Windows as I do a lot of work for people and unfortunately (LOL) they mostly all use windows. When the RC functionality ends on June 2010 I will reinstall XP to the 7 RC partition. Unfortunately I still need windows once or twice a month for work. I may be getting laid off this month, if I do I won't need windows anymore after the 7 RC experiment.

But I don't think that will be a problem for them as they can remove win 7 when the trial is up and continue to use XP. I have never had more than one version of windows on my machine at a time (even one is too much IMO) but I would think XP would be fine after removing win 7. In the worst case maybe have to restore XP bootloader and then restore GRUB.

---

### Post by prickee on 2009-08-06
Hmmm I didn't know that about Win 7 RC. Well I'll just re-install Vista.  The thing with fresh win install is it takes like 1/2 a day to trim the fat so it operates with any kind of consistency lol

---

