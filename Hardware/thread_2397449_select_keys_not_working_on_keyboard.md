---
title: "select keys not working on keyboard"
date: 2018-07-29
forum: Hardware
---

### Post by bholtemeyer on 2018-07-29
Hi all,  
 
I’m having having trouble with the keyboard on my Dell Precision M4400 keyboard ... but it’s a long story!

 1) My machine was not turning on reliably. After some research, it seemed like* the most likely* culprit was the motherboard.
 2) I purchased another M4400 machine for parts. I’ll call this my “new” machine. The new machine lacked a hard drive.  
 3) I powered the new machine up without making any changes. Since it lacked a hard drive, I just explored the BIOS. I noticed that the ENTER button was not working.
 4) After moving the hard drive and keyboard from the old machine to the new machine everything seemed perfectly normal (I started it and ran a few programs). I didn’t do a thorough keypad test, but the ENTER key was definitely working. But then I had to keep making changes ... 
 5) I decided to move my RAM from my old machine to my new machine since the old machine had 8 GB and the new machine only had 4. I did this while the machines were disconnected from all power.  
 6) Upon restarting the new machine, 9 keys did not work: z x c v m , . RIGHTSHIFT and ENTER. It seems like a strong coincidence to have key issues on both keyboards when I have never had any keyboard issues in the past. 

 Things I’ve tried: 

 - reseating the keyboard
- switching the two keyboards
- upgraded from Xubuntu 17.10 to 18.04 (I was thinking that perhaps this was a driver issue. I had planned to do that upgrade anyway.)
- multiple restarts. 
- using an external keyboard (that works fine)

Here is the system info that I currently am running (courtesy of -neofetch-): 

OS: Ubuntu 18.04.1 LTS x86_64 
Host: Precision M4400 
Shell: bash 4.4.19 
Kernel: 4.15.0-29-generic 
DE: Xfce 
WM: Xfwm4 
Terminal: xfce4-terminal 
CPU: Intel Core 2 Duo T9600 (2) @ 2. 
GPU: NVIDIA Quadro FX 770M 

One of the simpler theories that there is an issue with the port into which the keyboard fits into? Or a driver issue? Any suggestions are very appreciated!

---

### Post by Autodave on 2018-07-30
Sounds like a hardware issue and not a software issue. Is that one of those Dell machines that use the ZIF connectors? If so, are you properly installing the cable? There is a tab that you need to pull up to release the cable. After inserting the cable back in and making sure that it is fully seated, then you push the retaining tab back into place.

---

### Post by bholtemeyer on 2018-07-31
> **Autodave said:**
> Sounds like a hardware issue and not a software issue. Is that one of those Dell machines that use the ZIF connectors? If so, are you properly installing the cable? There is a tab that you need to pull up to release the cable. After inserting the cable back in and making sure that it is fully seated, then you push the retaining tab back into place.

Thanks Dave. I don't believe it's a ZIF connector. I took a screenshot of what my keyboard looks like. The connection is "below" the space bar and clickers. 
 [ATTACH=CONFIG]280604[/ATTACH]

---

### Post by bholtemeyer on 2018-08-17
Does anyone else have any ideas? Much appreciated!

---

