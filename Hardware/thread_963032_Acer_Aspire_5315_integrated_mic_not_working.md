---
title: "Acer Aspire 5315 integrated mic not working"
date: 2008-10-29
forum: Hardware
---

### Post by BlackieC on 2008-10-29
Hello fellow ubuntu users,

This is my first report with a problem since Ubuntu provides such a great community support, except this time I haven't been able to find a solution. On the laptop it appears to have an integrated mic yet somehow I am unable to get it to capture sound. I have set all the levels in alsamixer to max yet still nothing, please help and solve this problem so i don't have to carry around an external microphone (I'm already on a external mouse because the touchpad stopped working). Thank you in advance.

edit: Since I'm a slight newbie if you need any other information then please say so and how I would retrieve it.

---

### Post by Black_Math on 2008-10-30
Hello there!

I got an Acer Aspire 9920 and I got the same problem, tried alot of threads using the alsamixer turning everything up, ending up in some horrid sounds :P. I managed to get it to capture faintly but under alot of background noise.

---

### Post by BlackieC on 2008-10-30
external mic then?

---

### Post by dantakeoff on 2008-11-20
exactly the same problem here... it worked fine with 8.04, but internal mic disappeared with 8.10, which goes to show its a software problem. ive looked everywhere and tried just about everything, to no avail...now i gotta lug an external mic around with me, how irritating is that...anyways, i think everyones just about given up trying to find a solution to this one. sorry.:(

---

### Post by PMA on 2008-12-19
Hello, I just installed Ubuntu 8.1 in a Acer Aspire 5102 and I also cannot capture sound with built in mike. Any suggestions?

---

### Post by dantakeoff on 2010-01-29
[QUOTE=gunnz]hi sorry for the late response.
if you still have the problem you could try to update the kernel to the latest stable version [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
then in sound settings set to pulse everything.if you can't select pulse install it from synaptic.in skype audio settings set to pulse also and then make a test audio to check it.
take a look at my post here [http://ubuntuforums.org/showthread.php?t=806555&highlight=gunnz&page=3](http://ubuntuforums.org/showthread.php?t=806555&highlight=gunnz&page=3) on how to install kernel and on post #27 about pulse.
if you have other questions pm me and i'll try yo help
all the best[/QUOTE]

mate youre a star....my post was up there for a loooong time, and meanwhile id got used to booting into xp if i needed to skype, completely unaware that it had been made possible to fix....so thanks again...
the internal mic works fine now(its under mic 2 in sound preferences/input/connector), and skype too, as long as i dont allow it to automatically adjust audio settings...problem solved.
peace...

---

### Post by dantakeoff on 2010-01-29
update your kernal to the most recent, it should work fine. once you have updated, you should find your internal mic if you reboot, right-click the volume control on your panel,click on sound preferences,input,and then microphone 2...do not set your input volume too high, though, or it wont work. you can test it by speaking and watching the input level....mine works best when the input volume is about one third up the meter...
thanks to gunz for that solution....

---

### Post by JonEK90 on 2010-04-20
[SIZE=2]Hi all,
[/SIZE] 
[SIZE=2]I think this is the most up to date thread on this long running issue.
I am using:
Linux Acer7735Z 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

on my Acer Aspire 7735Z laptop which has Acers 'Crystal Eye' camera and integrated (builtin) microphone.[/SIZE] 

Originally I did not have 'Microphone 2' as an option - but adding
[FONT=Courier New][I][I]alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer

[/I][/I][FONT=Arial][SIZE=2]to [/SIZE][/FONT][FONT=Arial][SIZE=2]/etc/modprobe.d/alsa-base.conf did give me that option but it is still not picking up any sound.

gunnz advised building the most recent kernel - but can anyone tell me if that is required (give me anything more) than my current 2.6.31 version?

Secondly, this thread does not mention having to install Alsa drivers - is that unnecessary or even a problem with the most recent kernel?

Finally, the Alsa GUI mixer I have only shows two pairs of stereo sliders (Master & Capture) - is that what I should expect to see? (I am wondering if Mic 2 is muted in software somewhere?)

I would really like to get this working as it's the main defect I have found with Ubuntu.

Many thanks,
 - jon.[/SIZE]     


[/FONT][/FONT]

---

### Post by lidex on 2010-04-21
Rather than doing the kernel thing, you can try installing the alsa-backports (karmic). Info here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Or upgrade alsa using the script linked to in my sig.

---

### Post by tb1991 on 2011-04-09
> **JonEK90 said:**
> [SIZE=2]Hi all,
[/SIZE] 
[SIZE=2]I think this is the most up to date thread on this long running issue.
I am using:
Linux Acer7735Z 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

on my Acer Aspire 7735Z laptop which has Acers 'Crystal Eye' camera and integrated (builtin) microphone.[/SIZE] 

Originally I did not have 'Microphone 2' as an option - but adding
[FONT=Courier New][I][I]alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer

[/I][/I][FONT=Arial][SIZE=2]to [/SIZE][/FONT][FONT=Arial][SIZE=2]/etc/modprobe.d/alsa-base.conf did give me that option but it is still not picking up any sound.

gunnz advised building the most recent kernel - but can anyone tell me if that is required (give me anything more) than my current 2.6.31 version?

Secondly, this thread does not mention having to install Alsa drivers - is that unnecessary or even a problem with the most recent kernel?

Finally, the Alsa GUI mixer I have only shows two pairs of stereo sliders (Master & Capture) - is that what I should expect to see? (I am wondering if Mic 2 is muted in software somewhere?)

I would really like to get this working as it's the main defect I have found with Ubuntu.

Many thanks,
 - jon.[/SIZE]     


[/FONT][/FONT]

Hi,

i have the same laptop as JonEK90. I already tried somethings but nothing works for me. Could somebody please answer how i can configure my mic at a simple way cause I'm new to Linux.

thanks

---

