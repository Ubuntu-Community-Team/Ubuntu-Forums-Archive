---
title: "&quot;Coukld not start the X server&quot; on boot."
date: 2008-08-15
forum: General Help
---

### Post by ShakeyJake on 2008-08-15
Co I just installed Ubuntu on another machine I have at home.

Its been fine for a few days but now after the ubuntu loading menu (the orange bar that moves from left to right) I get a blue background with a grey box that reads.

"Could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog dialog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected.

<OK>

I can press enter then I move to the CLI which is behind this box and I log in with no GUI.

So, any ideas? Where is this syslog dialog and how can I use that to diagnose the problem?

Thanks in advance guys,
Jack.

---

### Post by overdrank on 2008-08-15
> **ShakeyJake said:**
> Co I just installed Ubuntu on another machine I have at home.

Its been fine for a few days but now after the ubuntu loading menu (the orange bar that moves from left to right) I get a blue background with a grey box that reads.

"Could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog dialog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected.

<OK>

I can press enter then I move to the CLI which is behind this box and I log in with no GUI.

So, any ideas? Where is this syslog dialog and how can I use that to diagnose the problem?

Thanks in advance guys,
Jack.

Hi and could you give us some system specs like graphics, memory and Version of Ubuntu? Have you tried to reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` the sudo reboot and hopefully this will get you back to the desktop

---

### Post by BarryMaccaukner on 2008-08-15
On that error there where it says check syslog, it also gives you a path. You can use the cd command and navigate to the path , then use nano or pico to read the log. It will usually tell you where the error is . When you read the log it will say something like "couldn't read line 43 of xorg.conf" so you then navigate to the xorg.conf file and again use nano,pico,vi, vim or whatever non-graphical text editor you have. In the options you can choose to show line numbers. When you go look at line 43 you most likely will see the problem. It is usually something like a comment that isn't commented with an octothorp (#) or a line that starts with a comma. However I understand that it seems really daunting to fix. It isn't usually though. If you just follow the instructions and look at the log file, it will amaze you how much you can understand and fix on your own. It's actually my favorite thing about linux. Good luck

---

### Post by ShakeyJake on 2008-08-17
Overdrank, your reconfiguring and rebooting worked a charm, thanks mate.

For the record, this is an Eee 900 with Ubuntu Hardy.

---

### Post by ShakeyJake on 2008-08-20
Ok, since this first happened it has happened twice more. 

I know I can fix it, but I'd prefer it to just not break in the first place. Any ideas what's causing it? I tried navigating to syslog but there isnt a path specified and I dont know my way round the cli well enough to find it tbh.

As far as isues go, this isnt the biggest, but it is a little annoying. Any help much appreciated guys.

Jack.

---

### Post by overdrank on 2008-08-20
> **ShakeyJake said:**
> Ok, since this first happened it has happened twice more. 

I know I can fix it, but I'd prefer it to just not break in the first place. Any ideas what's causing it? I tried navigating to syslog but there isnt a path specified and I dont know my way round the cli well enough to find it tbh.

As far as isues go, this isnt the biggest, but it is a little annoying. Any help much appreciated guys.

Jack.

Ok what is the model of the graphics card? You can use the ```
lspci
``` command in the terminal. Look for VGA. I believe it is the intel graphics and they are usually pretty stable. How much memory on the system and how much shared with the intel graphics? You may look in bios to adjust that amount shared.

---

### Post by quicksiedo on 2008-10-12
"bump!"

Hi, I've had ubuntu eee installed on my eee pc 901 for about a day and now I've got the same problem. Unfortunately I'm new to all this and don't have the slightest clue as to what all this means... Is there a simple fix to this for an absolute (absolute) beginner, or will it be easier for me to format and reinstall?

Matt :(

---

### Post by ringmaster on 2008-10-28
The same problem here, too. Eee PC too, with Ubuntu Intrepid; on my other computer with the same config I don't have problems.

I am using JFS file system, and I can't fix it 'cause the system is in read-only mode. It is the second time that it happens for me in the last week, having to reinstall. I think that it happens when I switch off the computer the hard way (with the power button pressed for 5 seconds), but I don't know for sure.

I will try to figure out what happened and copy the logs. Could be the SSD system?...

---

### Post by ShakeyJake on 2008-12-05
Well, this has just happened to me AGAIN, this time with Ubuntu-eee.

I only moved to this distro because I was having so many problems with eeebuntu doing this. I too have a JFS filesytem and I cant fix it either cos the system in read-only mode.

Anyone able to help please? 
TIA,
Jack

---

### Post by ringmaster on 2008-12-06
ShakeyJake, it looks like there are problems with JFS in Ubuntu, not only on the eee PC. On my Ubuntu 8.04 home PC every time that the computer is switched off the bad way, a secondary hard disk (with JFS) has to be fixed manually.
I would use XFS or Reiserfs if I were you, now I am using reiserfs on all my partitions without problems for almost 3 months with Intrepid.

I hope this is fixed sometime... or use Mandriva 2009, it supports eee PC completely out of the box and has better boot time.

---

### Post by ShakeyJake on 2008-12-07
Really? I cant find anything on the net about JFS being anything less than perfect. It's good reviews were the reason I chose it. My desktop has been JFS since Feisty.

---

### Post by piheuvel on 2008-12-21
I too have this problem with the read-only file system. Therefore Overdrank's solution for fixing the problem with the X server doesn't work, as ringmaster and ShakeyJake describe.

Can I fix this problem with the read-only file system? All devices are mounted rw.

Gr. Pim

---

### Post by piheuvel on 2008-12-21
OK folks, I found the solution elsewhere. I did an fsck -a and all seems well now!

---

