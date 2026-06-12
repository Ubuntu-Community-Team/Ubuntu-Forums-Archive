---
title: "&quot;CUPS server could not be contacted&quot; printing problem"
date: 2005-12-09
forum: Hardware &amp; Laptops
---

### Post by mangocrazy on 2005-12-09
I'm very much an Ubuntu (and Linux) newbie, and have installed Breezy on my computer and my wife's. On my wife's computer she can print from Ubuntu to our LAN/print server attached Lexmark Optra L. When I try to check the status of my printer subsystem by going System > Administration > Printing from the Ubuntu desktop, all I get is this message:

**Error**

**The CUPS server could not be contacted.**

I have checked using sysv-rc-conf and cupsys is on at runlevels 3, 4, 5 & S. Also at bootup the CUPS system appears to start OK (it shows as OK in the list of subsystems that Breezy activates prior to user login).

Is there anything I should be doing to activate printing on my PC? I don't even get as far as the 'add new printer' icon that I used on my wife's PC. Any help would be appreciated.

One other thing - Lexmark supply drivers for my printer under Debian - GNU Linux on their site; are these the ones to use? I have downloaded the "print-drivers-linux-glibc-x86.deb" file to my desktop but am now at a loss to what to do with it. Again, any help etc...

Graham

---

### Post by amohanty on 2005-12-09
To install the drivers you would need to do a :

```
dpkg -i print-drivers-linux-glibc-x86.deb
```

Also if it is a print server based printer I think you can configure it as an IPP printer. So in System->ADdministration->Printing 
goto the Global Settings menu item and select Detect LAN printers and see if that works.

Or in the add printer dialog, select the Network Printer option and specify the IP of the printer.

HTH

---

### Post by mangocrazy on 2005-12-09
amohanty,

Thanks for the info about installing .deb packages. I'll try that later.

But my problem is that the System > Administration > Printing dialog terminates before it will allow me to do anything. I can't even get to the 'Add Printer' dialog. 

The error message I get has a big red 'no entry' symbol along with the text

**Error**

**The CUPS server could not be contacted.**
 
And an 'OK' button. Press the OK button and you're dumped back to the desktop. There's no way forward via the GUI and I'm ignorant of any command-line alternatives.

I installed the printer (and got a test page out) using the method you describe on my wife's PC, but I simply don't even get those options on mine...

Graham

---

### Post by amohanty on 2005-12-09
Ok Try to go this URL:

