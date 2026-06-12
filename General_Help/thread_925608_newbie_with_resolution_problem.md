---
title: "newbie with resolution problem"
date: 2008-09-20
forum: General Help
---

### Post by tar54805 on 2008-09-20
Hi all,

I'm new to ubuntu and have installed the latest version on an older computer.  I was playing with the different screen resolutions and accidently accepted a small res that will not let me display the entire resolution window.  I am unable to switch back to a usable res. because I can't scroll down to the buttons to make the change.  I have only pulled out about 25% of my hair trying:)

thanks, steve

---

### Post by gregconquest on 2008-09-20
I *think* you are going to have to edit your xorg.conf file. Look at this thread for more info:

[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973")

Maybe someone else will have a more direct answer here for you.

Good luck.
Greg

---

### Post by fooman on 2008-09-20
reboot the computer and at the grub menu, choose recovery mode.

once there,  choose the xfix option and see if that works.

---

### Post by tar54805 on 2008-09-20
Thanks Greg, I will give it a try.

steve

---

### Post by treehouse on 2008-09-20
I'm pretty sure there's a terminal command you can enter to change resolution, but I don't know it. Here's the sequence of keyboard commands you should be able to push in order to change resolution after opening the screen resolution dialog (they should work even if you can't see it)

1. open screen resolution dialog
2. press 'Tab' once
3. press 'space' once
4. press the up arrow a few times to scroll to a higher resolution (however many times you think it'll take to make it useable again, or just mash it to get the highest in the list)
5. Press 'Tab' four times
6. Press 'Space'
7. Resolution should change and you should get the 'do you want to keep?' dialog, spacebar will cancel, right arrow, then spacebar will keep.
8. You should be changed to where you can navigate on your own.

---

### Post by tar54805 on 2008-09-20
Hi all,

For anyone who might end up on this thread with the same problem, I tried the xfix and that wasn't the trick, then did the tab and space bar and got back on track.  Thank you treehouse.  

cheers, steve

---

