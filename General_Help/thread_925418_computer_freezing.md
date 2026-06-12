---
title: "computer freezing"
date: 2008-09-20
forum: General Help
---

### Post by mosty friedman on 2008-09-20
hey everyone,
i got this problem sometimes that ubuntu completely freezes and i cant do anything, i cant even run the terminal or open a window or anything..the mouse cursor can move and all but i cant click on anything...this just happened to me before i post this thread, it was working great and all but i tried to play a song and it froze then i had to turn off the laptop by holding down the power button....anyone here got any idea what may be causing this problem and also when the OS freezes, is there anything i can do ??..thank you all for your time

---

### Post by tCarls on 2008-09-24
If it's not completely frozen (the mouse still moves) you can try killing the gui with ctrl-alt-backspace, or try going to a non-X terminal with ctrl-alt-F1.

If you're able to get to a terminal (using the above) the first thing you should do is run "dmesg" to see any errors. Otherwise, look in /var/log/messages. There should be something in there that points to the problem.

---

### Post by luckis on 2008-09-24
Even though linux has one of the most sophisticated filesystems rebooting this way is not suggested, i would suggest reading about "R E I S U B" (**R**aising **E**lephants **I**s **S**o **U**tterly **B**oring).
This is a key combination that goes like this :
Hold down the Alt and SysRq (Print Screen) keys. 2. While holding those down, type the following in order. Nothing will appear to happen until the last letter is pressed: REISUB 3. Watch your computer reboot magically and safely! :D
(****Attention!*** You HAVE to be root to enable/disable!! Become root using "sudo su" and don't forget to exit!*)
You can enable this feature with this:
echo 1 > /proc/sys/kernel/sysrq
You cab disable it with this :
echo 0 > /proc/sys/kernel/sysrq

---

### Post by mosty friedman on 2008-09-25
never heard of either methods lol, well anyway thanks i appreciate the help..will try both ways

---

### Post by mkham on 2008-09-25
Wonderful. I'm getting the same thing- progressive to total mouse lockup and the HD buzzing like mad till I do hard power down (which FU things, i know). There is some flaw in new Firefox 3 update that is supposed to cause something like this- read latest release notes.
MH

---

### Post by lanr01 on 2008-09-25
> **mkham said:**
> Wonderful. I'm getting the same thing- progressive to total mouse lockup and the HD buzzing like mad till I do hard power down (which FU things, i know). There is some flaw in new Firefox 3 update that is supposed to cause something like this- read latest release notes.
MH


 I have been getting this off and on today and yesterday... I have had to power down hard a few times now. I don't like doing that.. I will try some of tricks mentioned earlier in this thread..

 Is this something that is buggy with Ubuntu 8.04??

Thanks,

---

### Post by Camilia on 2008-09-28
If you're able to get to a terminal (using the above) the first thing you should do is run "dmesg" to see any errors. Otherwise, look in /var/log/messages. There should be something in there that points to the problem.

run dmesg, where, how?   look in /var/log/messages  where, how? 


Hold down the Alt and SysRq (Print Screen) keys. 2. While holding those down, type the following in order.
This is now possible for me to do. For alt key on the left and prt screen on the right. I would have to type with my tongue to do this.

---

### Post by tCarls on 2008-09-29
> run dmesg, where, how? look in /var/log/messages where, how? 

Just open a terminal (Applications menu -> Accessories -> Terminal), type "dmesg" and press enter.

If you're unable to get to a terminal before rebooting then open a terminal after rebooting, and type "sudo cat /var/log/messages" or "sudo less /var/log/messages" or maybe "sudo gedit /var/log/messages". Good luck.

---

### Post by Camilia on 2008-09-29
What are these commands  suppose to do? 
 sudo cat /var/log/messages" or "sudo less /var/log/messages" or maybe "sudo gedit /var/log/messages". 

I just turn the computer off from the tower and reboot it.   With my computer it sometimes happens when I add a program via synaptic for a short while.

---

### Post by tCarls on 2008-09-29
Oh, sorry. I didn't realize you weren't the one that started the thread.

I'm not sure what problem you're having (it might be worth starting a new thread so things don't get too confusing.)

So originally I started out explaining what to do if things lock up. You can try to force a logout by pressing ctrl-alt-backspace. If things are completely locked up you can use that REISUB trick to turn it off safely.

Secondly, I listed a couple ways to try to diagnose the problem so it doesn't happen again. There is a file called /var/log/messages. Whenever something bad or out of the ordinary happens there will usually be an entry in that log file. Those commands let you view the file. Apparently, the easiest way to view it is to just go to System Menu -> Administration -> System Log. If something bad happens and you don't know why it's usually helpful to look in that log.

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

---

### Post by Camilia on 2008-09-29
I have the exact problem as the originator  at times thus I don't understand the confusion or why I need to post another thread.

Did System Menu -> Administration -> System Log-> /var/log/messages.  What seen I don't understand.  Is there anything specific I should be looking for?

---

### Post by tCarls on 2008-09-29
Sorry, the confusion was all on my end. No need to post another thread.

---

### Post by Crafty Kisses on 2008-09-29
It could be a resource issue, post the results of this command:
```
top
```

---

### Post by Camilia on 2008-09-29
Unable to copy the info.  Had to put in flicker.
[IMG]http://farm4.static.flickr.com/3140/2900735634_17466dc7b8.jpg[/IMG]

Excuse the thumbs down icon. I didn't put it there.

---

### Post by mosty friedman on 2008-10-03
ok so basically if there's an X or a GUI freeze the ALT + CTRL + BackSpace should do the trick but if its a complete kernel freeze then the REISUB trick should come in handy

---

### Post by mosty friedman on 2008-10-03
thanks for all the info people...btw how can i learn more about the terminal commands and bash scripting? so when i face a problem i can sorta figure it out..

---

