---
title: "Cannot suspend with SD card inserted - Dell Mini 9"
date: 2009-01-21
forum: Hardware
---

### Post by Freq18Hz on 2009-01-21
Symptom:

With an SD card inserted, the machine will not suspend.  On a reboot, with SD card inserted, suspend works once.  After that, the computer will not suspend, or shutdown, even if I physically remove the SD card,  I still have to manually hard boot the machine.  I have also tried using software eject in nautilus, which does not help the issue.

This is reproducible every single time using the above scenario.  

When the issue occurs, the machine looks as if it is going to suspend, in that the screen goes black as expected, but it just hangs at the cursor and does nothing.  Usually if I press a key, the login screen comes back, but if I shutdown, I cannot get the login screen to reappear.  Opening a terminal via alt+F2 and restarting gnome-session does not work.  

If the SD card is not inserted upon reboot, the machine suspends and shuts down just fine, every single time. 

Steps:

1. With SD card inserted, Power on machine
2. Log in
3. Wait for wireless to connect/services to start
4. Click user login menu, select suspend
5. After machine suspends, wake it back up
6. Log back in
7. Suspend machine again

Result:  After step 7, the screen goes black, but the machine does not appear to suspend (light on the front of the system does not blink.  Pressing a key usually brings the login screen back.  If you attempt to suspend again, even if you remove the SD card, it will not suspend.  If step 7 is replaced with Shutdown/Restart machine, the machine will not shutdown or restart, and only a black screen with a blinking cursor is shown.

Notes:
After using tail to follow /var/log/messages and /var/log/syslog it appears that there is a GPF occurring, and some message about the kernel.


Config:

Dell Mini 9, 1GB ram, 8GB SSD, 16GB SDHC 6X, Ubuntu 8.10 (installed updates)


I don't really know enough about Linux to debug these.  Does anyone have a solution/fix for this, or have any advice on how I can proceed to try and debug this?

Thanks much,

-Freq

---

### Post by pmreimer on 2009-01-22
Use less butter.

---

### Post by Freq18Hz on 2009-01-22
anyone?
:popcorn:



-Freq

---

### Post by yooy on 2010-05-08
sudo gedit /usr/sbin/pm-suspend

go to the fist line which is not bashed (#), which is:

export STASHNAME=pm-suspend

just before this line, you add

umount /dev/mmcblk*

works with Karmic and Lucid 

Hopes it helps

---

### Post by ianmillington on 2010-05-10
There is a fairly well-documented issue with the Acer Aspire One SDHC card where suspending or hibernating the machine apparently trashes the filesystem on the card. 

Please can you advise whether the code shown will fix that issue?

Thanks

---

### Post by yooy on 2010-05-10
Well I can't confirm it myself but see here (post from [scross01]("http://ubuntuforums.org/member.php?u=1071202")) 
[http://ubuntuforums.org/showthread.php?p=9269450#post9269450](http://ubuntuforums.org/showthread.php?p=9269450#post9269450)

I'll try to do it on my wife's aspire one later in the week but according to our friend it works

---

### Post by ianmillington on 2010-05-10
Thanks, look forward to hearing

Like you, the netbook belongs to my wife so I have been reluctant to try it, as I am sure she would be thrilled - I've never found a way to recover the situation other than to reinstall. To add to this, like many I'm sure, the L\H SD card is the home partition.

---

### Post by ianmillington on 2010-05-12
Having re-read the thread you linked to, it would appear that the fix does not sort things out where the home directory is on the SDHC card. 

In a way I wish I had bought her the HDD version now, but suspect that I would not have been permitted to wipe windows.

---

### Post by yooy on 2010-05-12
Wait, I doubt your (her) home partition is on her SDHC card. The guy on the other thread owns a Dell mini 9 with a very small SSD disk (4G) so he had to put his home partition on his SDHC card but it's not a very common way to install an operating system. 
Don't you mistake SDHC for SSD? (no offence)
Acer didn't sell Aspire one with such small SSD, so I can't see a reason why you put the home partition on the SDHC (of course you do what you want :P )

Am I clear? English is not my first language as you had realize by yourself :)

---

### Post by yooy on 2010-05-12
I'm not sure I got it : why would you not have been permitted to wipe windows on the HDD version of the Aspire One? I'm a little but confused here :P

---

### Post by ianmillington on 2010-05-12
Thanks for the response

The machine has 2 "disks" an 8Gb SSD and an 8Gb SDHC card in the left hand slot. 

They have been formatted so as to maintain a separate home partition so the SSD card has / (ext 4) and swap and the SDHC card has home (also ext 4). When the machine arrived with Linpus the sdhc card was solely for expansion purposes and I suspect that arranging things the way I have done is part of the problem.

---

### Post by ianmillington on 2010-05-12
> **yooy said:**
> I'm not sure I got it : why would you not have been permitted to wipe windows on the HDD version of the Aspire One? I'm a little but confused here :P

My wife probably would have sworn at me if I had, or forbidden me to do so:)

---

### Post by yooy on 2010-05-12
> **ianmillington said:**
> My wife probably would have sworn at me if I had, or forbidden me to do so:)
HO! I see :P I suspected something like that.

