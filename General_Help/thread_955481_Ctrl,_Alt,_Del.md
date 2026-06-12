---
title: "Ctrl, Alt, Del"
date: 2008-10-22
forum: General Help
---

### Post by Quarkrad on 2008-10-22
New HD and new install of Ubuntu but Desktop keeps locking up - most annoying, especially for wife who is OK to change from WinXP but 'just wants something that will work'.  I have all sorts of strange things happening, graphics wise.  Everything is dead apart from the mouse curser movement - clicks do not work.  To get out of the lock up is there a Linux equiv of Ctrl/Alt/Del or is just a case of crashing the PC?

Thanks....

---

### Post by mali2297 on 2008-10-22
Well, you can raise some [skinny elephants]("http://en.wikipedia.org/wiki/Magic_SysRq_key"). It's boring, but better than pressing the power button.

---

### Post by prshah on 2008-10-22
> **Quarkrad said:**
> New HD and new install of Ubuntu but Desktop keeps locking up - I have all sorts of strange things happening, graphics wise.  Everything is dead apart from the mouse curser movement - 
To get out of the lock up is there a Linux equiv of Ctrl/Alt/Del 

> **mali2297 said:**
> Well, you can raise some [skinny elephants]("http://en.wikipedia.org/wiki/Magic_SysRq_key"). It's boring, but better than pressing the power button.

Elaborating...

1) To gracefully recover from a lock;

Alt+SysRq+R (Remove keyboard control from X)
Alt+SysRq+E (End all running tasks)
Alt+SysRq+I (kIll remaining (hanging) tasks)
Alt+SysRq+S (Sync unwritten data to disk)
Alt+SysRq+U (Unmount filesystems)
Alt+SysRq+B (instant reBoot)

The keys sometimes _may_ not work, if the hang is hardware based.

2) If you restart after an improper shutdown, the disks are immediately checked. 

3) Check if you have setup [pulseaudio properly]("http://ubuntuforums.org/showthread.php?t=776739").

4) You may not be running the correct drivers for your graphics card, or it may not be setup properly. Check the following, then post back for resolutions:

    a. Press Alt+F2, give the command
 ```

    displayconfig-gtk

```
    Click on the "Graphics Card" tab, and note which driver is in use.
    b. Now open a terminal (Applications-Accessories-Terminal) and post the output of the below command
```

    lspci -v | grep -E -A 5 -B 1 -i vga\|graphics

```

---

### Post by ad_267 on 2008-10-23
Sounds like there's issues with your hardware not working well with Linux, that's too bad.

There is something like control-alt-delete if you go to system - administration - system monitor where you can kill programs that aren't responding. You can also add an applet to your panel that you can click on and then click the window of any application that isn't responding to kill it. Usually with Ubuntu if one program isn't responding then everything else still works fine.

---

### Post by Quarkrad on 2008-10-23
Thanks - I did ask about motherboard/chipset drivers on another post but had no feedback.  (I don't have any hardware - everything is plugged into the motherboard - foxconn winfast 760GXK8MC - I'm using a standard wired mouse and a monitor). When the pc locks up I get mouse movement but no response to the buttons - I am keen on this applet to see if the mouse responds if it is visible on the screen. How do I go about finding out about instructions to get this applet on the screen?   This maybe a possible solution - I would like to stay with Linux.

---

### Post by DrMelon on 2008-10-23
Hmm, sounds like the Window Manager is playing up. Do you know what Graphics Chipset you have in your motherboard? We might be able to find alternative drivers you see.

---

### Post by Bucky Ball on 2008-10-23
How much RAM?

---

### Post by ad_267 on 2008-10-23
You can just right click on the panel (top or bottom) and select "Add to panel" and it should be called something like "Force quit." 

There are other options for killing unresponsive programs like if you can press Alt+F2 to bring up the run application dialog and run "xkill" and then click on the window. You can also switch to another TTY and use the killall or kill command, but that's getting a bit more complicated.

You might want to try a different desktop environment like XFCE, which is used by xubuntu. That might run better on your computer.

Bucky Ball: It has 500 MB ram.

---

### Post by Bucky Ball on 2008-10-23
> **ad_267 said:**
> You can just right click on the panel (top or bottom) and select "Add to panel" and it should be called something like "Force quit." 

There are other options for killing unresponsive programs like if you can press Alt+F2 to bring up the run application dialog and run "xkill" and then click on the window. You can also switch to another TTY and use the killall or kill command, but that's getting a bit more complicated.

You might want to try a different desktop environment like XFCE, which is used by xubuntu. That might run better on your computer.

Bucky Ball: It has 500 MB ram.

Thanks. Like ad said, I would definitely go the Xubuntu route. Try the alternate install. I have a couple of computer's rock solid (including the wife's!) and we couldn't be happier. Then I have a Ubuntu Studio install on my desktop for playing.

Your suggestion earlier might be a good one - keep an install on one of your personal boxes and then when you feel like you are across it, try again. Incidentally, why can't you run internet in both OSs and just dual boot?

