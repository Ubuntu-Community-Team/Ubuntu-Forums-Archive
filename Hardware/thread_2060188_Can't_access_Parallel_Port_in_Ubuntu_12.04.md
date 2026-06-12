---
title: "Can't access Parallel Port in Ubuntu 12.04"
date: 2012-09-19
forum: Hardware
---

### Post by foberle on 2012-09-19
I apologize if this is a duplicate - I thought I posted it this morning with several other questions, but can't locate it on the forum.

 

 I recently installed Ubuntu 12.04 as a dual boot on a Windows machine. Among many issues I've encountered, one annoying one concerns the lack of support for the parallel port. I had earlier posted questions about this on another forum, but got NO responses whatever, so I thought I would try here.
 

 Here's the data about the card provided by the command “lspci -vv”:
 

 ```
[FONT=Courier New, monospace][SIZE=2]03:07.0 Communication controller: NetMos Technology PCI 1 port parallel adapter (rev 01) [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	Subsystem: LSI Logic / Symbios Logic Device 0010 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	Interrupt: pin A routed to IRQ 3 [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	Region 0: I/O ports at ce00 [size=8] [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	Region 1: I/O ports at cd00 [size=8] [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	Region 2: I/O ports at cc00 [size=8] [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	Region 3: I/O ports at cb00 [size=8] [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	Region 4: I/O ports at ca00 [size=8] [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	Region 5: I/O ports at c900 [size=16] [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]	Kernel modules: parport_pc [/SIZE][/FONT] 
 
``` 
 It seems obvious to me that Ubuntu recognizes that the card exists, which suggests that a) it didn't know how to set it up automatically during install, and b) that I should be able to get it to work through some incantation or other. There are many, many posts about using a parallel port in Linux/Ubuntu on the web, but none of the techniques seem to work for me (and the vintage and applicability of some of these postings isn't at all clear). Based on the most literate of the web postings I found (on this forum by the way), dated in January 2009 (by “Alex”), here's a recap of my most recent attempt to get the port working:
 

 I issued the following commands in sequence:
 

 ```
[FONT=Courier New, monospace][SIZE=2]sudo rmmod lp[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]sudo rmmod parport_pc[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]sudo /sbin/insmod /lib/modules/3.2.0-30-generic/kernel/drivers/parport/parport_pc.ko io=0xce00 irq=none[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]sudo /sbin/insmod /lib/modules/3.2.0-30-generic/kernel/drivers/char/lp.ko[/SIZE][/FONT]
 
``` 
 After this, when attempting to add a generic printer (all I need), I can select “parallel:/dev/lp0” as the device URI (after a surprisingly long wait for the list to be populated – is that a clue?), but the “Print Test Page” button is greyed out, and nothing whatever happens when I attempt to print to it.
 

 Dropping down to the command line, the commands [echo “Hello” > /dev/lp0] and [echo Hello > /dev/parport0], even when prefixed with [sudo] both give “permission denied” messages.
 

 I checked permission levels on /dev/parport0 and /dev/lp0, and both have permissions set to “crw-rw----”, which seems to me in my current ignorant state to suggest that “permission denied” may be a red herring, since these are owned by lp. But my last exposure to Unix was back in the mid-1980s, so I'm prepared to be yelled at.
 

 Next I attempted to use the same sequence of commands above, but with the IRQ set to 3, as shown in the lspci output above. I had originally used the “irq=none” based on the referenced posting.
 

 Still the same results all around. I also attempted the sequence using different io addresses given in the lspci output; again, I started with the one for Region 3 as suggested in the referenced posting.
 

 I should mention, of course, that the parallel port works just fine under Windows, so I don't believe that's an issue.
 

 Does anyone have any insights to share?

---

### Post by howefield on 2012-09-21
Thread moved to the "*Hardware & Laptops*" forum.

---

### Post by Ms. Daisy on 2012-09-21
I can't help you with the parallel ports, but I can tell you how to find your thread again.

[ATTACH]224456[/ATTACH]

As the picture shows, you can subscribe to the thread.  Then to see it later, go to the User CP to view "subscribed threads"

[ATTACH]224457[/ATTACH]

---

### Post by steeldriver on 2012-09-21
Have you tried adding your user to the group that owns /dev/lp0 (probably 'lp')?

```
sudo gpasswd --add *youruser* lp
``` 

