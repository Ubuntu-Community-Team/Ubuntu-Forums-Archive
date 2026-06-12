---
title: "MP3 Player Not Being Detected"
date: 2009-03-29
forum: Hardware
---

### Post by andyauff on 2009-03-29
Hey everyone. I just recently installed Ubuntu (my first time ever using anything but Windows), and I love it. However, I am having a problem. I plugged my MP3 player (Creative Zen Vision:M 30 GB) into my PC via USB. I know the USB is working because the Zen charges when I plug it in. But the computer doesn't seem to recognize it... in Windows, it would autoplay and I could open the HDD via My Computer to transfer music to it. Ubuntu doesn't seem to recognize the fact that the Zen is plugged in... it doesn't show up in Computer. Any help would be greatly appreciated.

---

### Post by lemuriaX on 2009-03-29
You might try installing gnomad2 - it's in the repos.
I believe it works with most Creative Zen MP3 players.

---

### Post by andyauff on 2009-03-29
> **lemuriaX said:**
> You might try installing gnomad2 - it's in the repos.
I believe it works with most Creative Zen MP3 players.

Thanks for the suggestion... I tried it but it didn't recognize my MP3 player either.

---

### Post by ad_267 on 2009-03-29
This is an MTP device, not a USB storage device so it wont show up in the file browser. 

Does it show up if you open up Rhythmbox (the default music player)? Other media players like Banshee should also recognize it. It should show up then and you can drag and drop music into it. Check you have the MTP plugin enabled in Rhythmbox if it isn't there. Also check that libmtp8 is installed in the Synaptic package manager if you have problems.

I've used an MTP player without any major problems, but just remember that MTP is a closed protocol developed by Microsoft, so you're lucky there's any support at all for these devices.

According to this page, your device should be supported perfectly: [http://libmtp.sourceforge.net/compatibility.php](http://libmtp.sourceforge.net/compatibility.php)

---

### Post by lemuriaX on 2009-03-29
Did you try opening Gnomad2 from the Sound & Video menu or just looking for the player as a USB device? If you type:

```
lsusb
```

in a terminal you can see if it's being recognized.

---

### Post by andyauff on 2009-03-30
Thanks for the info and tips guys. I managed to get gnomad2 to recognize it and it's working. I did have a problem transferring large amounts of music from my MP3 player to my computer (about 4000 songs -.-)... after quite a few of them, the program would close itself. When I had opened up gnomad2 with the terminal, after it closed the terminal would say something about a memory error. I'm not sure why it did that but I'm not really worrying about it. It works for getting music on my Zen now, which is most important. So thanks everyone.

---