Well, I'm surprised that so many people use their SDHC card like that but there are probably many reasons. And yes, since your home is on the SDHC, of course you can't unmount before suspending... This is not a bug, this is pure logic actually. And I doubt you can do something, but I'm just an average user of ubuntu....

But personally, my system is entirely on my 8Go SSD (and take the half only) and I have 8 and 16Go SDHC card for additional storage. And of course this way I can suspend with the little trick we're discussing here

good luck

---

### Post by ianmillington on 2010-05-12
IIRC when it came with Linpus, the whole system was on the SSD and the SDHC card was allocated to expansion, and the whole thing got reported as one. 

So when you installed ubuntu (presumably it had linpus pre-installed) how did you deal with the SDHC card during the install - did you not allocate it to anything?

---

### Post by ianmillington on 2010-05-12
Just to follow I have read on a guide that one way to configure things is for the SDHC card to be configured as /media/Data. How do you set yours up please? 

The other question on that is that if you say have files open on the disk does that cause a problem if you suspend or hibernate, as it will still be mounted?

Thanks

---

### Post by yooy on 2010-05-12
I didn't pay enough attention to what you wrote and I missed a point. Actually, it seems to me that the trick would probably work for you since you have allocated the SDHC card to home partition and nothing else. On the other thread I linked previously, the guy installed UNR on the SDHC card which caused a logical problem : it's part of the GUI and Ubuntu can't unmount it. On your home partition I think you will have nothing that will cause the same problem. Just personal data...

To answer to your question ("how did you deal  with the SDHC card during the install - did you not allocate it to  anything? " 	  	) : no, I didn't. It means that I lose the "integrated extension" if can say  that. Now I have (actually my wife ) the SDHC card mounted the usual  way, on the desktop.

---

### Post by ianmillington on 2010-05-12
Thanks for the reply. I'll give it a go when I'm feeling brave and there's enough time to rectify if it goes pear-shaped! :-)

---

### Post by yooy on 2010-05-12
> **ianmillington said:**
> Just to follow I have read on a guide that one way to configure things is for the SDHC card to be configured as /media/Data. How do you set yours up please? 

The other question on that is that if you say have files open on the disk does that cause a problem if you suspend or hibernate, as it will still be mounted?

Thanks

as you probably understood mine is the usual way (just /media) but it seems to be a good idea. I'm not sure of the output however. 

Your second question is a good question. I never hibernate by the way, just suspend...I will ask to my wife or try it myself with her Aspire One. I have to admit that with my Mini 9 I use the SDHC card as a back-up storage. I will try with my dell and I'll give you the result asap.

---

### Post by yooy on 2010-05-12
> **ianmillington said:**
> Thanks for the reply. I'll give it a go when I'm feeling brave and there's enough time to rectify if it goes pear-shaped! :-)
  :-D good luck then, and keep us posted. Anyway, I don't think that you can harm your system.

---

