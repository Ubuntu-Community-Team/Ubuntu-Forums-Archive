---
title: "Can't run live CD"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by docmanny on 2005-06-28
I want to try ubuntu on my desktop but I keep getting a OUT OF SYNC error when the X-server starts. I'm running a Intel 865G chipset motherboard with built in video and a Samsung SyncMaster 170MP monitor. It looks like its trying a refresh rate of 100K????

Do I have to type something different at the boot prompt before ubuntu loads?

---

### Post by GTvulse on 2005-06-28
Boot into single user mode a.k.a recovery mode (you'll be root so watch out those little fingers :-). 

Edit your xorg.conf file:

```

-# cd /etc/X11

-# nano -w xorg.conf

```

Scroll down the file listing till you find the Monitor section. Grab the manual of you monitor and find the Horizontal Sychronization range (in KiloHertz) and the Vertical Refresh rate range (in Hertz). Now create the proper entries in the Monitor section, save the file and type exit at the prompt. The system should continue booting and bring up X windows.

As an example (and I meant it, this is only an example!), here are the entries in my /etc/X11/xorg.conf file:

```

Section "Monitor"
        Identifier      "Generic Monitor"
        VendorName      "Samsung"
        ModelName      "SM750s"
        Option          "DPMS"
        DisplaySize     303 228
        HorizSync       30-70
        VertRefresh     50-160
        #Gamma          1.15
EndSection


```

If you don't have a Samsung 750s(M)t CRT monitor, **don't** use the example above as settings for your monitor! You can fry the DDC and leave the monitor as dead as a doorstep. You can learn the meaning of each entry by typing "man xorg.conf" in a terminal emulator.

Hmm.. Now that I read again... You are using a live cd! I'm afraid you are out of luck because you can't modify the settings... But the advice above works if and when you decide to install Ubuntu (or another Unix or Linux distro) directly in your desktop.

---

