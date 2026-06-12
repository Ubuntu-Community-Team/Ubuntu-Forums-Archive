---
title: "Cannot install Ubuntu 8.04 (Hardy Heron)"
date: 2008-08-17
forum: General Help
---

### Post by bladefinor on 2008-08-17
Hi!
I downloaded Ubuntu 8.04 LTS Desktop Edition ISO, and burned it to a DVD. I got an autostart for the burned DVD and I installed Ubuntu (from Windows XP) with Wubi. Then I had to restart my computer, and then run Ubuntu from boot loader. I did so and then got this message:
> Warning: Unrecognized partition table for drive 80. Please rebiuld it using a Microsoft-compatible FDISK tool(err=114). Current C/H/S-16383/16/63
Press 'ESC' to enter the menu... [Countdown from 2 seconds]
I let it do the countdown and the UBUNTU startup is loading. After its loading, I got this message:
> Loading, please wait...
Linux ubuntu 2.6.24-16-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686

The programs included with the Ubuntu system are free software:
the exact distrubtion terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ [It wants me to type something here (like commands)]
The only thing I can do here is to type commands. And in guides and videos for how to install this Ubuntu does not show this message, so I think something is wrong...

This happens when trying to install from DVD from boot (without Windows XP) too. And when I'm trying to try Ubuntu from Live CD, it checks if things are OK and then nothing happens... Something is wrong, and what's the problem?
I really appreciating some help :)

---

### Post by cooke77 on 2008-08-18
ubuntu@ubuntu:~$ [It wants me to type something here (like commands)] 

When this last part appeares,you typed in what?
The whole message is equivalent.....to Windows EULA.
You didn't have to type a thing in......when that last line appears.(That's why there NO 'instructions'...here......on what to do NEXT.)
Read the next bit.........very very very carefuly!
You are just a minute or two away, from finishing the Installation process.
Sure, the screen will go blank...beyond this point.....for about another minute or two.....then, the OS begins to LOAD (proper).

The reason why you are having trouble, with yours, is that....you are too impatient, didn't give it time to work.
Linux DOES NOT load (at the snap of your fingers)..like Windows.
You have to give it time.
Even when you succeed, it still takes Time, to switch from Windows to Linux. 

And, MORE IMPORTANTLY, make sure that WHERE you are going to put Linux......is MORE than 20 Gigs of 'free space'!
You are definitely going to NEED that space.

---

### Post by bladefinor on 2008-08-18
Thx for the anwser :)

I didn't typed in something... So I just need to wait?

**EDIT:** I've been in this situation in 1 hour now. I doesn't doing anything. It just want me to type something :S

---

### Post by minhmeoke on 2008-08-19
Does this only happen after installation, or are there problems when you try to use the liveCD?

If the liveCD works, but the installation doesn't, did you run out of hard-drive space? Check if you have a graphical environment by entering the following command:
```
sudo apt-get install ubuntu-desktop
```
It should either install the graphical environment, or say something like
"ubuntu-desktop is already the newest version."

Now try starting the environment with
```
sudo gdm
```

If you are lucky, then a login window should appear; if not, then it will dump you back into the console. In the second case, there is probably a configuration problem with your graphics adapter. Search for the manufacturer and model of your video card (for example: Nvidia Geforce 6200) in the forums, and there should be a howto that will fix the problems.

---

### Post by benhur99ph on 2008-08-20
It's working, its just that it doesn't load the graphical environment. Follow what minhmeoke said. Or you could try a reinstall. You installed it via wubi so uninstalling and reinstalling shouldn't be a problem.

---

### Post by bladefinor on 2008-08-20
well... i have problems to use liveCD too. I can't go to the demo of ubuntu, something fails...

And I do have enough with space (30GB). And that should be enough.

You may help me out of this problem, but i have decided to cancel my dream to get it installed. I just wondered how it looked and I got it to work by using VMWare...
BUT THANKS ANYWAY! :D

---

### Post by jimmyhacker on 2008-08-21
just press esc and go to live cd demo(read-only):):)and when you want to shutdown give a hard shutdown.:S

---

