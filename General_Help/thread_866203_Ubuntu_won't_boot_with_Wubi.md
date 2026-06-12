---
title: "Ubuntu won't boot with Wubi"
date: 2008-07-21
forum: General Help
---

### Post by Diablo2king on 2008-07-21
I installed Ubuntu with Wubi and when I try to boot it come to some command thing where you put commands in. I'm kind of a noob to linux so I don't know what I should do.

---

### Post by ago on 2008-07-21
See first [http://ubuntuforums.org/showthread.php?t=396526](http://ubuntuforums.org/showthread.php?t=396526)
If you have still problems boot in verbose mode and post here the errors

---

### Post by JasonSilver on 2010-06-30
Why do synaptic updates sometimes break Wubi?

After an Ubuntu update today, I'm told there's no wubildr. :(

---

### Post by catsails on 2010-06-30
I am having this same issue today. I was in ubuntu earlier this afternoon. When I tried to shutdown, ubuntu would only return to the login screen and not actually shut down, so I had to force it to shut down manually. When I rebooted, selecting Ubuntu at the boot screen resulted in:
1) messages telling me it could not find wubildr
2) it loaded a command line prompt (GRUB?)

It could be an update thing, as I have it set to update automatically. 

For the record, I've already tried chkdsk in vista and rebooted, with no success.

---

### Post by wilee-nilee on 2010-06-30
First both of you need to start your own threads and post the bootscript in my signature in code tags as described.:p

---

### Post by JasonSilver on 2010-07-01
I've been waiting all afternoon for a reply to my post on a new thread, and hardly anyone looks at it, nevermind answering it. :-/

So, I'll see if I can figure out what your bootscript thing is.

Thanks!
Jason

---

### Post by Alex Ber on 2010-07-01
You should check [http://www.uluga.ubuntuforums.org/showthread.php?p=9533407](http://www.uluga.ubuntuforums.org/showthread.php?p=9533407)

---

### Post by JasonSilver on 2010-07-01
FASCINATING! 
I booted into Windows last night, tried the chkdsk, but it would only work on reboot.

While I was in there, I thought- hey let's make Ubuntu the default OS on boot.

Then I left to go hear a great funk band play in the city.

When I checked the computer this morning, I was booted into Ubuntu. 

GO FIGURE!

---

### Post by JasonSilver on 2010-07-02
Ubuntu required a restart this morning, and again have the same problem-- 

Try (hd0,0) NTFS5: no wubilder
Try (hd0,1) NTFS5:

Then it says

Unknown command 'load font', 
File not found.

Anyone able to help me at all?

Jason

---

