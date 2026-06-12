---
title: "HOW-TO: Possible fix of battery drain on 11.04"
date: 2011-06-28
forum: Hardware
---

### Post by Lolpanda on 2011-06-28
I'm just passing along knowledge to make sure that this issue gets the press it deserves. 

**_Background:_** Alright, as anyone who reads Phoronix, or Tomshardware knows. Ubuntu 11.04 was on a massive power-binge, sometimes cutting battery life by up to 50%. 

[http://www.tomshardware.com/reviews/ubuntu-11.04-natty-narwhal,2943-13.html](http://www.tomshardware.com/reviews/ubuntu-11.04-natty-narwhal,2943-13.html) 

This issue has been known for some time, but no one knew what the cause was or how to fix it. Thanks to our friends over at Phoronix; both issues have been addressed. The issue was a patch submitted during the 2.6.38 kernel window, that attempted to "Fix" or atleast deal with, bugs in poorly written BIOS in terms of Power Management. The patch did exactly what it was designed to do, but the, hidden, net effect was that Linux wasn't utilizing the power management that some hardware did support, all because BIOS said that it didn't. Beforehand, the Linux Kernel would atleast try to enable said power management, but this caused problems for some users. The patch basically made the kernel say "If it says it doesn't, don't bother even trying." 

([http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1)  Phoronix article with a much more in depth analysis. My summary was dumbed down for convience of readers)

**_[SIZE="3"]WARNING: YOU MAY BE IN THE SEGMENT OF USERS WHO'S BIOS' WILL CAUSE LINUX TO HANG WITH THIS FIX ENABLED. DO NOT TRY UNLESS YOU KNOW HOW TO REPAIR YOUR SYSTEM FROM A LIVECD[/SIZE]_**

**_The Fix:_** This fix will work on any linux distro utilizing grub2, a similar fix will also work on grub-legacy. 

1) Load up terminal from your menu.
2) ```
cd /etc/default/
```
3)
     GNOME USERS:  ```
gksu gedit grub
```
     KDE USERS: ```
kdesudo kate grub
```
     ALL OTHERS: ```
sudo nano grub
```
4) Find the line that says "GRUB_CMDLINE_LINUX_DEFAULT=" Most users will have 'quiet splash' following that. 

5) Immediately after 'quiet splash' add the words "pcie_aspm=force" without quotes

6) Save the file and exit the text editor you used, for nano users that would be ctrl-x, y to save the following. For VI/VIM/Emacs, you're on your own as I don't use them.

7) run the command ```
sudo update-grub
```

8 ) wait for grub to finish updating, reboot. and enjoy a longer battery life! 

I was personally able to get an extra 50 minutes of battery life from that one simple fix. 

Michael at Phoronix has said that he is looking into 2 MORE power-usage regressions, one of which lies within the kernel's scheduler, so there's another one that will effect everyone (unless you're using a custom kernel)


**_TO REVERT:_**  This is assuming you're system didn't start hanging when you rebooted, and you just want to revert it for testing purposes. Follow steps 1 - 5, but instead of adding "pcie_aspm=force", remove it. Save. Exit. And re-run sudo update-grub and reboot. 

To restate, if you don't know how to fix your system from a liveCD, don't use this fix! This fix also won't do anything for you if you have a CORRECTLY coded BIOS, as Linux would've activated Power Management correctly, this is only for poorly written BIOS'. This isn't limited to laptops, anyone wanting to tone down their power usage (servers for example) can use this fix.

---

### Post by dtach on 2011-06-30
Hi, I think that my laptop (hp dv4 117nr) may be one of the laptops affected by this "bug" i guess you could call it. I want to try this fix, and am somewhat confident in my ability to fix this if it makes the boot hang, but I'm not positive so am very skeptical about doing it. My main concern is that I wouldn't be able to write over the files necessary because of lack of root access. Is there anyway that you can post a short post on how exactly someone might go about fixing this if they DO get a hang on bootup?

---

### Post by Lolpanda on 2011-06-30
@dtach

That guide above was to make the change "permanent" to only give it a try for, what I believe only lasts a single boot.


1) Boot up your machine
2) When you get the grub menu during the boot process, hit one of the arrow keys to stop the timer.
3) Look at the bottom of your screen to double check what key to hit to edit the menu, mine was 'e' but that MAY be different for you. No matter what though, it'll say like 'press (key) to edit, press (key) for command line.' You want to edit.

4) In my menu, the line you're looking for was the second to last line but yours could be different. You're looking for a line that says 

```
root UUID: (bunch of numbers/letters) ro quiet splash
```

jump on over to just after quiet splash and immediately following that add "pcie_aspm=force" (without quotes), add a space after "force' if there isnt one already there. And I believe it's F10 to boot with the changed options. (will say at the bottom of the screen)

Unless the functionality changed in Grub 1.99, that will add pcie_aspm=force ONLY for that single boot up. If it doesn't work (your system hangs) you can reboot and it shouldn't enable pcie_aspm anymore. You can double check by going in and pressing the edit key again to make sure pcie_aspm isn't listed. If it is, just delete pcie_aspm=force and boot hit F10 again and you should be good to go.


Sorry if the reply was a little confusing, I just woke up at the time of this posting haha

---

### Post by Mars73 on 2011-07-01
This would be awesome.
For this very reason I went back to Lucid because I hated working with my notebook which was constantly blowing the fans.
I'll download the latest iso and check if it works.
Why this is not a sticky on top of the page and in bold is beyond me, again I can't imagine someone working with Natty and not going crazy about the powerhungry kernel.

---

### Post by dtach on 2011-07-01
I will by trying your guide asap, and I will post my results!

---

