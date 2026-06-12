---
title: "Gutsy is destroying my hard drive!"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by Zdravko on 2007-12-19
Help! Ubuntu is destroying my hard drive. At the beginning there was only Vista running. I noticed the hdd activity led is constantly on. I thought my laptop is not compatible with Vista. That is why I decided to erase Vista and replace it with Gutsy. No effect. What to do?

---

### Post by wthanna on 2007-12-19
You had a problem with Vista and the hard drive.  Now you have a problem with Ubuntu and the hard drive.  What is the common thing in the previous sentence?  Hint: It is not Ubuntu.  Check or have your hardware checked. Gutsy is not destroying your hard drive, if you had the same problem running Vista.  Thread titles like this.. well, I've said enough. Good luck.

---

### Post by Zdravko on 2007-12-19
But how do I know what is the problem? How do I have my hardware checked?

---

### Post by leader303 on 2007-12-19
you can scan your hd with fsck. if you don't know how to start it at bootup, you can install bonager ([http://ubuntuforums.org/showthread.php?t=295262](http://ubuntuforums.org/showthread.php?t=295262)).

---

### Post by Whiffle on 2007-12-19
Try doing:

'sudo hdparm -B255 /dev/whatever/your/hard/drive/is'

and see if it goes away...

---

### Post by Zdravko on 2007-12-19
I just installed it. I forced a scan for the next boot. Wait a sec...

---

### Post by tgalati4 on 2007-12-19
How much memory in your laptop?  If less than 256 MB then you may have excessive hard disk activity due to swapping out memory to disk.  This would happen in either Vista or Ubuntu.

---

### Post by Zdravko on 2007-12-19
I have 2x512 MB of RAM with 1 GB swap.
I restarted and the scan was made.
After logging in I got an error message about activating a service. Now my desktop looks awkward:

---

### Post by tech9 on 2007-12-19
> **Zdravko said:**
> Help! Ubuntu is destroying my hard drive. At the beginning there was only Vista running. I noticed the hdd activity led is constantly on. I thought my laptop is not compatible with Vista. That is why I decided to erase Vista and replace it with Gutsy. No effect. What to do?

do you have any scheduled jobs, such as AV scans in the background. It sounds like your HD is constantly reading or writing.

---

### Post by wthanna on 2007-12-19
Try posting some of the following, and see if someone else in the forums has had similar issues and can help.

PC Manufacturer and model
Hard disk manufacturer and model, if known.
As detailed a description of the problem as possible.
Does the computer run as it is supposed to other than the hard drive light issue.
Any other related symptoms, if possible.
Did the computer "ever" run correctly?
If this is a new computer, do you have a warranty? Possibly the seller will fix or replace it.

---

### Post by Zdravko on 2007-12-19
> **tech9 said:**
> do you have any scheduled jobs, such as AV scans in the background. It sounds like your HD is constantly reading or writing.
I just installed Gutsy. How should I know of these?

---

### Post by tech9 on 2007-12-19
> **Zdravko said:**
> I have 2x512 MB of RAM with 1 GB swap.
I restarted and the scan was made.
After logging in I got an error message about activating a service. Now my desktop looks awkward:

1 GB is sufficient....

If worse comes to worse, you can always backup your data and reinstall ubuntu clean. 

Then if your problem persists, you know it's hardware related.

---

### Post by Zdravko on 2007-12-19
> **Whiffle said:**
> Try doing:

'sudo hdparm -B255 /dev/whatever/your/hard/drive/is'

and see if it goes away...

Elaborate please. During install I set 3 partitions:
10 GB /
20 GB /home
1 GB swap
Rest - 49GB unpartitioned.

---

### Post by tech9 on 2007-12-19
> **Zdravko said:**
> I just installed Gutsy. How should I know of these?

sounds like you don't then... I meant if you setup some automatic scripts.

---

### Post by Zdravko on 2007-12-19
> **tech9 said:**
> 1 GB is sufficient....

If worse comes to worse, you can always backup your data and reinstall ubuntu clean. 

Then if your problem persists, you know it's hardware related.
I installed Ubuntu clean :cry:

---

### Post by Zdravko on 2007-12-19
> **wthanna said:**
> Try posting some of the following, and see if someone else in the forums has had similar issues and can help.

