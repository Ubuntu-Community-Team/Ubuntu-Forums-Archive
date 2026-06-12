---
title: "How do I give Windows Vista prime position on the bootloader?"
date: 2008-11-19
forum: General Help
---

### Post by jantar on 2008-11-19
Can someone tell me how I can have Windows Vista in the prime position (before Ubuntu) in the bootloader.
I want it this way until I am fully conversant and happy with this new (to me)Ubuntu Hardy Heron operating system. Once I am happy Bill Gates and his crew of robbers can go the final journey.
Make it easy please!
Regards
jantar

---

### Post by Sub101 on 2008-11-19
Do you mean you want Vista to be the default selection on your grub list?

---

### Post by hardyn on 2008-11-19
[http://ubuntuforums.org/archive/index.php/t-77030.html](http://ubuntuforums.org/archive/index.php/t-77030.html)

This shold help.

I noticed that this was your first post... most of these type of questions have been answered many many many times; try a search before a post :)... and keep the questions coming (after searching) that is what all of us are here for.

---

### Post by jantar on 2008-11-19
Yes, That is just what I want it to do until I get used to Ubuntu. Load first.
Regards
jantar

---

### Post by linux_tech on 2008-11-19
Backup menu.lst-
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

Then edit menu.lst-
```
sudo gedit /boot/grub/menu.lst
```

Scroll down a bit and find the part that says "default 0" and change the "0" to number of the OS you want to default to. Depending how they are listed on GRUB menu, count to where it's located, starting with the number 0 rather than 1.

ie. If the line now reads default 0, (where the first menu item is Ubuntu, and the second item is Vista in your menu.lst file, you should change the line to read default 1 so Grub boots Vista by default.

---

### Post by jantar on 2008-11-20
Hm,
Tyhanks for your assistance but I have tried to do as instructed but I cannot get it to work. All it does is to tell me that the instruction is not recognised.
Presumably I start by selecting the command prompt item at startup in grub and then insert the text you have given.
If not can you guide me through step by step as my old and tired grey cells are not what they used to be.
Regards
jantar

---

### Post by Sub101 on 2008-11-20
So you have attempted to edit the grub file but it didnt work?

How far did you get?

---

### Post by jantar on 2008-11-20
I followed the instructions as given by selecting the 'c' command from the startup page. I then inserted the text as given but it did nothing at all.
aaaargh.
What am I missing?
jantar

---

### Post by Sub101 on 2008-11-20
I suggest you follow linux-techs post. That should work fine.

---

### Post by jantar on 2008-11-20
Thanks, been there and done that but it has no effect.
Am I starting the procedure the right way?
I suppose the place to begin is with the command prompt within grub?
All this is making me wish that I had not bothered with linux and from what I can see in the forums there are many like me. I really do wand rid of microsft at some point but I need Vista to laod first in the meantime.
jantar

---

### Post by pratekin on 2008-11-20
You can try a program called startup manager.  It is a gui that allows you to set which os you want to be default.  You should be able to get to it under add/remove programs.  It will show up under system and then administration.  Hope this helps you.

---

### Post by Sub101 on 2008-11-20
If you have changed the grub file you also need to run:

```
sudo update-grub
```

That may help?

---

### Post by Slim Odds on 2008-11-20
> **jantar said:**
> Thanks, been there and done that but it has no effect.
Am I starting the procedure the right way?
I suppose the place to begin is with the command prompt within grub?
All this is making me wish that I had not bothered with linux and from what I can see in the forums there are many like me. I really do wand rid of microsft at some point but I need Vista to laod first in the meantime.
jantar

Dude, you're making this **WAY** more complicated than it needs to be (or really is).

You don't need to do anything "IN GRUB". Let your system boot into ubuntu and then follow the previous instructions that you were given about *editing your menu.lst file.*

It's in /boot/grub/

It's not as hard as you make it sound.

---

### Post by Slim Odds on 2008-11-20
> **Sub101 said:**
> If you have changed the grub file you also need to run:

```
sudo update-grub
```That may help?

No need to do this. GRUB reads the menu.list file (from /boot/grub/) everytime it boots. This is one of the biggest advantage of GRUB over LILO. With LILO, every time you change your config you need to rewrite the boot sector. Not so with GRUB.

---

### Post by tom66 on 2008-11-20
I think he is getting confused between the GRUB prompt and the Linux command line/terminal. What you need to do is first go into Ubuntu then open the terminal and run the commands that the other posters have suggested. After that you need to reboot to see your changes.

---

### Post by Sub101 on 2008-11-20
> **Slim Odds said:**
> No need to do this. GRUB reads the menu.list file (from /boot/grub/) everytime it boots. This is one of the biggest advantage of GRUB over LILO. With LILO, every time you change your config you need to rewrite the boot sector. Not so with GRUB.

Oh? What is the function of the update-grub command then? 

I thought that it was required. Even the startup-manager runs it on shutdown does it not?

---

### Post by pratekin on 2008-11-20
Startup manager does do that, but it is automatic.  It is a much easier interface for someone new to linux than messing with their grub and potentially harming the way their computer boots.

---

### Post by Slim Odds on 2008-11-20
> **Sub101 said:**
> Oh? What is the function of the update-grub command then? 

I thought that it was required. Even the startup-manager runs it on shutdown does it not?

update-grub scans the /boot directory looking for kernels.... etc.

That's not any help.

He needs to manually edit his /boot/grub/menu.lst to select which item he wants to be the default.

---

### Post by CholericKoala on 2008-11-20
This won't be the popular solution but it will work.

Go into vista, install EasyBCD, add your partitions, click on "write bootloader" and you're done.

---

### Post by Slim Odds on 2008-11-20
jantar:  you might also want to install one of the GUI grub config tools. I don't remember the names. Look in the application add/remove

---