### Post by dtach on 2011-07-03
Okay so I tried the temporary version first, just to make sure that I would be able to boot up. Luckily, I booted up just fine, so I actually modded my grub file. I've been running ubuntu like this for about 12 hours total, and not only has my battery life improved, but the overheating issues that I've ALWAYS had with my laptop, even when i was running windows, have almost completely vanished. My computer is running quieter, smoother, and overall its battery seems to last a bit longer too. This is really great and im glad i took the leap to try this thing out.

---

### Post by Mars73 on 2011-07-03
Same here!!!
Whereas before, I used 11.04 the minute it came out and turned back to 10.04 as soon as possible because of the heat. The fan was constantly blowing, even when it was just out of hibernate. It is now quiet!
Sure, when watching some movies or other intensive work it goes on, but when idle the fan goes back to quiet again.
I've not used it that much this weekend but it's a totally different experience then when 11.04 just came out.
Thanks, and this should be sticky in bold on top of this page.
(for the record, I use a HP ProBook 4710s, with Ubuntu 11.04 64bit)

---

### Post by Lolpanda on 2011-07-05
Glad to see that everything worked for you both. 

A little extra info on why heat issues were fixed by this fix. Active State Power Management (ASPM) controls anything plugged into the PCIE slots on your computer (everything for a laptop, graphics/network card for desktops.) It can tell the hardware to jump between full power, idle (powersave) or totally off at will. If ASPM is turned off (like it is by default without this fix for most people) all hardware is set to full power no matter what. Which can cause significant heat issues, leading to overheating, or just your fans Being turned on 24/7 to compensate. 

What would be interesting to try for anyone who's willing. Revert back to 10.10 or 10.04 and try this same fix, see if you can get an even longer battery out of those than you do natty just for the heck of it. It may be that ASPM wasn't turned on for all your devices (some but not all, cuz the all or nothing fix came with natty's kernel) and so you could get even better battery off those. Again, just a quick experiment to try. It may not even work, but it popped in my head cuz you two mentioned 10.10/10.04.

Also, admins. Icanhassticky?

-Lolpanda-

---

### Post by subehsharma on 2011-07-19
hello,

when i tried the "permanent solution" i.e. editing the grub menu and pressed f10, i got this message on the next screen:

Booting a command list
ALloc magic is broken at 0x7dc55210.
Aborted. Press any key to exit.

Any ideas?

-------------------
Problem solved!
-------------------

---

### Post by hawthornso23 on 2011-07-19
This made a huge difference to my Dell Latitude E6510. Not only is battery life extended hugely, but the laptop is now running a lot cooler. Very highly recommended.

---

### Post by subehsharma on 2011-07-20
> **Lolpanda said:**
> Glad to see that everything worked for you both. 

A little extra info on why heat issues were fixed by this fix. Active State Power Management (ASPM) controls anything plugged into the PCIE slots on your computer (everything for a laptop, graphics/network card for desktops.) It can tell the hardware to jump between full power, idle (powersave) or totally off at will. If ASPM is turned off (like it is by default without this fix for most people) all hardware is set to full power no matter what. Which can cause significant heat issues, leading to overheating, or just your fans Being turned on 24/7 to compensate. 

What would be interesting to try for anyone who's willing. Revert back to 10.10 or 10.04 and try this same fix, see if you can get an even longer battery out of those than you do natty just for the heck of it. It may be that ASPM wasn't turned on for all your devices (some but not all, cuz the all or nothing fix came with natty's kernel) and so you could get even better battery off those. Again, just a quick experiment to try. It may not even work, but it popped in my head cuz you two mentioned 10.10/10.04.

Also, admins. Icanhassticky?

-Lolpanda-

I have to add the statement "pcie_aspm=force", everytime i bootup my laptop, in the grub list. Is this normal?

---

### Post by hawthornso23 on 2011-07-31
> **subehsharma said:**
> I have to add the statement "pcie_aspm=force", everytime i bootup my laptop, in the grub list. Is this normal?

Are you sure you followed the instructions in the first post completely. That is edit  /etc/default/grub  and then run 

```
sudo update-grub

```to implement the change permanently. If you forget to do the last step ...

Also these instructions are for GRUB2. If you are still running GRUB you have to edit  menu.lst

---

### Post by fyfe54 on 2011-08-23
Just updated grub.  All ok.

Apparently, my battery now has 3.75 hours left a from full charge when it used to be a little over 2 hours.

Dell Inspiron 1545, Ubuntu 11.04, 4Gb, Pentium dual core 2.3GHz, Linux 3.1.0-0301rc2-generic


More Info:  Seems to be working - I can feel my left leg getting cooler.

---

### Post by tastefuldeath on 2011-09-24
Wow. Before fix, my netbook batt life runs at 3-4 hours. After, it's up to 5-6 hours. Not only that, the part where I rest my palm while typing, it's usually hot but now it's noticeably cooler. Thanks!

---

### Post by rossmurray on 2011-11-13
I just wanted to thank for this thread. I had an issue with my Samsung NC10 netbook flashing through low and high brightness after a few minutes of starting up. Made it impossible to orient around the screen or even select apps.. well except with a lot of patience. 

I was guided here by the user 'tastefuldeath' and using your method it fixed the issue immediately. Great job folks!! :guitar:

---

### Post by MoreOrLess on 2011-11-13
This should be automatically fixed in kernel 3.2: [http://www.phoronix.com/scan.php?page=news_item&px=MTAxNDM](http://www.phoronix.com/scan.php?page=news_item&px=MTAxNDM)

---

### Post by Bbeto on 2012-01-22
Ok, just one question:
You guys think this could work in 10.04?

Thanks for the answer.

---