PC Manufacturer and model
Hard disk manufacturer and model, if known.
As detailed a description of the problem as possible.
Does the computer run as it is supposed to other than the hard drive light issue.
Any other related symptoms, if possible.
Did the computer "ever" run correctly?
If this is a new computer, do you have a warranty? Possibly the seller will fix or replace it.
My laptop is brand new. Its parameters are located here:
[http://ubuntuforums.org/showthread.php?t=640709](http://ubuntuforums.org/showthread.php?t=640709)
I explicitly ordered another 512 MB of RAM. Under Vista I even saw - total RAM is about 1 GB.
This may have not happened, if someone had answered on the previous post :cry:

---

### Post by Zdravko on 2007-12-19
> **Zdravko said:**
> I have 2x512 MB of RAM with 1 GB swap.
I restarted and the scan was made.
After logging in I got an error message about activating a service. Now my desktop looks awkward:
I just did another restart and this time the desktop environment seems ok :)
Okay, help me find out what is constantly tackling with the hard drive!

---

### Post by tech9 on 2007-12-19
> **Zdravko said:**
> I installed Ubuntu clean :cry:

That's strange Then... 

maybe you could install bootchart

```
sudo apt-get install bootchart
```

and see if there is anything strange going on during boot up (see what the HD is doing)

---

### Post by Zdravko on 2007-12-19
> **tech9 said:**
> That's strange Then... 

maybe you could install bootchart

```
sudo apt-get install bootchart
```and see if there is anything strange going on during boot up (see what the HD is doing)
Install another application? The previous one didn't help?

---

### Post by Whiffle on 2007-12-19
> **Zdravko said:**
> Elaborate please. During install I set 3 partitions:
10 GB /
20 GB /home
1 GB swap
Rest - 49GB unpartitioned.


Well, this sounds like the Load cycle issue that everybody's been up in arms about.  The drive constantly unloads the heads if i remember right, about twice every minute.  When I put slackware on my T43 I noticed that my hard drive light was on all the time, and when I put my ear to it I could hear it making a clicking noise every once in a whiile.  I set it to do

```

hdparm -B255 /dev/sda 

```

every time it boots, or resumes.  Now it doesn't do it.  I'm curious if you're having the same issue.  That command shuts off the advanced power management of the drive.  

In your situation, I'm guessing /dev/sda is what we need to use.  We're addressing the whole physical drive, so we don't need to know any of the partitions (which is what the numbers denote)

---

### Post by Zdravko on 2007-12-19
> zdravko@ubuntu:~$ hdparm -B255 /dev/sda
/dev/sda: Permission denied
zdravko@ubuntu:~$ sudo hdparm -B255 /dev/sda
[sudo] password for zdravko:

/dev/sda:
 setting Advanced Power Management level to disabled
zdravko@ubuntu:~$ 

No effect. :cry:

---

### Post by Whiffle on 2007-12-19
Well you could always run

top

and see if theres any programs at the top of list, anything that is accessing your drive that much is bound to be using some cpu.  If its not a program...then its hardware.  I'm not totally convinced on the hdparm thing though, I'll think about it.

---

### Post by Zdravko on 2007-12-19
> zdravko@ubuntu:~$ top

top - 18:56:02 up 15 min,  2 users,  load average: 0.06, 0.13, 0.16
Tasks: 110 total,   1 running, 109 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.2%us,  0.0%sy,  0.0%ni, 98.5%id,  0.2%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1019780k total,   759060k used,   260720k free,    14680k buffers
Swap:   979924k total,        0k used,   979924k free,   354324k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 5448 root      15   0  397m  23m 7564 S    2  2.4   0:27.42 Xorg                                                                                            
 6505 zdravko   15   0  265m  26m  12m S    1  2.7   0:00.25 gnome-terminal                                                                                  
 6525 zdravko   15   0 18952 1324  972 R    0  0.1   0:00.05 top                                                                                             
    1 root      15   0  5112 1964  572 S    0  0.2   0:01.23 init                                                                                            
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                     
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                     
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                      
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0                                                                                        
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                                                        
   11 root      10  -5     0    0    0 S    0  0.0   0:00.01 khelper                                                                                         
   30 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                                       
   31 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                       
   32 root      10  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                          
   33 root      20  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                    
  183 root      10  -5     0    0    0 S    0  0.0   0:00.10 kseriod                                                                                         
  215 root      16   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                         
  216 root      15   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                         
  217 root      11  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                         
  270 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                           
  271 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                           
 2205 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                   
 2206 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                           
 2246 root      10  -5     0    0    0 S    0  0.0   0:00.09 ata/0                                                                                           
 2248 root      10  -5     0    0    0 S    0  0.0   0:00.10 ata/1                                                                                           
 2249 root      20  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                         
 2426 root      20  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                       
 2428 root      20  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                       
 2453 root      10  -5     0    0    0 S    0  0.0   0:00.29 scsi_eh_2                                                                                       
 2454 root      14  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                                                       
 2603 root      10  -5     0    0    0 S    0  0.0   0:00.05 kjournald                                                                                       


