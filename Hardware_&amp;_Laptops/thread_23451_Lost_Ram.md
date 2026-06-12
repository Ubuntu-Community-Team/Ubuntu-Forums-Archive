---
title: "Lost Ram??"
date: 2005-04-02
forum: Hardware &amp; Laptops
---

### Post by kfc on 2005-04-02
hi,
I've just installed ubuntu a few days ago.
Starting to love it.
but 1 thing i've notice missing is the amount of user ram in my system. My machine has got 512x3 ram. it should have display about 1.5 gig of ram in the system monitor. but now it only has 885.4 MB of ram.
Where is the rest of the ram go?
is it related to the amount of swap disk (1.6 gig)?

I hope i can have an answer before i try someway to resize the swap disk.
Thanks.

MemTotal:       906660 kB
MemFree:        167232 kB
Buffers:        200296 kB
Cached:         360708 kB
SwapCached:       2792 kB
Active:         308112 kB
Inactive:       370304 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       906660 kB
LowFree:        167232 kB
SwapTotal:     1630524 kB
SwapFree:      1627732 kB
Dirty:             256 kB
Writeback:           0 kB
Mapped:         172884 kB
Slab:            46336 kB
CommitLimit:   2083852 kB
Committed_AS:   297212 kB
PageTables:       1632 kB
VmallocTotal:   122800 kB
VmallocUsed:     25608 kB
VmallocChunk:    96172 kB

---

### Post by bored2k on 2005-04-02
Linux kernel 386 supports a maximum of 900MB of ram. Install linux-686 and use that .

---

### Post by kfc on 2005-04-02
thank.
is there a way that i can upgrade the kernal instead of installing the whole machine?

---

### Post by bored2k on 2005-04-02
[QUOTE=kfc]thank.
is there a way that i can upgrade the kernal instead of installing the whole machine?[/QUOTE]
 sudo apt-get install linux-686 .

[http://www.ubuntuguide.org/temp/#extrarepositories](http://www.ubuntuguide.org/temp/#extrarepositories)

Did I say Welcome to the forums? if not, welcome.

---

### Post by kfc on 2005-04-02
Oh!
u've made my day man!
:D

thanks for the help.
i thought i was going to reinstall the whole os.
just about to ask why can't i find i686 iso.... but thanks for the great support!

---

### Post by bored2k on 2005-04-02
Make sure you read the guides :
[http://ubuntuguide.org/](http://ubuntuguide.org/) [old - dont use tis repositories, but its useful] and [http://www.ubuntuguide.org/temp/](http://www.ubuntuguide.org/temp/) [in development].

Also do [http://ubuntuforums.org/showthread.php?t=22646&highlight=script](http://ubuntuforums.org/showthread.php?t=22646&highlight=script) on your system for some quick setup easy for newcomers and loved by everyone else.

BTW, once you install 686, your grub boot loader will  look all ugly, install grubconf, then from a terminal run sudo grubconf and modify it ;) .

---

### Post by paul cooke on 2005-04-02
don't bother resizing the swap disk... with that amount of RAM,  you should never get anywhere near filling what you've already set... I have 1/2 gig RAM and 1/2 Gig swap and I've only got 9 Meg of swap occupied... and some 200 Meg free RAM (I've got azureus running with a couple of isos being seeded, azureus eats ram for breakfast...)

---

### Post by mirland on 2005-04-05
I have the same problem with a lot of ram not being recognized. BUT what are the risks of updating to 686 ? My laptop is a Centrino-based Travelmate. 

And what does it mean that the Grub will look "all ugly" ? Will it not work or are we talking aesthetics here ? :) 

Please enlighten me !

/Mirland

---

### Post by HiddenWolf on 2005-04-05
[QUOTE=mirland]I have the same problem with a lot of ram not being recognized. BUT what are the risks of updating to 686 ? My laptop is a Centrino-based Travelmate. 

And what does it mean that the Grub will look "all ugly" ? Will it not work or are we talking aesthetics here ? :) 

Please enlighten me !

/Mirland[/QUOTE]

Shouldn't be any problem, centrino should support 686 fully.
Even if you installed a totally incompatible kernel, the old one will still be there to boot from, it just wouldn't be the default anymore.
You could just log in using the old kernel, and remove the new to get back to the old situation.

---

### Post by mirland on 2005-04-06
Thank you for the answer !

It all sounds very tempting but as mentioned before: What would be the problem with Grub? Will it not work or ?

Please bear with all my questions. I'm very new to this linux thing having used windoz for years...

/Mirland

---

### Post by kfc on 2005-04-06
[QUOTE=mirland]Thank you for the answer !

It all sounds very tempting but as mentioned before: What would be the problem with Grub? Will it not work or ?

Please bear with all my questions. I'm very new to this linux thing having used windoz for years...

/Mirland[/QUOTE]
 I've got it fixxed.
works like a charm. it has fully detected all of my rams in the system.
btw, i've no problem for grub. it just added 686 selection other than 386.

---

### Post by mirland on 2005-04-07
Works like a charm is the exact phrase. It all worked out perfectly. 

/Mirland

---

