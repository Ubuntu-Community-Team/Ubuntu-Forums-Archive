---
title: "Freezing on boot after Karmic upgrade"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by 68pontiac on 2009-10-31
I'm not super-new to Ubuntu (been using a couple years) but I'm not necessarily a power user. I upgraded from Jaunty to Karmic this morning via network and everything seemed happy and fine. On restart I got past bios, GRUB loaded and I was shown a new screen about AppArmor and it said it was starting various programs. The screen flickered A LOT while doing then. It then stays steady and reads:

"restarting openbsd secure shell server sshd"

And that's it. It just stays there. For hours. I'm in the process of downloading a Karmic LiveCD and might do a clean install but I'd like to avoid that if possible. Any ideas, friends?

---

### Post by carvao on 2009-10-31
the same with me

---

### Post by qwerta001 on 2009-10-31
I had the same - I cancelled the install (couldn't find the 1st disk /dev/sda1, said I had no operating system!!!), then chose reboot - the screen went blank, the install disk ejected, then it just sat there doing nothing. I had to hold down the power button to finally shutdown my PC.

From my own experience, and all the other peoples experiences here, I can only conclude that Ubuntu is fatally flawed. Canonical should consider withdrawing 9.10 until they can fix all these really obvious problems that should have all been fixed during the beta phase. To release this buggy, incompetent excuse of an OS is criminal! (especially considering how well 8.04 did).
Come on Canonical, even MS are better than this! Grrrr... :mad:

---

### Post by littlemisscrazy on 2009-10-31
I'm prettynew to ubuntu and i was loving it more day by day- but this night it made me cry for the first time!
i also tried to upgrade from internet and it seems like i only have graphic problems, because after start up, when the cpu is quiet i can type my user name and password- though the screen is balck- and it starts up completely i think because i can hear it continuing work.
but icannot save all my data because i can't see anything...i can only reinstall 9.04 from cd and i'm so upset!

---

### Post by 68pontiac on 2009-10-31
Well I'm posting this from the LiveCD, which seems to be working great. Right now I'm backing up all my photos/music/videos and World of Warcraft folder (the most important thing ;) ) to an external hard drive in an attempt to reformat to ext4 and start over. Is there anyone that has an idea in regards to our problem?

---

### Post by qwerta001 on 2009-10-31
68pontiac said
'...Is there anyone that has an idea in regards to our problem?'

Windows 7? :twisted:

I'll get my coat! :)

---

### Post by 68pontiac on 2009-10-31
> **qwerta001 said:**
> 
Windows 7? :twisted:

I'll get my coat! :)

I'd like to avoid spending hundreds of dollars. ;)

---

### Post by qwerta001 on 2009-10-31
> **68pontiac said:**
> I'd like to avoid spending hundreds of dollars. ;)
Seriously, I was hoping 9.10 would be good enough to replace Vista, rather than have to buy Windows 7. I was planning to maybe use VMs to run the few Windows apps that I need, leaving most of my day to day stuff running on Ubuntu (Music production, email, browsing etc).
I really hope they can sort this stuff out soon.

---

### Post by littlemisscrazy on 2009-11-02
i'm not an ubuntu geek, so i was pretty rushing on installing new- 

when booting the computer press ESC when it comes to the GRUB screen choose the last working kernel recovery 

and wait for working 9.10 while enjoying your former system....

despite this problem nothing will get me back to windows!

---

### Post by auburn on 2009-11-02
Same problem here. There are a couple things you can try. When it first boots and asks you if you'd like to hit Esc for grub options, do that. You should get a list of kernels to boot from on the menu. My top option (the default) is: Ubuntu 9.10, kernel 2.6.31-14 generic. You can choose to boot from that kernel or toggle down to any of the kernels below. 

You can also edit the boot configuration from the grub menu (very easy, don't worry) by toggling to the kernel of choice and hitting 'e' for edit. That takes you to a second screen where you can toggle down to the middle line and hit 'e' to edit and remove a few options. These changes are temporary and will not exist on your next restart. I've been having good luck removing 'ro quiet splash' but you can try deleting any of those options.

After editing you have to hit 'esc' and 'b' to boot the configuration you just edited.

Be patient, i've had good luck with several different kernels and edits.

---

