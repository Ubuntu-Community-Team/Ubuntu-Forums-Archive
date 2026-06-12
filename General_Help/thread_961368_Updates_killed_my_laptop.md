---
title: "Updates killed my laptop"
date: 2008-10-28
forum: General Help
---

### Post by johns996 on 2008-10-28
I ran the normal automatic update today and it seems to have killed my laptop.  

After the update I noticed the reboot required icon next to the clock, so I rebooted.  At this point Grub simply failed and I was taken to a screen that said:

> Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/file name.


I then put in my Ubuntu live CD, booted and restored a backup of my old Grub menu.lst file.  Using this restored Grub menu, I can get back into my windows partitions but my Ubuntu entries will not work.  They are still looking for kernel 2.6.24-19, but each time I try to boot it I get:

> Error 15: File not found

Any ideas on what I can try?

---

### Post by tgalati4 on 2008-10-28
As a general rule, new users should avoid updates to "linux" and "xorg" until they can handle the repairs that are sometimes required to get a system working again.

A forum search on "repair grub" will give you ideas.  I don't recall what the specific error 15 means other than it can't find the kernel file to boot from.

It could be a partition problem, a hard disk root selection error (hd0,0) vs (hd0,1), a device description error (/dev/hda1 vs /dev/sda1).

Without more descriptive information, it's tough to say.  Although restoring your menu.lst or grub.conf file means that you no longer have the new kernel entry (2.6.24-19).  It could be as simple as editing your grub configuration file and including the correct kernel and initrd image name.

---

### Post by johns996 on 2008-10-28
> As a general rule, new users should avoid updates to "linux" and "xorg" until they can handle the repairs that are sometimes required to get a system working again.

That has to be the worst possible answer you could give.  Isn't ubuntu intended to be the desktop-friendly distro?  It's not like I was doing anything out of the ordinary with my system.  It prompted me to run the automatic updates, I ran them and my computer now fails to boot properly.  

If "new users" should avoid updates to certain parts of the system, maybe those updates should not be pushed as recommended updates to anyone using the system.

> Without more descriptive information, it's tough to say.

What other descriptions can I provide?  The error I've seen have been displayed exactly as shown on the screen.  There is nothing else for me to report since I can do anything except see Error 15: File not found.

---

### Post by neighborlee on 2008-10-28
> **johns996 said:**
> That has to be the worst possible answer you could give.  Isn't ubuntu intended to be the desktop-friendly distro?  It's not like I was doing anything out of the ordinary with my system.  It prompted me to run the automatic updates, I ran them and my computer now fails to boot properly.  

If "new users" should avoid updates to certain parts of the system, maybe those updates should not be pushed as recommended updates to anyone using the system.



What other descriptions can I provide?  The error I've seen have been displayed exactly as shown on the screen.  There is nothing else for me to report since I can do anything except see Error 15: File not found.

I think he may have misunderstood ;)

Its clear you updated as a result of being prompted to,  so his reply would not make sense ;)

I think inpart such things happen because the 'pool' of testers isn't large enough since linux is slightly framented due to  people using many different distros, even though ubuntu seems to be standardizing linux, to what degree we'll see.

I dont know, as I dont have your laptop, and that error means litle to me.. but you might get online at irc.freenode.net , on channel #ubuntu and see if anyone there can help you..

If its too busy there feel free to get help at #neighbors on the same server, it would be more one on one there if  #ubuntu is a bit busy atm, as sometimes asking doesn't return a reply due to that issue and of course depending on time of day YMMV :)

cheers and good luck.
nl

---

### Post by lunarcloud on 2008-10-28
Try reinstalling in a few days when intrepid comes out.

---

### Post by johns996 on 2008-10-28
I poked around in the grub menu for a bit and if I change the kernel line from:

> kernel /boot/vmlinuz-2.6.24-19-generic root=[...]

to

> kernel /boot/vmlinuz-2.6.24-21-generic root=[...did not change this]


I can get Ubuntu to boot.  It loads the desktop but none of the launcher bar menus.  Clicking on the desktop does not work either.  Is the desktop not working because I didn't change the root section of grub for the different kernel?  Or is there something else going on?

---

### Post by johns996 on 2008-10-28
> **zarquad said:**
> Try reinstalling in a few days when intrepid comes out.

that sounds like a "Windows" solution.  One I'm all too familiar with.  But you're right, I'll probably just end up doing that.  I like to try to fix these problems though since it is the only way I really learn more about the OS.

---

### Post by Wilfred on 2008-10-28
Can you work out what kind of files you have  in your /boot?

there are probably several "vmlinuz-2.6.24-xx" files.

Try to change the menu.lst file with different entries.

I have had something similar some time ago. Changin 'xx' to an older number resolved the issue for me , where next updates were smooth as before.

whoever states that new users shouldn't update kernel or x.org should initiate improvement to the update programs, so new users know what update to skip. Until then they better spend thier time trying to help other users.

Hope this helps for you!

---

### Post by johns996 on 2008-10-28
> **Wilfred said:**
> Can you work out what kind of files you have  in your /boot?

there are probably several "vmlinuz-2.6.24-xx" files.

Try to change the menu.lst file with different entries.


Thanks man.  I was wondering where I could find a list of kernels on my system.  I'll check it out.

--Update--

Only one kernel was listed, the 2.6.24-21 kernel.  Adding that to the grub menu allowed me to boot into recovery mode and then I just ran the different fixes there and things seem to be sorted out now. I wish I knew what happened so I could prevent others from running into this mess but I still have no idea.

---

### Post by malleus74 on 2008-10-28
Please take a look at this thread to see other problems people who recently updated have had. You might find some answers to your problem. Most of us have no problems at all if we go back to the .24-19 kernel.

[http://ubuntuforums.org/showthread.php?t=948584](http://ubuntuforums.org/showthread.php?t=948584)

---

### Post by malleus74 on 2008-10-29
If you can list your hardware, ubuntu version, what the update did over in the other thread, we'd really appreciate it! We're trying to gather up all the threads pertaining to this issue, and get the developers' attention. :)

---

