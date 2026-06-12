---
title: "Install the base system - debootstrap warning"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by happyface_0 on 2009-04-24
Installing Jaunty with the alternative CD.
After the installer copies the required files and starts installing, I get the error:
```
[!!] Install the base system
Debootstrap warning
Warning: Failure trying to run: chroot /target dpkg --forge-depends
--install /var/cache/apt/archives/dpkg_1.14.24ubuntu1_i386.deb
```
If I press <continue> on that window, the next says:
```
Base system installation error
The debootstrap program exited with an error (return value 1).
Check /var/log/syslog or see virtual console 4 for the details.
```
The next error window says: 
```
Install to /target failed...
```
Console 4 says:
```
debootstrap: dpkg-deb: subprocess <decompress> killed by signal (Segmentation fault)
debootstrap: dpkg: error processing /var/cache/apt/archives...
debootstrap: short read in buffer_copy (backend dpkg-deb during './usr/share/locale/hu/LC_MESSAGES/dpkg.mo')
kernel: [...]: segfault at bfba000 ip 08066580sp bfb9d1c0 error 6 in dpkg-deb[...]
debootstrap: Error were encountered while processing:
```

Any help is greatly appreciated.

---

### Post by happyface_0 on 2009-04-25
bump

---

### Post by Kidaf on 2009-04-25
I have the same Debootstrap Warning problem. Only it shows various times the message with different filenames.


Any help?

---

### Post by groen on 2009-04-26
Same problem here,
 
I wanted to make a raid system, but its not working this way. It keeps telling me to install the base continuesly...
 
 
Apparantly it also happens with the server edition....

---

### Post by happyface_0 on 2009-04-26
I figured out what the probably cause of the error is.
Memtest fails horrendously, I'll RMA this RAM and try her again another time.

---

### Post by groen on 2009-04-27
My memory seems to be ok.

I wonder if that is the problem. Please write your newer experiences in this thread since I get emails when someone writes in it.

Thanks

---

### Post by Kidaf on 2009-04-27
I am installing from another HD, with the alternate iso (using vmlinuz and initrd.gz and a new grub entry), and I have no raid. Just two independent HDs (linux partition is on the first HD and the iso is on the second one).

And I already tried tons of times, and ALWAYS the same debootstrap warnings of corrupt files.


I will accept any help of suggestions.

---

### Post by groen on 2009-04-27
Hi Kidaf,

First I tried the 64bit desktop with ext4 raid. I had some problems and installed the desktop 32bit. Was ok, but I could not create raid partitions from the installer ( I wanted swap on raid5, aswell as the /, /boot, /home). Then I tried the 32bit alternate.
Humm, Now I could make nice raid5 partitions using 4 disks.The problems started when I tried to install the base onto it. Well that didn't came our right. One whole day wasted....
The next day I tried the server 32bit. Hee, I could make raid partitions again. Then I tried to install the base. Well, no luck. Again same problem. :confused:

Solution:

Installation of 32bit desktop Jaunty. Made some raid5 partitions using ext3 (not ext4). And this is running at the moment. 

Reasonable stable. Although when I click on power management, the whole computer freezes. Removed program from the installation. Oh, I boot from a flash ide disk (4gigs). Installation is about 2 gigs. I'm not yet finished with the installation - have to  move some directories to the disks (like /home, /var etc.).

But my first important thing is to use the system to offload and backup photo's from another computer.

I hope you understand a little more now. This Ubuntu is not really tested when released.

 :lolflag:

Cheers,

---

### Post by Kidaf on 2009-04-27
I am already trying with 32, not 64. Also, I don't even try to make raid with my disks. And I just try to install with ext3, not ext4.

So, I try from the begining what you used to solve, but I have the Debootstrap Warnings of corrput files. And the iso md5sum is OK!

---

### Post by groen on 2009-04-27
do you use the desktop installation?

---

### Post by Kidaf on 2009-04-27
Yep. Desktop 32 alternate.

---

### Post by groen on 2009-04-27
I had no luck with that alternate.

I use the desktop 32bit standard. 
What would happen if you use that one? Why do you want alternate?

---

