---
title: "Ubuntu 15.04 &amp; Nvidia GTX660 : very poor resolution!"
date: 2015-05-23
forum: Hardware
---

### Post by Fr-Gilou27 on 2015-05-23
I just tried  Ubuntu 15.04 on my computer (Nvidia GTX660 + IIyama Vision MasterPro 510 CRT Monitor).

       I get a very poor display resolution:
           - (800 x  600 and  1024 x  768 ) using the native driver supplied with the package
           - (800 x  600 ; 1024 x  768 ; 1152 x  864 and 1300 x  768 )  using the Nvidia proprietary drivrer 346.59
       With the same hardware I get  20 different resolutions from (800 x 600) to (2560 x 1600) with Windows Seven!!
                     
       Where is the problem ? It is not a hardware problem, obviously.
       I'm 99% convinced that there is also no driver issue. Here is why :
                  In 2008 ,  I experienced a similar problem with Hardy Heron  with another Nvidia graphic system but the same CRT monitor:  
                   - only  (800 x 600) available with Hardy Heron compared to (2048 x 1536) available with Windows XP.           
                  
                  I was told on a Help Forum that the problem occured because the monitor did not supply any information to the Operating System
                  regarding which resolutions it was actually able to handle.
                  Witout information from the monitor, the windows OS offers the user to choose between all the resolutions that can be safely handled by the driver board
                  whereas the Ubuntu system, for whatever silly reasons, only offers the lowest resolution available.
                  
                  This problem was resolved by patching some configuration file inside Ubuntu.  And the whole system worked fine for several years at (2048 x 1536) as well as (1920 x 1440) !

       Hence I am quite sure I'm today in a silmilar situation and I have to tell to the Ubuntu System that my monitor is able to handle much more  than  (1152 x 864) !   
       How shall I proceed  ?  

       Thank you for your help

---

### Post by dino99 on 2015-05-23
the difference between Hardy time and now is mainly that now the kernel directly deals with X, so xorg.conf is now needed only for special config: multi screens, hardware detection issue . So xrandr and/or dmidecode can be used to set the required line entries. But i suppose you might see some warnings/errors logged (dmesg, xorg.0.log) about wrong display detection (lspci -vvnn)

---

### Post by grahammechanical on 2015-05-23
There could be two possible causes. a) A video connection with VGA will limit resolutions. I have found that to be the case with digital monitors.  b) Modern versions of Linux do not come with an Xorg config file because they expect to get the appropriate (optimum) resolution from the monitor's EDID (Extended Display Identification Data) during the loading process. This is why when we install Ubuntu we do not need to set screen resolutions and refresh rates which ordinary people might not know anything about and so might set the wrong resolution. So, it is not really a silly reason after all.

[http://en.wikipedia.org/wiki/Extended_Display_Identification_Data](http://en.wikipedia.org/wiki/Extended_Display_Identification_Data) 

To create our own Xorg configuration file, which I think that you need to do because you have a CTR monitor, there is this.

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

Regards.

---

### Post by Fr-Gilou27 on 2015-05-24
Thank U both for answering , Dino99 and grahammechanical !

      _Dino99_
 You may have noticed that I'm not that familiar with Ubuntu... nor with programming !  Basically I'm a retired harware engineer and my
   software knowledges are restricted - (as are, unfortunately, my knowledges in English and my skills in searching the net ...)
 Hence, your answer appears to me a little bit "hermetic" .
 Nevertheless, lets be positive: (The only thing I'm rich of is time, I hope I'll not waste yours.) So from what I understand:
[LIST]
[*] X stands for the graphic subsystem of the UBUNTU Operating System 
[*] xorg.conf: looks like the file containing configuration instructions for X . (Most probably the file I was instructed to modify at Hardy time ) 
[*] "xrandr" and "dmidecode" are most likely  "commands"  to be used on in the  commmand line in a terminal. As these commands are totally unknown
  to me, could you provide me with a link towards their references (what do they do, what are their parameters etc)  ? 
[*] (dmesg, xorg.0.log) is (are ?) probably files containing error message(s). Until now I didn't find anything alik through the whole UBUNTU Directory tree 
[*] (lspci -vvnn) sounds like another command with a parameter ??? 
[/LIST]
 Sounds like I've plenty of things left to learn ... Thanks for your help

        _grahammechanical_

   Forget about cause a) . The hardware -including connection - doesn'nt change when i boot my computer with Windows or with Ununtu! In other words,
   the "electrical" information that is available  from the monitor is strictly the same in both case. What this information is used for is a matter of software only.

   From the remainder of your post, I am understanding that "modern" UBUNTUs expect to get appropriate information from the monitor, in order to make 
   installation of the OS more easy . Fine . But that's only one half of the way ...
   Totally depriving the user from any possibility of adjusting these all parameters is against what I thought was the "Philosophy of UBUNTU".
   Hence there must be a way left - even an uneasy one - for providing the OS with the information it doen't get from the monitor.
   
   Anyway, thank you again for your help. Now I'll follow your links and try to learn more.  I'll keep you informed.

---

