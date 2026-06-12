---
title: "Big installation bumps, assistance?"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by Fuzz Pucker on 2009-08-15
Hello, I'm very, very new to Linux, and Id appreciate your help. I'm trying to install for the first time, but I'm running into a couple problems or concerns...

First off I'll state I burnt an Ubuntu ISO to a DVD, oh maybe 6 monthes ago. I'm think it's somewhere inbetween version 7.1-7.9, but I'm not really sure. I decided to get into Linux now, and why let the disc go to waste? So I decided to use it because it is my understanding once installed it is very easy to update to the newst version. I'd be fine burning the newst Ubuntu (9.04?) if it will help me out.

I am running Vista x64 originally (I know, I know) and I intend to keep it for familiarity and gameing purposes. So when I attempt to install Ubuntu, I go to the manual partitioning menu, because I want to keep my Windows patrition untouched. I read somewhere, (I forget) to have one Ext3, and one Swap mounted with "/". So, I did this and continued to install. When it got to the actual installation part where the files were copied to the hard drive ect. about halfway down the road I got an error message that said something to the effect of "The file (blank) on the hard drive does not match the file on the CD-ROM." It also gave me reasons why this might be such as a bad DVD-ROM drive, or HDD. So I decided to click "retry" about a thousand times and it eventually told me to shove it and go away (Not really). So I hit the big RESTART button and tried it all again, same turnout. I registered on this fourm, and thought I had better get some error messages to help you guys help me. So as I tried to install for the third time to copy down the error messages, it magically worked without a hitch, no error messages at all (go figure, hey?). As far as logging in and going to system, administration, update manager; it seems to be working fine. Thats all Iv'e done so far.

Now, my first question is the file system/swap partition, Is this acceptable (Ext3 for Ubuntu, and swap which is 4GB big also mounted with "/")? 
Secondly, should I be concerned about those errors even though they disappeared the third time around? I am confident my HDD and DVD-ROM are functioning correctly. 

Thanks for your time in advance, after all I'm just another one of those newbs who needs some help.

---

### Post by cmannnn on 2009-08-15
hay it worked as far as the disc is concerned if i were you id burn or order a new one from ubuntu.com so you don't run into that problem or you can boot off it and choose check disc

---

### Post by Fuzz Pucker on 2009-08-15
Okay, Thankyou. I think I just may order one from ubuntu.com.

I have another question, and I think its about GRUB. I do remember reading GRUB is what controls the other Operateing Systems booting, and I have a problem with it. It sets up Ubuntu as the first choice, so if the computer is turned on with no interception, it will automaticialy load into Ubuntu. This, for me is a problem because I have Wake on Lan enabeled on my PC, it turns on, auto logs into Windows, starts up my VNC server so I can acess it then shut it back down; all done over the internet with no physicial interaction at my PC. There is no way to remotely control what it boots into, so unless Windows is the first choice, this isnt going to work out well for me. Is GRUB not configureable as to which is first on the list?

---