[that's the safest way imo - you could use usermod but if you get it wrong you can blow away other group memberships]

and / or 'lpadmin' if you are not already (I think that the primary user gets lpadmin by default)

Your test with echoing stuff as sudo *is* a red herring - though possibly not for the reasons you think (it's the > redirect that's the problem - the 'sudo' doesn't apply to it, only to the echo - so it doesn't affect the permissions that matter)

---

### Post by BlinkinCat on 2012-09-21
> **foberle said:**
> I apologize if this is a duplicate - I thought I posted it this morning with several other questions, but can't locate it on the forum. 

Further for your information - You can find all of your threads (to 250) or your posts on the Drop down "Search" Menu.

Cheers - :p

---

### Post by s1baker on 2012-09-21
I have a plotter hooked up to my 12.04 box using the parallel port.
I run my CAD software using VirtualBox, and I could not send the plot files to the parallel port.
What I had to do was plot the drawings to files, and then I used this command to send the file to the parallel port:
```
cat  file1 file2 file3  > /dev/lp0
```
if you can print to a file, you may want to try this, if you can't find a better & quicker way.

---

### Post by foberle on 2012-09-26
I am only now able to take advantage of the suggestion to "cat file > /dev/lp0" since, thanks to trolling the web, I've been able to get output from the command line to my dumb printer. Unfortunately I still have not been able to use the parallel port when setting up a printer. The following will outline the steps I took; if anyone can tell me what other magic incantations I need to assign this port to a dumb (text-only) printer, I would much appreciate it.
 

 One piece of advice I received said to determine whether I was a member of the groups lp and lpadmin. To do this, I downloaded and installed the libuser package to get the lid command. I ran the lid command as follows:
 [FONT=Courier New, monospace][SIZE=2]sudo lid -g lp[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]sudo lid -g lpadmin[/SIZE][/FONT]
 

 The output showed that I was NOT part of the lp group. I then ran the following command to add myself to the group:
 [FONT=Courier New, monospace][SIZE=2]sudo gpasswd -a foberle lp[/SIZE][/FONT]
 

 Then I issued the following commands in sequence to unload and reload the kernel modules related to the parallel port::
 [FONT=Courier New, monospace][SIZE=2]sudo rmmod lp[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]sudo rmmod parport_pc[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]sudo /sbin/insmod /lib/modules/3.2.0-30-generic/kernel/drivers/parport/parport_pc.ko io=0xce00 irq=none[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]sudo /sbin/insmod /lib/modules/3.2.0-30-generic/kernel/drivers/char/lp.ko[/SIZE][/FONT]
 

 I should note that the io address that ended up working (at least partially) for me was the one listed as Region 0 in the lspci -vv command output (0xce00); I only mention this because the most useful post I found on this issue suggested that the author had gotten his to work using the address given under Region 3, which didn't work for me at all. So, finally, when executing:
 [FONT=Courier New, monospace][SIZE=2]cat Test_File.txt > /dev/lp0[/SIZE][/FONT]
 or
 [FONT=Courier New, monospace][SIZE=2]echo “Hello” > /dev/lp0[/SIZE][/FONT]
 

 the output printed on the dumb printer just fine.
 

 In order for the permission changes to survive a reboot, I had to create a new file called /etc/modprobe.d/options that contained the line:
 [FONT=Courier New, monospace][SIZE=2]options parport_pc io=0xce00 irq=none[/SIZE][/FONT]
 

 I also edited the /etc/modules file to add the following lines:
 [FONT=Courier New, monospace][SIZE=2]parport_pc[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]lp[/SIZE][/FONT]
 

 Then, after a reboot, I can continue to print to the machine on the parallel port from a terminal - a kludge at best, but somewhat useful.
 

 ***BUT*** I am still unable to locate, much less select this port from the Add Printers app. I attempted to change the permissions on /dev/lp0 and /dev/parport0 to a=rwx, which didn't seem to make any difference whatever. So, although I can still select parallel:/dev/lp0 as the device URI, the “Print Test Page” button is still greyed out, and I am unable to use this printer definition from any app (although it shows up as a choice).
 

Does anyone have any suggestions as to where to go from here (other than return to Windows, of course)?


Thanks...

---

### Post by foberle on 2012-09-30
Latest Discoveries – Is my problem using the parallel port a Linux Kernel issue??
 

 The following interesting lines are found in the output of the command dmesg | grep par
 ```

[   16.377512] parport 0xce00 (WARNING): CTR: wrote 0x0c, read 0x09  
 [   16.377532] parport0: PC-style at 0xce00 [PCSPP,TRISTATE,EPP]  
 [86255.224539] parport0: ppdev0 forgot to release port  
 [107052.004667] parport0: ppdev0 forgot to release port  
 [107174.369301] parport0: ppdev0 forgot to release port 


``` ppdev is described as “user-space parallel port driver”
 

 Searching around on the internet, I located the following posting at [https://lkml.org/lkml/2012/9/1/94](https://lkml.org/lkml/2012/9/1/94)
 

 Error handling of parport_register_driver() in ppdev_init() is broken because it deallocates all resources but still returns zero.
Currently parport_register_driver() always succeeds. Nevertheless it is worth to fix the issue.
Found by Linux Driver Verification project (linuxtesting.org).
Signed-off-by: Alexey Khoroshilov <khoroshilov@ispras.ru>  So, ppdev “deallocates all resources but still returns” an error.
And my machine is reporting that ppdev “forgot to release port.”  This posting is dated less than a month ago.  So, I have two questions: 
1) Is this possibly the source of my difficulties assigning my parallel port to a printer? 
2) If it is a likely cause, is there any practical way of updating this portion of the kernel?

---

### Post by claas42 on 2013-06-22
I seem to have a similar problem after upgrading from 10.04 to 12.04. Details are described here:
[http://askubuntu.com/questions/307913/how-to-set-up-a-parallel-port-printer-in-12-04](http://askubuntu.com/questions/307913/how-to-set-up-a-parallel-port-printer-in-12-04)
Any ideas of what I could test? Already lspci gives no output:
```
$ sudo lspci -vv | grep parallel
$
```

Maybe this could help, too:
```
$ dmesg | egrep 'lp|parall|parport'
[    0.000000] On node 0 totalpages: 1013615
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6666.46 BogoMIPS (lpj=13332928)
[   16.808350] lp: driver loaded but no devices found
[   16.818719] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   16.818781] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   16.938743] ppdev: user-space parallel port driver
$
```
Thanks for ideas! :)

---