Does this mean something to you?

---

### Post by Whiffle on 2007-12-19
Well, I see two things here.  1, linux isn't even touching your swap partition, so its not that.  I don't see any programs either that look suspicious.  

I think we should do some more checking on this load cycle count issue.

Do:
```

sudo apt-get install smartmontools

```
(I think thats the right one)

and then lets make this little script in a file
```

nano -w script.sh

```

paste this into it:
```

while (true);
 echo `date` >> loadCycleCountLOG.txt
 do sudo smartctl -d ata -a /dev/hda | grep 193 >> loadCycleCountLOG.txt;
 sleep 30
 done

```

then save and close with F3 and ctrl+x 

then
```

chmod +x script.sh

```

then

```

./script.sh

```

Now wait a little while,  and then open up loadCycleCountLOG.txt and see how quickly the number is going up (not quite which number it is, I don'thave my laptop in front of me)

I got that script here:
[http://hobbylobby.wordpress.com/2007/11/24/ubuntu-demon-says-the-load-cycle-count-not-ubuntus-fault/](http://hobbylobby.wordpress.com/2007/11/24/ubuntu-demon-says-the-load-cycle-count-not-ubuntus-fault/)

---

### Post by tgalati4 on 2007-12-19
Post the output of:

>dmesg | tail

and see if there are any system messages of interest.  A loose or worn ribbon cable may cause data errors that are correctable and can take a long time to access the drive.  Are you having any freeze or slowness issues when accessing the drive?

---

### Post by Nano Geek on 2007-12-19
As was said before, since it happens both in Vista and Ubuntu, then it's probably a hardware problem.
Take it back to the store where you bought it from and ask them to look at it if it's under warranty. 

Just make sure you put Vista back on it so they can fix it.

---

### Post by tech9 on 2007-12-19
> **asjdfwejqrfjcvm msz34rq33 said:**
> As was said before, since it happens both in Vista and Ubuntu, then it's probably a hardware problem.
Take it back to the store where you bought it from and ask them to look at it if it's under warranty. 

Just make sure you put Vista back on it so they can fix it.

I second that!

---

### Post by astromech on 2007-12-19
> **asjdfwejqrfjcvm msz34rq33 said:**
> As was said before, since it happens both in Vista and Ubuntu, then it's probably a hardware problem.
Take it back to the store where you bought it from and ask them to look at it if it's under warranty. 

Just make sure you put Vista back on it so they can fix it.



This is the best advice.You should not have to go through all this if it's under warranty and especially brand new . Get it fixes and then if Vista works reinstall gutsy and if that dosen't work try feisty.

---

### Post by Zdravko on 2007-12-19
> **tgalati4 said:**
> Post the output of:

>dmesg | tail

and see if there are any system messages of interest.  A loose or worn ribbon cable may cause data errors that are correctable and can take a long time to access the drive.  Are you having any freeze or slowness issues when accessing the drive?

This one yields:
> zdravko@ubuntu:~$ dmesg | tail
[  613.320920] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  631.426010] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  657.234737] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  677.609021] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  699.698411] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  725.854764] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  747.401520] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  770.841846] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  796.404788] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  822.639141] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
zdravko@ubuntu:~$ 


I am thinking of calling the sellers. The laptop is new and it has 1 year of warranty. I bought it 5 days ago.

---

### Post by Zdravko on 2007-12-19
> **tgalati4 said:**
> Post the output of:

>dmesg | tail

and see if there are any system messages of interest.  A loose or worn ribbon cable may cause data errors that are correctable and can take a long time to access the drive.  Are you having any freeze or slowness issues when accessing the drive?

Actually, to be honest, I think Ubuntu feels a little bit slow. Most of the options windows of Administration and Preferences take a while to load completely. Dunno whether this is normal. :cry:

---

### Post by wieman01 on 2007-12-19
It's your hardware as the others have highlighted.

Does the HD also make a sound as if there is stuff written on to it? Or is it only the LED that is lit?

---

### Post by Zdravko on 2007-12-19
I can only hear the cooling fan. The hdd makes a sound, only when something is really written (e.g. during boot up). The LED blinks normally during boot-up, after a few seconds being powered, the LED remains lit :cry:

---

### Post by wieman01 on 2007-12-19
> **Zdravko said:**
> I can only hear the cooling fan. The hdd makes a sound, only when something is really written (e.g. during boot up). The LED blinks normally during boot-up, after a few seconds being powered, the LED remains lit :cry:
Then it should not be a big deal. Perhaps the LED flickers as soon as something is written on to it, but otherwise simply remain lit. Could that explain it? No sound generally means inactivity, so you should be OK in fact.

