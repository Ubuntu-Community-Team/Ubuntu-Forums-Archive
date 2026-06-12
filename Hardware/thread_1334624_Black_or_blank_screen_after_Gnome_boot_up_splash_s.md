---
title: "Black or blank screen after Gnome boot up splash screen"
date: 2009-11-22
forum: Hardware
---

### Post by kammce on 2009-11-22
[SIZE=2]Previously I have had an issue with my computer not starting up Gnome after the computer finishes booting up. I am left with a black screen, no cursor, and no functionality from my keyboard. I have found that 9.04 boots up my computer so fast that it doesn't have enough time to warm up. Sounds weird but that is what happened.

I figured out how to fix this issue after doing these steps.

step 1) I found that, if I restart my computer, Gnome fires up fine without issue. My only guess was that because of the fact that my computer was still active, it allowed Gnome to start up.

step 2) To get Gnome to work I had to select which kernel to boot from. This made me take time out to select a kernel. Allowing my computer to warm up and run Gnome.

step 3) The next thing I did to check if the second step was true. I went into "Choose Boot Device" mode on my computer (I have a COMPAQ computer so I pressed the "esc" key), waited 10 seconds then told my computer to boot from the master boot drive (my hard drive). This time I did not select a kernel but let GRUB run freely. Then, out of nowhere, Gnome fires up without an issue.

My main guess is that 9.04's boot is so fast that when my **old** computer gets to the point where it has to run Gnome, Gnome stops responding and stalls out. The fix to this is extremely simple:

All you need to do is increase GRUB's timeout time. I changed it from 3 seconds to 6 seconds.
If you are new to linux, grub, or ubuntu then this tutorial will help to fix this issue. The file you are looking for is: "/boot/grub/menu.lst"
[B]
First enter the directory[/B]
```
cd /boot/grub/
```[B]
Create a back up file just in case something happens[/B]
```
cp menu.lst menu.lst.bak
```
**Now use VI, gedit, kate or any other text editor to edit the file menu.lst. I generally use vi.**
```
vi menu.lst
```[B]
locate a line that says :[/B]
timeout        3
**and change 3 to something higher. I chose 6.**

save and exit from the editor you are in and restart your computer.
If this works then good for you!!!!

 If this doesn't work then increase the amount of time that GRUB waits for. 

If this doesn't work also, then you might have another problem. This might be an update issue. I haven't tried this solution but other have. I suggest this as a last resort because you are required to remove a X.org driver. The link to the tutorial is:

[http://blog.dipinkrishna.info/2009/06/blank-screen-after-boot-process-in.html](http://blog.dipinkrishna.info/2009/06/blank-screen-after-boot-process-in.html)

I hope this helps anyone how has the same issue!!![/SIZE]

---

