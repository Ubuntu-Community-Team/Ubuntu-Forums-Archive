---
title: "Acer Aspire 6930 Headphones not working"
date: 2009-03-04
forum: Hardware
---

### Post by marcwatt@api-partners.com on 2009-03-04
Fairly new to the linux/ubuntu O.S. So far I am in love with it and feel liberated having completely removing vista from my system. One problem. I bought new headphones (yes they work fine), and i plug them in and the sound continues to come through system speakers and not the headphones. I have read many of the threads posted here and none seem to fix the problem, yet they are all marked as solved....please someone help me out.

---

### Post by One Way on 2009-03-04
Hi, I have (among others) he same problem with my headphones in Ubuntu 8.10. I am new to linux and I have just installed the 8.10 two days ago.
How /where from can I install the drivers for this laptop?
Thanks in advance.

PS. I wrote my message here to avoid opening a new topic. Thanks for understanding.

---

### Post by e.deniz on 2009-03-05
I have the same problem, subwoofer is also not working... please anybody help...

---

### Post by executorvs on 2009-03-09
I'm in the same boat.

---

### Post by davidryderuk on 2009-03-10
Hi,

1. Open terminal in Applications>Accessories>Terminal

2. Edit the the file at /etc/modprobe.d/alsa-base in a text editor
```
gksudo gedit /etc/modprobe.d/alsa-base
```

3. Add the following line to the end of the file and save
```
options snd-hda-intel model=auto
```

4. Now try rebooting your machine to see if the headphones work. If this makes the sound any worse, repeat the above steps, this time removing the line you added the first time.

Please note i have not tried this with my own machine but post number #33 in the link below says it should work.

[http://ubuntuforums.org/showthread.php?p=6686537#post6686537](http://ubuntuforums.org/showthread.php?p=6686537#post6686537)

There is also another page in the link shown below about compatability of this laptop with linux that you might want to read.

[http://www.linlap.com/wiki/Acer+Aspire+6930](http://www.linlap.com/wiki/Acer+Aspire+6930)

---

### Post by e.deniz on 2009-03-10
Yeah, it worked, headphones are working very well. Thanks a lot...;)

---

### Post by ydraliskos on 2009-03-14
> **davidryderuk said:**
> Hi,

1. Open terminal in Applications>Accessories>Terminal

2. Edit the the file at /etc/modprobe.d/alsa-base in a text editor
```
gksudo gedit /etc/modprobe.d/alsa-base
```

3. Add the following line to the end of the file and save
```
options snd-hda-intel model=auto
```

4. Now try rebooting your machine to see if the headphones work. If this makes the sound any worse, repeat the above steps, this time removing the line you added the first time.

Please note i have not tried this with my own machine but post number #33 in the link below says it should work.

[http://ubuntuforums.org/showthread.php?p=6686537#post6686537](http://ubuntuforums.org/showthread.php?p=6686537#post6686537)

There is also another page in the link shown below about compatability of this laptop with linux that you might want to read.

[http://www.linlap.com/wiki/Acer+Aspire+6930](http://www.linlap.com/wiki/Acer+Aspire+6930)

thanks :)

---

### Post by ashwindatye on 2009-08-31
without changing any conf files first try this: Go to Volume Control window from your main panel. Then open preferences and add "Surround", "Center" "Front" etc and max out the volume and un-mute it. I got my headphone working this way. Also got my ext mic to work because it was muted by default. Int Mic does not work tho :-(

---

### Post by megamania on 2009-10-29
> **ashwindatye said:**
> without changing any conf files first try this: Go to Volume Control window from your main panel. Then open preferences and add "Surround", "Center" "Front" etc and max out the volume and un-mute it. I got my headphone working this way. Also got my ext mic to work because it was muted by default. Int Mic does not work tho :-(
Any way I can try this in Karmic? The preferences are completely different from Jaunty, and I've found no way to do what you're suggesting.

EDIT: the procedure described in message #5 worked (**thanks!**). I'm just wondering if there's a way to do it from the sound preferences as I used to do with Jaunty,

---

### Post by ashwindatye on 2009-10-31
Hi megamania,
Did you upgeade to Karmic? I have not done so yet. Please let me know the situation with your int mic, headphone etc.
The ONLY real trouble I have wit jaunty is the int mic.
I do want to upgrade to karmic, more for the curiosity around all the hype :-)
But I wont do that till some other user of Acer 6930 tells me that it upgrades fine.
Awaiting reply from you or any other Acer 6930 user.

---

### Post by megamania on 2009-11-01
> **ashwindatye said:**
> Hi megamania,
Did you upgeade to Karmic? 
I got my laptop on july and I installed Karmic Alpha on it, so I never got to try 9.04 on it and can't make comparisons.

Karmic works ok. I had to replace Network Manager with Wicd because wifi didn't work on the alpha/beta versions - maybe it would work now that it has reached the final release.

I didn't get the internal mic to work, but didn't spend too much time on it. The headphones work ok and so does the external mic. Skype works ok, too, in case you're wondering.

After all, I don't see good reasons NOT to upgrade. I'm using the 64-bit version, by the way.

Slightly off-thread - Did you get the fingerprint reader to work? I'd like to try it just for the fun of it, but don't want to go crazy... :-)

EDIT: Just did a quick search and found that apparently the internal mic issue will be fixed with the new alsa drivers (1.0.21). There's a guide to install them here (unfortunately it's in italian): 
[http://forum.ubuntu-it.org/index.php?PHPSESSID=bbd524417e90c1a2da2a3cd0eb42b026&/topic,316183.0.html](http://forum.ubuntu-it.org/index.php?PHPSESSID=bbd524417e90c1a2da2a3cd0eb42b026&/topic,316183.0.html)

---

### Post by ashwindatye on 2009-11-01
Hello Megamania,
Nice to know that they are going to fix the int mic prob in the new alsa release. I will check that link out.
finger print-> my model's got no firgerprint reader.
I will mst probably upgrade soon. Right now i am on tour and dnt want to risk my tons of photos i downloaded from my camera. first a back up t my ext harddrive a home then the upgrade.
Thank you for your comments.
regards,
Ashwin

---

### Post by Dan Again on 2009-11-02
> **davidryderuk said:**
> Hi,

1. Open terminal in Applications>Accessories>Terminal

2. Edit the the file at /etc/modprobe.d/alsa-base in a text editor
```
gksudo gedit /etc/modprobe.d/alsa-base
```

3. Add the following line to the end of the file and save
```
options snd-hda-intel model=auto
```

4. Now try rebooting your machine to see if the headphones work. If this makes the sound any worse, repeat the above steps, this time removing the line you added the first time.

Please note i have not tried this with my own machine but post number #33 in the link below says it should work.

[http://ubuntuforums.org/showthread.php?p=6686537#post6686537](http://ubuntuforums.org/showthread.php?p=6686537#post6686537)

There is also another page in the link shown below about compatability of this laptop with linux that you might want to read.

[http://www.linlap.com/wiki/Acer+Aspire+6930](http://www.linlap.com/wiki/Acer+Aspire+6930)

Worked like a charm for me...thanks!

---

### Post by Canned on 2012-09-04
David, the solution you provided works perfectly! Thank you! :cool:
What does this command really do?

---

