---
title: "Removing Grub completely"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by Sojurner on 2009-04-09
Well yesterday i install 2 new video cards. When i installed linux after having some issues it booted up after the initial install and looked fine.

Now when i reboot and use Grub t select it loads like its supposed to but X never loads up. after the initial load screen it goes to text and drops to a login prompt.

Also it wont load the windows installation that i have.

I have seen a dozen or more threads on how to intall grub but none on how to completely remove it. 

Thats what i want to know how to do. I need to remove it totally from everywhere so i can do a clean reinstall of ubuntu and install it fresh with no problems..

---

### Post by dandnsmith on 2009-04-09
You need to use the recovery console to do 'fixmbr' - assuming it's XP you have.
That will re-instate the Windows boot primitive in the MBR, and get you back to the XP boot sequence.

---

### Post by Sojurner on 2009-04-09
yea i tried that. but i had to end up changing the boot order of my drives for it to take effect (well thats what it took for me to get it to boot straight into xp)

i had to change my boot order some time back becuase of grub error 17. so since this is now my first boot hard drive should i try re installing linux now?

---

### Post by dandnsmith on 2009-04-09
If you had, earlier, to change the boot order, then you should have changed it back before doing the fixmbr (as, indeed, you found)
If you tried the fixmbr on the wrong drive, I assume that you wiped the grub primitive boot code from that drive too.

Yes, you can carry on to do the install, but you may, once again run into trouble, depending on what exactly you do - you know one way of getting it wrong, so you can either go ahead and try it, or post a plan, and we'll comment on whether it looks 'good'

---

### Post by Sojurner on 2009-04-09
well im gonna go ahead and just do a fresh install of ubuntu on the drives that i have set aside for it and let it default install the boot loader. If i run into problems i can always get past grub with my windows cd and post my problem.. 

so i will be updating in this thread.

---

### Post by dandnsmith on 2009-04-09
Right - good luck

---

### Post by Sojurner on 2009-04-09
well i have installed ubuntu again and it loads into it with no problem. However. I have yet to install the drivers which i am doin in jut a minute after the update finishes.

Everytime i do this when ubuntu restarts. X Fails to load and i have no idea how to recover it. It just crashes to a login prompt.

I know i am using the right drivers because its the ones that the hardware manager in ubuntu reccomends. I am using the 180 nvidia drivers with my dual 9800GTX+'s

I fear that the next time i read this thread or respond ill be doing it from inside windows.

---

