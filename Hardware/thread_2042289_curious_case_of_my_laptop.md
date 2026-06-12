---
title: "curious case of my laptop"
date: 2012-08-14
forum: Hardware
---

### Post by jusis on 2012-08-14
Hello to all,

On my laptop there have been following problems with most Linux OS (including Linux Mint, Ubuntu from  11.10 on, Knoppix, Dream Studio, Artistx, Apodio and Bodhi Linux), but NOT with Tango Studio, which I use now and works error-free since I installed it (a week or two ago):

 -PC freezes within 1-2 minutes to 1 hour of desktop session start.
 -random shutdown-reboots. this began to happen 1 to 3 times a day only since last  friday. (this also happened even PC was at the "factory settings" in  Windows Vista)
 -Knoppix live USB boot hangs after disk partition containing Knoppix OS is detected.
 I used the following diagnosis methods:
 1.I did Memtest with 10 passes,leaving it running overnight. All passes were without errors.
 2.I did the longest SMART test on Disk Utility. It showed the same  error that existed for months now; reallocated sector count, explained  as read/write verification error (4 bad sectors and the normalized/worst/threshold values remaining the same since the error started).
Online information says this error value staying constant and  not increasing is to be deemed as something not to worry about so far.
 3. I installed a CPU temperature indicator on the Tango Studio desktop. The values  remained between 44-51°C over the course of about 2 hours, where the  critical value was shown as 114°C. does this rules out that CPU might  have a general overheating problem? (I might have to test it with other OS, too, though?)

 

Half-opening the laptop case (I didnt know how to completely dissamble, so couldnt manage it), I blew compressed air in it from the opening I could get, and  tried to clean the fan I could see, but not ins and outs of the  hardware. I reseated both RAMs, too.
 would a full clean-up,  that is obviously worthwhile for hardware health, still be worthwhile in  terms of tackling above issues?
 Having then reassembled PC and booted Ubuntu 11.10, it froze in 2.minute.


 4.I feel by now absolutely certain that with Tango Studio I have none  of the problems that happen with all other referred OSes; no PC freezes, no random shutdown-reboot attacks (btw, this happened during brief "factory settings" session in Windows Vista, too), no breakdown whatsoever.


 A possibly important point: my power adapter had a loose contact on the input cable, and I used it that way since last April. between April and late July I'd had only screen freezes for a brief period or occasionally; but about 2 weeks ago it began happening at every boot. Hence I recently bought a new adapter, this was a fancy-looking universal one, sold at an electronic market. The piece looked reliable, voltage, amper and PC model were supported and confirmed by the sales attendant, the price was fairly enough to expect some reliability (40 Euros). 



OTOH, I thought, if there were a hardware problem whether with RAM, HDD, CPU,  processor or motherboard, shouldn't this also have occured in Tango  Studio, either?..but then..I dont get why since only last Sunday Knoppix  boot from USB hangs, too, at the point the partition gets detected..
  

A notebook repair guy told me that I should definitely not trust universal adapter and get an original adapter ASAP. However he wondered why the PC had no problem with a single OS. Any failures of referred sorts should have affected any OS, he meant. 

After all, Knoppix USB hanging started only recently, after I got the new adapter. So the regularly daily auto-shutdown-reboots have become. whether or not correlated??... 



Another repair guy said power cable weaknesses wouldnt induce such failures, and that the main board was likely defected. This was contrary to many online comments in forums that connected power supply defects to PC freezes. and he explained the functioning of one OS as "some parts of main board could be enough to run one OS perfectly, while other OS demand more performance or involvement of other main board parts". 



what might have been the reason(s) in this case, from your experiences and knowledge? what could I try more? 



I dont know how to proceed now..getting an original adapter seems to be worth trying, I can still return the universal one back to the seller..else are there motherboard testing tools for linux OS? I already downloaded ultimate boot cd, phoronix (also systemrescue CD, but this one seems to be more for data recovery..) would these tools return reliable evidence for any possible motherboard failure? can a layman run them with the help of online guide and documentation, or better having an experienced helper by one's side?  


thank you so much for your time and insights!

best summer days!

[COLOR=Green]
_recent update:_ [/COLOR][COLOR=Green]

I applied ultimate boot cd and selected one of the "system" testing  applications (cant remember the name, but it was the one with four big  letters starting with N). As soon as it started, it returned the message  "an active virus has probably been detected in memory! You should run  some good antivirus program and check your system!" [/COLOR][COLOR=Green]
 Upon this, I decided to make a fresh install, and installed Bodhi  Linux on my whole HDD, just for the purpose of  erasing everything that  was there.
The first result was encouraging: Knoppix USB booted again, instead of hanging after partition detection.
I am currently running the same Knoppix session, hope the freeze or shutdown issues have disappeared, too.
 for me it is still a question mark what has been happening all the  while, but if errors are now gone for good, I cant ask for more :)[/COLOR]

---

