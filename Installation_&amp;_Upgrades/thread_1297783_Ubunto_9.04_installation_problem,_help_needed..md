---
title: "Ubunto 9.04 installation problem, help needed."
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by trail_fairy on 2009-10-22
Hi folks,
After Vista updates killing my computer for the 3rd time in the last 6 months i decided to use something that worked properly.
Last time my pc crashed i tried to do a full system restore, but for some reason it didn't reinstall all of Vista, everytime i turn the pc on it goes straight to the system restore menu, but error messages appear if i try to run a restore.
 
So i downloaded Ubuntu 9.04 and copied it to a disc. When i boot the pc from the disc it goes to the select language screen and then to the installation menu.
I select to install Ubuntu as the only operating system and the installation starts. I get a minute of a progress bar and then pages and pages of text appear. Then the pc stops doing anything and leave me with.......
 
Traceback (most recent call last):
File "/usr/bin/ubiquity-dm", line 280, in <module>
ret = dm.run(*sys.argv [3:]
File "/usr/bin/ubiquity-dm", line 114, in run
raise XStartup Error, "X server exited with return code" +str(status)
--main--. XStartupError: X server exited with return code 1
 
0% Scanning disks...
0% Detecting file systems...
 
And the pc wont progress any further.
Any suggestions on what is wrong and what i need to do.
 
Please note, that i really only know a little about computers and know very little about programming and how they work.
Any help is greatly appreciated.
Thanks.

---

### Post by irw on 2009-10-22
A quick suggestion - have you tried checking the CD for any errors?
- boot from CD, initial menu includes an option to check the CD

I cannot work out what he error you are getting is, but during a recent install I was getting random errors -  different each time; when I checked the CD, it reported problems with it. New CD burnt -> no problems

---

### Post by trail_fairy on 2009-10-26
Thanks for the reply.
I booted up form the disc and ran the disc check, it all came back fine with no errors.
Ubuntu works if i choose the option to try Ubuntu without installing, but i just can't install it.
Ta.

---

### Post by Kyugetsuki on 2009-10-26
what pc is it? brand, type, whatever you can recall. just do tell

---

### Post by nexes128 on 2009-10-26
Does the system have an Asset Recovery(i can't actually recall the name of the service) option? if so there software (which resides on the BIOS) will block any attempts to change the partitions and that may be the problem.

---

### Post by trail_fairy on 2009-10-26
The computer, is a compaq/hp desktop. I'm afraid that's all the info i can give. 
Asset Recovery? When the computer is booting up, if you press F11 ( i think it was) it goesto a system recovery/repair/restore menu. Where i've tried Windows system restore to an earlier point, Windows system repair and Compaq full system factory restore.

I've just tried to install ubuntu form the icon on the desktop when just trying out ubuntu, it got to the part where i select my keyboard layout, then i got a cursor icon of spinnig dots (assuming that's the same as the hourgalss) and had that for last 20 minutes and nothing has happened.
Thanks.

---

### Post by matmuc on 2009-10-29
Hello,
I would like to join this thread, because I have exactly the same problem on one of my computers. I tried a Wubi-Install on my Notebook and  on my Desktop PC. Both run Windows XP Professional, SP3. No problems with the Notebook. But the Desktop PC comes up with exactly the same error message that trail_fairy reported.
I can start in safe graphics mode, but then I get a live session. I can configure this session, install the driver for my Nvidia card and adjust language and keyboard settings, but everything is forgotten, as soon as I shut down and reboot.
By the way, trail_fairy, does your PC use an Nvidia card?
I thought, I might join this thread to find out some common facts about the computers in use. I run a noname System without any exotic components and no Asset Recovery.
If you dont consider it useful to see the same error on another system, I am sorry for interfering with my post.
Greetings from Munich
Mathias

---

### Post by trail_fairy on 2009-10-30
If it is windows stopping the install from working properly, would it work if i uninstalled all windows items and installed from there. If this would help, how do i do it. Apologies if this is a stupid newbie idea.


Welcome Mathias, it's good to here i'm not the only person with this problem.
Cheers

---

### Post by matmuc on 2009-11-02
Hello trail_fairy,
no new answers, so far. I will go on searching the forums for someone who knows what is happening in line 114 and 280 of "ubiquity-dm". And I decided not to change anything about my hardware, because at the moment everything reminds me a bit of the early days of Windows 95 and OS/2, when the phrase "plug and pray" was created. I will keep you informed about any new informations.
By the way: I tried to install Ubuntu 9.1 - no chance! At a certain point, the system hangs and I can only switch it off.
I hope to come up with new informations soon.
Bye

---

### Post by trail_fairy on 2009-11-08
Just a quick update (especially for matmuc). Yay, Ubuntu is installed and working properly.

After no luck trying to install from the boot menu, i tried to install from the live desktop, the 1st time it just halted before the partition step. 2nd time it got to around 90% installed then an error message appeared (after this attempt any windows bits had gone), 3rd time it got to around 75% and an error message appeared stating my hardrive had corrupt/damaged segments. I ran a hardrive scan via the partition manger, no faults were detected. Straight away attempted install number 4 from the live desktop and it worked without a problem.
I don't know why it installed now and wouldn't before or what i've done, if anything, to sort the problem (quite frankly i'm just glad it's working).
Thanks for the advice guys and i hope you get yours sorted soon matmuc.
Cheers.

---

### Post by matmuc on 2009-11-15
Hey, you made it! Congratulations.
I am still struggling with the same problem, but right now I don't have enough time to try the same thing over and over again. Maybe I will try again one of the next weekends. Until then, I have my notebook running an almost complete install of Ubuntu. Have a good time!
Bye
Mathias

---