### Post by Kidaf on 2009-04-28
I have no burner, so I install via alternate. Have been doing this since Feisty (I have a tuto for Gutsy on that), and Jaunty is the first one that troubles me with that.

Anyone else with any idea? =)

---

### Post by groen on 2009-04-28
I put the standard desktop iso on an usb stick and boot from there. The program I use is called:

unetbootin

Good luck

---

### Post by africantiger on 2009-10-04
Is there a solution to this problem that anyone would like to share with me?  I have tried for over a week now to install Jaunty server (alternate cd, RAID1 config) but no joy.

africantiger

---

### Post by ujuhani on 2009-10-22
I faced the same problem  with server installation and I stocked with it for almost four days.....

At the end I solved it :P

I just unplug my network so I received the option to set up my network manually which I didn't get before ....... then I got the partitioner, base installation, .... and my system is working fine now :P

Hope this will help you

Umar

---

### Post by ujuhani on 2009-10-22
That worked when I connected an IDE HD.... I was able to complete the installation and run the system.

When I come reconnected my SATA HDs (my server has 3 500G HDs) and configured the software RAID it didn't work :(

I am still working and trying

Umar

---

### Post by ujuhani on 2009-10-25
:KS Solved.....

The problem is related to the hardware. It is the memory configuration in the BIOS. The default configuration didn't work for me even when I select to use the Load Optimized Defaults or Load Fail-Safe Defaults.... 

The auto or defult won't work all the time

Specifecly, I changed the values related to the memory and memory timming after I matched them with the values in my memory datasheet or what the motherboard read and wrote adjacent to the value

After that, the server installation run smothly without any problem :grin:

My server is up and running now \\:D/

Thank you

Umar

---

### Post by Techman9 on 2009-12-09
Hey, ujuhani. I've been having the same problem. How did you find the correct values for Memory Timings. I've been in the BIOS all day and i don't know what to do. Any guideance is Greatly Appreciated, Techman9

---

### Post by ujuhani on 2009-12-09
I was checking the motherbored manual and I guess the performance of my mb is very high that ubuntu installer couldn't catch up with it.

In the BIOS of my motherbored it gives me the ranges of values for each and every parameter, I tried to minimize them not be on the optimum performance. Actually, I changed them to the lowest or near to lowest values.

I couldn't remember which parmeter I had changed but this was my strategy. I think while I am not sure, the parameters I changed were related to the writhing speed on the memory

Hope this can help you

Regards,

---

### Post by Techman9 on 2009-12-09
All right. Still no joy. :( so i tried the method described in the last post, but the system still gives me the warning. The first file to go bad is BSDULTILS.deb and after that it goes downhill. any other ideas? any help is awesome

-techman9

---

### Post by ujuhani on 2009-12-10
Techman9 did you try to burn new cd. I would suggest fresh download to be burned in the cd.
also, you can try other cd/dvd drive or previous release of ubuntu

---

### Post by Techman9 on 2009-12-10
Yup. i tried a new CD and new ISO, which did the exact same thing, and i'm going to try hardy a little later. i'll let you know how that goes.

---

### Post by Techman9 on 2009-12-10
All right. so i tried a boot with Hardy thinking that that would maybe make it ok, but i got the same issue. a possibility might be that the PC isn't seeing all of the installed RAM for some reason because it says "DDR at Bank 0   1 ". any ideas?

---

### Post by maraja on 2010-08-24
> **ujuhani said:**
> I faced the same problem  with server installation and I stocked with it for almost four days.....

At the end I solved it :P

I just unplug my network so I received the option to set up my network manually which I didn't get before ....... then I got the partitioner, base installation, .... and my system is working fine now :P

Hope this will help you

Umar

I can confirm this was the solution for me too while installing the 10.04.1 i386 server

Thanks ujuhani, you saved me lot of time :popcorn:

---

### Post by nikoseubert on 2011-01-27
Hey There, 

i had same error using ubuntu 10.04.1 alternate with ext4. 
it worked fine with ext3.
Thx for the thread!
:-)

---

### Post by shukydurn on 2011-03-27
so did anybody find a solution or is there an alternate os that will work?

---

### Post by conkermaniac on 2011-08-28
Just FYI, I had the same problem using the AMD64 alternate install and what did the trick for me was switching from ext4 to ext3.

---

