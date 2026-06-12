---
title: "Display problem and OS boot problem"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by Kirium on 2006-10-20
Hi folks... I've run into a big problem with my Toshiba Satellite laptop that was running 6.06.

It started after the laptop hung while browsing this forum using firefox. The only thing that was responding was the mouse. I could not restart or anything so I was forced to cut the power to the laptop. When it restarted, it came back with distortion and vertical lines all down the display. It got to the Dapper login screen (still covered in lines) and I could log in, but it hung straight after entering the password. Only a horizontal splash graphic with Ubuntu on it shows and it refuses to go any further. I've left it overnight thinking it might just really be slow, but it would go no further. I restarted and ran memtest, and this is what the display looks like

[IMG]http://i58.photobucket.com/albums/g248/Kirium/21102006004.jpg[/IMG]

I left memtest going overnight and 10hours later it still hadn't finished. Not sure if that's normal or not.

I loaded the Toshiba recovery discs (with XP) and the graphical problem remained during the time the recovery discs were loading. Once it told me to reboot (the part where it restarts and re-installs windows) it refused to get past the initial XP screen. It would not go any further and actually install XP at all... 

So my final attempt at getting the laptop working was to install Windows Vista RC, which actually installed, much to my amazement. And this is now what the display looks like

[IMG]http://i58.photobucket.com/albums/g248/Kirium/20102006003.jpg[/IMG]

The vertical lines change all the time, and as you can see, the mouse has "cleaned" them up, but once you change windows or anything, they return. These lines are present at the Ubuntu login screen also, but I just snapped the pic while it had Vista going because it shows it much better...

I'm really stumped at what has gone so wrong with the laptop. I'm posting here because it happened while it had ubuntu installed, so I'm hoping there's something in Ubuntu that can fix it. Using recovery mode I can get to the command line, but it just won't boot into Ubuntu any more...

I don't think it's a driver issue or anything software related like that, because the toshiba recovery discs would have restored any settings that were causing it. Could it be BIOS or firmware related? Or has hardware somewhere become corrupted?

Can anyone help me out a bit here??

Cheers.

---

### Post by Kirium on 2006-10-21
Can anyone at all shed any light on what may have gone wrong with my 6.06 laptop???  :(

---

### Post by Kirium on 2006-10-23
Anyone got any idea at all??? :(

---

### Post by Kirium on 2006-10-28
Bueller??

---

### Post by Unicast on 2006-10-28
I'm surprised no-one's replied as they're normally quite a helpful bunch on here.

It's hard to say what the problem might be. Although I've had display problems on my Dell Latitude D400 (Intel 855GM shared graphics) when I bought another 512mb stick of memory. Turned out that the memory was faulty - replaced the memory, problem gone.

Worth having a look at maybe. I know that dodgy memory can cause xp to hang during re-installation.

---

### Post by Kirium on 2006-11-12
Thanks for the reply Unicast.

I did pull both sticks of RAM out and tried them in the opposite slot and tried  each by itself.. Didn't seem to change anything.. I might try and track down some cheap RAM and try it out..

I haven't touched the laptop in a few weeks now.. Just frustrates me that Ubuntu wasn't even on there for 24hrs before it (perhaps critically) damaged my laptop. Anything software I don't care about, there was nothing on it.. But hardware and repairs aren't free...

Anyone else got any idea what's causing this issue???

---

### Post by haxality on 2006-12-08
Ubuntu is not at fault for whatever is going on with your laptop. You are experiencing a hardware problem, and the Ubuntu installer only modifies files on your hard drive. (Software)

---

