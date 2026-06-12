---
title: "External Hard Drive not recognized"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by chadridesabike on 2007-04-28
I recently installed feisty fawn on my dell inspiron 9400.  Works great, so does beryl.  When i first installed it, ubuntu recognized my external hard drive.  It is a free agent (seagate) 250gb.  Any ideas why it would no longer recognize it?

other problems:
I have not yet found a solution to change my resolution to 1440x900.  I have read many forums and all 5 ive tried havent worked.  Ive had to reload ubuntu each time and start over.

I havent found a good forum post on how to set up my msn email account using either evolution mail or thunder bird.

Any help on these topics would be greatly appreciated.  Thank you in advance.

---

### Post by dfreer on 2007-04-28
msn (hotmail) email account = can't use evolution or thunderbird, because it is only accessable from http. that's the way I saw it anyways, maybe someone else has figured out a workaround.

---

### Post by chadridesabike on 2007-04-28
ok, so i thought i figured out how to fix the resolution from another forum, but when i log in, i see the mouse and a cream colored background, nothing else to click on.  So now i am back on my xp home to type this, ill have to start over again tomorrow.

---

### Post by SteveHoffmanUK on 2007-04-28
See my nearby post about my USB external hdd. It comes, it goes. At first it wasn't there, now it is, but I only upgraded to Feisty yesterday, so it's too early to detect any pattern.. Is yours now consistently not recognised? How many boots have occurred since it disappeared?

ON EDIT: My results seem to be completely random: 50 per cent of starts, the disk is there, 50 per cent it's not. Same for Feisty restarts.

---

### Post by Martin on 2007-04-28
The easiest way to fix your blank or 'cream' screen is to run the command "sudo dpkg-reconfigure -phigh xserver-xorg" from within a terminal. This will create a new xorg.conf file with the generic settings which should get rid of the cream background and get yourwindow manager working properly again.
While its always good to have a crack at things - installing something like Cairo from source for the sake of a blinged up dock is not for the faint-hearted. Spend a couple of hours/days/weeks getting familiar with basic commands and directory locations before embarking on something that is actually quite difficult. There's plenty of bling you can install before you need to get Cairo running. Good luck. 
As far as the usb drive thing - I've got the same problem and I've only had it since I did a clean Feisty install. My external drives worked fine under Edgy and all subsequent Feisty herds and the beta.

---

### Post by dentaku65 on 2007-04-28
> **Martin said:**
> ...
As far as the usb drive thing - I've got the same problem and I've only had it since I did a clean Feisty install. My external drives worked fine under Edgy and all subsequent Feisty herds and the beta.

Hmm, I' getting mad about it; since edgy till the beta version was working perfectly, now my external USB disk and CD/DVD USB drive do not automount/mount anymore (I have to unplug/plug them after every boot)... but also I noted a very weak USB performance in general, for example in my case a trouble in random (quite frequent) disconnections of my wintv usb card, loosing the buffer from the port to stay connected (or at list I think)...

---

### Post by Martin on 2007-04-28
There are a couple of things that seem to have been unfixed in the final release. Suspend and hibernate on my laptop is now no longer trouble free, I now have intermittant network waking up issues and sometimes the mouse doesn't come back - but the touchpad does. I've got the USB HDD problem and the googlearth glib problem has not been fixed. On the othe hand netowrking with my windows systems works now works flawlessly. So on the whole apart from having to re-remember the mount command and options I guess I'm about even with the latest version. Looking forward to the fixes though.

---