---

### Post by Quarkrad on 2008-10-23
Thank you for replying. Sorry to be long getting back.

MB                    Foxconn Winfast 760GXK8 MC
Chipset               Foxconn SiS760 Athlon 64
Memory                WinXP & SiSandra reads as 896MB
BIOS                  10/08/2005-SiS760-6A717FKAC-00

I have read that there are issues with Foxconn motherboards in that they support windows but have problems with Linux.  One one post there was a quote:

 "...Debian developer (and Ubuntu employee, I think) Matthew Garrett says that as long as you run a kernel greater than 2.6.9, this whole uproar is about nothing...."

this may be my problem. How do I find out my Kernel version?

---

### Post by lifestream on 2008-10-23
You can type:
```
uname -a
```
in a terminal, to see what the version is.

---

### Post by Quarkrad on 2008-10-24
Readout shows:

Linux liz-winfast 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

looks like my motherboard (might??) be OK.  I was half hoping it was the motherboard as changing it out would solve the problem and I could use Linux - if the mb is OK I am left with this lock up problem.  Shame - I don't have anything special in terms of pc spec, disappointing that winxp is a solid as a rock and Linux very flaky.  Not sure where to go now apart from winXP.

---

### Post by melojo on 2008-10-24
> **Quarkrad said:**
> Readout shows:

Linux liz-winfast 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

looks like my motherboard (might??) be OK.  I was half hoping it was the motherboard as changing it out would solve the problem and I could use Linux - if the mb is OK I am left with this lock up problem.  Shame - I don't have anything special in terms of pc spec, disappointing that winxp is a solid as a rock and Linux very flaky.  Not sure where to go now apart from winXP.


You must use what works, I for one find ubuntu linux rock solid and a more secure and stable os.  I  have 3 systems 2 home made and 1 hp laptop all run without a glitch.  The only real problem I encountered was the laptop wireless pcmica card, but after googeling I found a solution.

---

### Post by bapoumba on 2008-10-24
I've moved the thread to General Help.
To the OP: you should suggest a new thread title. Not very informative, for now ;)

---

### Post by ByteJuggler on 2008-10-24
Lockups like you describe are really not normal.  Linux if anything has far less of the problems you describe than Windows.   Usually such problems (on both Windows and Linux) are either due to:
1) Incomplete/buggy drivers
2) Flaky hardware problems, often falling into one of the following categories:
- Corruption/Crashing due to RAM issues 
- Corruption/Crashing due to HDD controller issues
- Corruption/Crashing due to videocard issues (RAM, overheat ...)
- Corruption/Crashing due to CPU (voltage/temperature issue)

In my experience, one of the most common problem often is flaky/broken RAM, so my first question to you is: Have you run the memory tester available on the Ubuntu LiveCD boot menu for a couple of hourse without reported errors?