[http://localhost:631](http://localhost:631)

If you cant cupsys is probably not running. Try:

```
/etc/init.d/cupsys restart
```

Screenshot of the URL:
[ATTACH]4371[/ATTACH]

HTH

---

### Post by mangocrazy on 2005-12-10
amohanty,

Many thanks - that's fixed the problem. I couldn't use the http link, but a restart of cupsys did the trick. I did try and configure the printer via the http interface, but found it easier and more successful via the System > Administration > Printing dialog.

Anyway, it's working now and I have a test print to prove it.  :D   Thanks again. 

Graham

---

### Post by mangocrazy on 2005-12-14
Seems like I spoke too soon...

A restart of cupsys makes the CUPS server available for the duration of my login, but when I reboot the system I lose my printing configuration.

How do I make this change permanent? I don't really want to have to restart cupsys every time I boot into Ubuntu...?

Graham

---

### Post by mangocrazy on 2005-12-15
Further to the last post, is there an Ubuntu (or general Linux) equivalent of dear old AUTOEXEC.BAT in DOS; i.e. somewhere you can activate devices and pre-configure stuff that gets read and activated during system startup?

I'm sure I'm being overly simplistic here, but hopefully you catch my drift...

Graham

---

### Post by Weman on 2005-12-18
Hi there I've read your replys, and the tips in them did not help me. I'm new to this forum and did not now how to do. I started a new thread with the topic and then realized I should apply to this thread, so i paste my text here too.
-------------------------------

I cannot access "system/administration/printers" without getting the message "The CUPS server could not be contacted"

I have tried "/etc/init.d/cupsys restart" and get the response:
"* Restarting Common Unix Printing System: cupsd [ ok ]"

I have tried to reinstall all CUPS part I can find in "Synaptic package manager".
I have tried "http://localhost:631" and from there I could send at test page, but it did not fix anything.
Everything worked fine yesterday but now I have no access to printer, what may have happened? Anybody have a clue. I found some guys with similar problem and one of them solved it by restarting CUPS but I have tried that as I mentioned.

// Weman from Sweden

---

### Post by mangocrazy on 2005-12-20
Hi Weman,

After doing a cupsys restart, did you try going back into the System > Administration > Printing dialog? It worked for me (for the duration of the login) after that.

So you were able to access printer one day, and the next day you got the "CUPS server could not be contacted" message? Did you make ANY system changes in between times?

And if anyone knows how to make cupsys start up automatically (i.e. without having to restart it manually every time I login), I'll be very grateful.

Graham

---

### Post by Weman on 2005-12-20
Hi mangocrazy,
Yes after restarting CUPS i tried System > Administration > Printing dialog and still get the message "CUPS server could not be contacted". 

I had a fresh installation saturday with printer both local and in network and I may have done some installation or changes while completing the installation. On sunday the CUPS was not accessable. I've tried reinstalling samba and cups with no luck. The changes I had made in conf-files was restored then so I tried to start from the beginning.

Funny part is that after reading about how to acess [http://localhost:631/](http://localhost:631/) without needing login, I managed to install my local printer there and send at testpage, but still I get the "CUPS server could not be contacted" when trying "System > Administration > Printing dialog", and if I open a text file and try to print ther is no printers.  

Very confusing Ubuntu is new to me and i like it so far, there must be a sollution. Last way out is complete reinstallation of UBUNTU.
I've tried reinstalling samba and cups with no luck. Think I've tried almost everything I have found to read.

// weman

---

### Post by Weman on 2005-12-20
Hi again, have you seen this?

[http://lists.debian.org/debian-printing/2005/09/msg00067.html](http://lists.debian.org/debian-printing/2005/09/msg00067.html)

could be the bug

//weman

---

### Post by mangocrazy on 2005-12-20
Hi,

I've figured out (I think) what my problem was - I think. It's basically a case of a little knowledge is a dangerous thing...

A day or so after I installed Breezy I was nosing around on the forums and came upon this Howto:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

I downloaded "sysv-rc-conf" from Universe repository and started trying various things. It seems I may have inadvertently messed up my cupsys install. I compared the 2 machines we have with breezy and on my wife's (CUPS server working) machine cupsys is on in runlevels 2,3,4,5. On my (no-working) machine it's only on in runlevel 3,4,5.

I ste mine to r/l 2,3,4,5 and restarted - bingo. I can access printing via the System > Administration > Printing route.

I dunno if it will work for you...

But the link you show is interesting. Are you running a mixed IPV4 and IPV6 environment? If so, do you really need IPV6? (I  very much doubt it). If not, then it would seem to be a good idea to disable IPV6 (but don't ask me how...)  

Graham

---

### Post by Weman on 2005-12-21
Hi
I realize that I did'nt think before posting the thing about mixed IPV4 and IPV6. I have not installed anything that I know uses or requires IP6 so that should not be the problem. I downloaded CUPS 1.2 but realized I cannot install it anyway without a C++ compilator, since it was only sorce-code.

This thing about runlevels is interesting though. Linux and Ubuntu is all new to me so I have much to learn. How did you detect the actual runlevels and how did you configure them? I have searced for info about this but did not find any good such.

// weman

---

### Post by mangocrazy on 2005-12-21
Hi,

First of all you need to enable the 'Universe' repository. You do this via the GUI:

Syetem => Administration => Synaptic Package Manager

then

Settings => Repositories

in the Software Preferences window, click Add and in the Edit Repository window check the box by "Community Maintained (Universe)" and click OK. Click 'Yes' to the Repositories Changed window.

Now you should be able to do a search for sysv-rc-conf, mark it for installation and  install it.

Once installed, I suggest you read the instructions VERY carefully in this link

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

and use it to check the runlevel status of cupsys on your system. It's an interesting read in its own right and will teach you a fair bit about what's going on at boot time. Enjoy!

Graham

---

### Post by Weman on 2005-12-23
Hi again, that thing about the runlevels was very intresting, I found out that my CUPS is running at levels 2,3,4,5 so that should not be the problem I guess. I will use the "sysv-rc-conf" later to experiment with the startup.

Right now I will lean back and use pdf-printing to move my printouts to XP via LAN and print them there and hope that future upgrades will solve my problem. In worst case I will try a complete re-installation but that sucks for now.

Thank you so far, maybee someone else with a solution will read our thread.

Merry Christmas and Happy new year with Ubuntu.

// Weman in Sweden

---

### Post by daibak on 2005-12-24
Hi all,

Encountered same problem, same CUPS message "The CUPS server could not be connected."
Intrigued, after initial install of Breezy 5.10 free Install CD when my Samsung ML-1430 laser printer worked fine, I recalled I'd then tinkered with Synaptic Package Manager setting up all the repositories and let Synaptic run for hours doing updates.
So decided to redo my settings for Repositores and run Synaptic updates all over again. Seems I had not added ALL the Repositories properly on first attempt (you have to very carefully add each source with the Add button one at a time, and not just click the OK button). This time a new kernel 2.6.12-10-386 got installed. A reboot was all it took for local ML-1430 printer to work perfectly.
In other words, my initial incorrect Synaptic Repositories set-up settings had mangled CUPS, so blame me not Breezy.

Few days later had another problem trying to print from (Install CD default) Firefox 1.0.7 browser, Firefox wouldn't print. So installed Firefox 1.5 and my online printing problem vanished.

Hope you find my experience useful.

---

### Post by Weman on 2005-12-26
Hi, I finally think I have a  clue about my problem.

I found this writing about CUPS problem when having support for ipv4 AND ipv6.

[http://lists.debian.org/debian-printing/2005/09/msg00067.html](http://lists.debian.org/debian-printing/2005/09/msg00067.html)

I first thought that was the issue but then thought that i had no ipv6 support. Well I looked in "program>systemtools>networktools" and found that I actually have ipv6 support in this machine.

So I have to wait for upgrade of CUPS to 1.2 or thy to disable the ipv6 support. That feels tricky. 

Anyone have a hint how to disable ipv6? Is it possible?

// Weman

---

