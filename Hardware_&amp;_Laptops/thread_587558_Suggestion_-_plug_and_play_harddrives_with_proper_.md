---
title: "Suggestion - plug and play harddrives with proper permissions - heres my problem"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by Squish on 2007-10-22
I have not really found a precise answer for my problems, and I do restrain from posting new threads.So sit back and enjoi!
  
Well I just bought a new hitachi deckstar HD (750gb, sata2, 32mb cache), popped her into a new nexstar 3 HDD enclosure, and connected it to my computer. There was no default Filesystem on the drive, so it was all unallocated. I couldn't find the Harddrive on my desktop though... 

[B]Suggestion:1:
When an unallocated Harddrive mounts, display an option automatically to whether the user would like to partition the drive for external use. This I am sure would help allot of people who dont know anything about partitioning. It certainly would have brightened my experience. Also, I had no idea it had mounted, and I figured  that because it wasn't on the desktop, I could just turn it off (which can be bad for the drive). So also displaying the unallocated drive on the desktop would be very helpful.
[/B]
Well because I know a bit better, I downloaded gparted, and then went forth to research what type of filesystem I should use.
ext4 sounds nice, but its unavailable. This means Reiserfs is my choice of drive.
I partition it, and that goes fine.
[B]
Suggestion 2:
Offer a bit more help dialogue when it comes to setting the disklabel. I have no idea what it is, and even after wikipedia-ing it, I still couldnt find out. The fact that MSDOS was the default, was disconcerning, because for all I know, this means I cant use it on my computer because I use linux. My logic is that because I am running linux, I should use a linux disklabel.[/B]

So after partitioning it, it comes forth to the desktop, and all is fine. I open it up, and I try opening up a folder already in it called Lost+Found, and it says I dont have proper permissions to open it.
Arg:confused:. No problem, I will just rightclick to its properties, and change the permissions

[B]Suggestion 3:
Me and my friend agree that this is one of the biggest annoyances behind permissions in gnome. That is, for when it comes to changing permissions of folders owned by root, you cant do it through properties, or through a GUIin general. When you go to the permisssions dialogue, it just shows that unclickable grey text.. Even when I chmod it, its still wont comply. Thus this suggestion is for reg users to be able to change permissions of a root owned folder, with a simple password request, and of course a warning message. I hate the fact that even after diving into command line, I still am clueless to howto change the permission, much less make it permanent. Perhaps an external harddrive utility manager would be a good idea. But honestly, this is so incredibally frustrating, moreso because ubuntu does not let me log in as root. (unless I wanna rescue in command line of course). Can anyone relate to this?[/B]

So in the end, I have a external harddrive thats top of the line, but I cant write to it, to backup my computer, so I can do a fresh install of ubuntu.

so anyways...
How do I change the permissions? I did the chmod 777, but that didnt do nothing. yarg.

BTW, what do you think of my suggestions Ubuntu Community? I figure there must be a layer of ignorance on my part, that I have overlooked or something like that. I think that this would make new users experience allot less stressful, because I can recall about a dozen times to which I wish I could have just changed permissions easily like that.

:guitar:Cool!

---

### Post by frafu on 2007-10-23
Hello, 

As the Accessibility forum is normally intended to discuss software related to disabilities, I will move this thread to the Hardware & Laptops forum, where it is more appropriate. 

By the way, suggestions for improvements are usually filed as RFE (request for enhancement) bugs against the appropriate package on launchpad.net .

Have a nice day. 

Francesco

---