Also, what temperature is your CPU running at? (There are sensors you can add to your desktop to tell you the CPU temperature, I'd like you to try and add that so you can see your CPU temp.)

HTH.

> **Quarkrad said:**
> Readout shows:

Linux liz-winfast 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

looks like my motherboard (might??) be OK.  I was half hoping it was the motherboard as changing it out would solve the problem and I could use Linux - if the mb is OK I am left with this lock up problem.  Shame - I don't have anything special in terms of pc spec, disappointing that winxp is a solid as a rock and Linux very flaky.  Not sure where to go now apart from winXP.

---

### Post by Bucky Ball on 2008-10-24
I would go here:

[http://torrent.ubuntu.com/xubuntu/releases/hardy/release/alternate/](http://torrent.ubuntu.com/xubuntu/releases/hardy/release/alternate/)

Torrent the version for your machine, burn slowly (simmer), and if that doesn't work, sometimes more RAM does. If it doesn't, back to Windoze (or a distro that works, try another , there are many). But, sounds like you want to upgrade anyhow, so no reason not to do that either and if you want to run Ubuntu, follow the recommended hardware guides. :)

[http://torrent.ubuntu.com/xubuntu/releases/hardy/release/alternate/](http://torrent.ubuntu.com/xubuntu/releases/hardy/release/alternate/)

Although dated and not 'off the shelf' machines, sounds like you might go for the build using existing bits anyhow.

---

### Post by poldie on 2008-10-24
> **ad_267 said:**
> Sounds like there's issues with your hardware not working well with Linux, that's too bad.

There is something like control-alt-delete if you go to system - administration - system monitor where you can kill programs that aren't responding. You can also add an applet to your panel that you can click on and then click the window of any application that isn't responding to kill it. Usually with Ubuntu if one program isn't responding then everything else still works fine.

There's also control-alt-backspace which lets you log in again. I'm new to this Linux malarky but I believe it starts a new X windows session. Possibly.  Give it a go.  I found it accidentally, and when I googled I saw discussions about whether it should be something which only happens after you've held the keys down for 2 seconds, but that's certainly not what happens in Ubuntu 8.4.1, where it's instant.

---

### Post by Quarkrad on 2008-10-24
CPU temp  32 degrees
Run live CD memory test for 2 hrs - no errors.  I have emailed foxconn re issues with their motherboards running Linux.  Frustrating in that I now duel boot with winXP and windows is, as always been, rock solid.  When ever I have installed windows on PC I have installed OS, then chipset drivers, than apps.  I am wondering if I need Linux specific drivers for my motherboard.  Some comments suggest Linux is a better OS but why is winXP rock solid but Ubuntu keeps locking up?   It has to be the motherboard.  (Installed Ubuntu - duel boot - on my other desktop and it is running like a rock.  Old HP oem motherboard with 2.0GH cpu and old ati graphics card.  Very pleased with this install. p.s. this is second re-install on wifes PC so it is probably not an install issue).

---

### Post by ByteJuggler on 2008-10-24
> **Quarkrad said:**
> CPU temp  32 degrees
Run live CD memory test for 2 hrs - no errors.  I have emailed foxconn re issues with their motherboards running Linux.  Frustrating in that I now duel boot with winXP and windows is, as always been, rock solid.  When ever I have installed windows on PC I have installed OS, then chipset drivers, than apps.  I am wondering if I need Linux specific drivers for my motherboard.  Some comments suggest Linux is a better OS but why is winXP rock solid but Ubuntu keeps locking up?   It has to be the motherboard.  (Installed Ubuntu - duel boot - on my other desktop and it is running like a rock.  Old HP oem motherboard with 2.0GH cpu and old ati graphics card.  Very pleased with this install. p.s. this is second re-install on wifes PC so it is probably not an install issue).

Well given the above, and the fact that you've mentioned graphics problems in your first post my suspicion would lie with the graphics drivers for your graphics chipset in Linux/Ubuntu.  Video cards/drivers misbehaving can easily cause a system to be unstable/crash etc.  

If you'd like to test this hypothesis, then you can perhaps try forcing the system to use the "vesa" generic driver which is a bit crap and slow but should always work.  If you'd like to test this, then edit your /etc/X11/xorg.conf fiel with the command 
```
gksudo gedit /etc/X11/xorg.conf
```
then find the secion starting with:
```
Secion "Device"
```
and add a line saying:
```
     Driver "vesa"
```
Then save the file and reboot your system.  It should bootup using the vesa driver (probably with a less than optimal resolution.)  But, it should be stable.  If your system is indeed stable using the "vesa" driver then you've at least identified where your instability is coming from and you can try addressing that issue directly.

---

### Post by Riffer on 2008-10-24
Hi checked your post history and did a quick search on your MB specs.  Your ongoing problems looks like they're hardware related, specifically your onboard graphics.  The graphics chipset is not well supported by Linux (and therefore Ubuntu) and will cause lockups.  

You may be able to fix it by using older work arounds but the ones I've found are out dated and require that you do alot of manual configuring etc.  Or you could try buying a newer low end graphics card that is supported by Linux.  Or try ByteJuggler's suggestion, you could at least get basic graphics working.

I can well understand if you do go back to Windows, perhaps when you buy a new computer you'll try Ubuntu again.  In either case good luck.

---

### Post by Quarkrad on 2008-10-25
Riffer - thanks, you may have hit the issue.  I suspect Foxconn are not going to admit there is a problem with the graphics chip.  I do not want to go back to windows so will source a graphics card and see if that does the trick.  Appreciate your help.

---

### Post by 3rdalbum on 2008-10-25
Is there a reason why you can't just run with normal 2D graphics? And which graphics chip does your motherboard use?

Can I guess: Nvidia?

There might not be actually something wrong with the graphics chip, but instead a problem with flaky proprietary drivers. Also note that there is a newer version of the Nvidia driver than is available from the Hardware Drivers program; it's just been released this month. It could solve your problems. It solved some of mine.

---

### Post by Bucky Ball on 2008-10-25
I'm with 3rdalbum. Incidentally, can we hear the 3 albums anywhere? :)

---

### Post by Riffer on 2008-10-25
> **3rdalbum said:**
> Is there a reason why you can't just run with normal 2D graphics? And which graphics chip does your motherboard use?

Can I guess: Nvidia?



No its a SiS chipset, completely different company.  I believe that Trident bought them out a few years back.

---

### Post by Quarkrad on 2008-10-30
Good news - so far.  New graphics card arrived - GeForce 6200.  Been in for thee days and no lock ups or problems with graphics.  Many thanks for all your help - looks like the sis chipset was just too old.

Rds...

---

### Post by ByteJuggler on 2008-10-30
> **Quarkrad said:**
> Good news - so far.  New graphics card arrived - GeForce 6200.  Been in for thee days and no lock ups or problems with graphics.  Many thanks for all your help - looks like the sis chipset was just too old.

Rds...

Glad your problem is sorted (touch wood.)  Ask away if you have any other problems.

---