---

### Post by Zdravko on 2007-12-19
The handbook I have with the laptop says something different: this LED shows HDD activity. 
I am worried. And as time passes by, I feel even more worried about the future of my hdd :cry:

---

### Post by wieman01 on 2007-12-19
> **Zdravko said:**
> The handbook I have with the laptop says something different: this LED shows HDD activity. 
I am worried. And as time passes by, I feel even more worried about the future of my hdd :cry:
Then contact customer support. They might have mistakenly swapped a wire or something like that, I don't know. But you should definitely touch base with them and ask for advice. 

There is little we can do on our end. It is still under warranty so it won't cost you a dime, but will save you a lot of trouble.

---

### Post by Zdravko on 2007-12-19
Today it is too late for such a call. Tomorrow morning I will contact them. Should I say something special about the problem?
BTW, originally the laptop was with Linpus. It was a very raw command line Linux and I replaced it with Vista. I noticed Vista is crap and replaced it with Gutsy. Now - with the same issue, no sound etc. - I am sorry. It seems this laptop is incompatible with any OS on the world. :cry: And my mother paid for it nearly 600 Euro! Can you imagine that? I shouldn't ever tell her about these problems. I will have to figure out some solution :cry:

---

### Post by wieman01 on 2007-12-19
> **Zdravko said:**
> Today it is too late for such a call. Tomorrow morning I will contact them. Should I say something special about the problem?
BTW, originally the laptop was with Linpus. It was a very raw command line Linux and I replaced it with Vista. I noticed Vista is crap and replaced it with Gutsy. Now - with the same issue, no sound etc. - I am sorry. It seems this laptop is incompatible with any OS on the world. :cry: And my mother paid for it nearly 600 Euro! Can you imagine that? I shouldn't ever tell her about these problems. I will have to figure out some solution :cry:
Is there a chance that you can return it? Have it replaced with another piece of hardware. Some vendors do that...

---

### Post by Zdravko on 2007-12-19
You mean the HDD? Well - if the HDD is the root of all evil - yes, I might insist on having it replaced. But I don't know whether HDD's could be replaced on laptops? And - how can I proof the HDD is faulty?

---

### Post by wieman01 on 2007-12-19
> **Zdravko said:**
> You mean the HDD? Well - if the HDD is the root of all evil - yes, I might insist on having it replaced. But I don't know whether HDD's could be replaced on laptops? And - how can I proof the HDD is faulty?
You could have the whole thing replaced with another brand for instance. If that is not possible, tell them your issue and prove to them that the user guide says something about the LED being lit only when the HD is active. They will understand that and hopefully help you. If not, sue them. ;-) Kidding of course.

They can either replace the HD (which is simple in most cases - Sony Vaio laptop being an exception) or replace the laptop with a new one (same brand or other). Just have a chat with them first and see how they respond.

---

### Post by Zdravko on 2007-12-19
Okay. I hope for the best :cry:

---

### Post by Zdravko on 2007-12-19
I just read: [http://forums.whirlpool.net.au/forum-replies-archive.cfm/544345.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/544345.html)
It seems that there are faulty HDD's around. I might be able to convince the seller replace the current HDD ;)

---

### Post by Zdravko on 2007-12-20
> **leader303 said:**
> you can scan your hd with fsck. if you don't know how to start it at bootup, you can install bonager ([http://ubuntuforums.org/showthread.php?t=295262](http://ubuntuforums.org/showthread.php?t=295262)).

Why don't you tell me how to show you the result of the scan? Else, I will remove this application.

> **Whiffle said:**
> Try doing:

'sudo hdparm -B255 /dev/whatever/your/hard/drive/is'

and see if it goes away...

Now that it is apparent this does no work, would you please be so nice and tell me how to revert to the previous state?
> **wthanna said:**
> Try posting some of the following, and see if someone else in the forums has had similar issues and can help.

PC Manufacturer and model
Hard disk manufacturer and model, if known.
As detailed a description of the problem as possible.
Does the computer run as it is supposed to other than the hard drive light issue.
Any other related symptoms, if possible.
Did the computer "ever" run correctly?
If this is a new computer, do you have a warranty? Possibly the seller will fix or replace it.

The HDD is Hitachi, as far as I can see it under BIOS. Another problem has also appeared. Once under Vista, the laptop just shut down. But a few seconds before that the fans started working. During Ubuntu install absolutely the same happened. So far - 2 times. If it happens one more time - I will have to call the sellers :cry:

---

### Post by Whiffle on 2007-12-20
It will revert as soon as you restart.

---

### Post by Zdravko on 2007-12-20
Okay, what about the other questions?

---

