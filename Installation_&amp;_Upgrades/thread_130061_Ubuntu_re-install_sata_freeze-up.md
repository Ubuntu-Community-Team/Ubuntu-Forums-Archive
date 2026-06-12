---
title: "Ubuntu re-install sata freeze-up"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by jscheiderer on 2006-02-15
I am using the ubuntu 5.10 to install onto sata 80 drive(s).
-> This is a re-install because the system has had some problems (such as: synaptic won't load-says another program ?syn? is loaded, and firefox closes itself for no apparent reason). I can build a pc but not program it, so I know I should look at some log files somewhere...somewhere...but :/ if I know where to start for those. Anyway, prbably a bad habit I have leftover from windows. 
-> Anyway, I popped the 5.10 cd in, booted it, wiped the partitions on both sata 80's, and then I thought hmmm here's an interesting menu - RAID. Well, that didn't succeed as the install gave me an error there. I therefore wiped the raid partition, created standard partitions and rebooted.
-> Now I am rebooted and locked in a black screen.
Any ideas?

---

### Post by jscheiderer on 2006-02-15
Well, I am back again. lol. Sorry, but this is going to be long winded, I hope someone can make sense of it all better than I can right now.
I have managed to reboot and get into the ubuntu os load screen (where it lists the different versions/os pre-login). There were about 10 or 12 installed ubuntu 5.10's listed there. I don't know how to edit the grub from here so I went ctrl-alt-del and went to bios. In bios I changed the boot order around (went through the process of change boot order and boot from the cd a few times). Finally, got the install to partitioning. :-D  From here I was able to deterine that I had left a raid configuration in place on the drives but had partitioned the drives themselves 'automatically' for standard install. Well, I removed the raid config, repartitioned BOTH sata drives (again) and rebooted the machine.
...
Ok, now the ubuntu installation cd has booted and proceeded through selecting lang, user name, time zone and ejected the cd. \\:D/  LOOKING GOOD...so far.
...
The pc has rebooted now, but still displays the long lsit of installed ubuntu OS's ( i am assuming that this is hard written into the grub boot loader from the previous attempts I made at installing ubuntu - will have to clean that up somehow, but that's another forum). Now we're into "Installing Packages". 
83% done so far...[-o<

YAHOO!!!!!!!!!!!!!!!! It Worked! It worked!
I don't know why, but it worked this time.
Now... let's see if it can make toast.. lmao!

---

