---
title: "Installing side by side with windows xp - dual boot"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by alon2 on 2009-09-08
Hi,
I'm trying to install kubutnu 9.04 side by side with windows xp.
I downloaded the image and burned it to a CD.
when I boot the CD every thing works great and I get to the menu - when trying to install or just try with out install - I get to the screen where I have the progress bar(under the kubuntu logo) - after the progress bar reaches the end the screen goes black.
for a couple of minutes it seems that the CD drive and the computer are working, but after that the screen stays black and nothing happens. I tried waiting some thing like 10 minutes but nothing is changing. this happens in both install and try without install.
I tried the disk on another computer and it worked fine. I also used the check defects on the main menu - it worked and no defects were found.
I used to have ubuntu 9.04 on that PC , but than I inserted a windows xp cd and boot from it and that destroyed the dual booting, so I just formatted the ubuntu partition and merged it with the windows one(my guess is that this is the reason why I can't install it again - maybe there are "left overs" from the last installation).
I have a Pentium 4 3GHZ processor on an Intel mother board   , with 3GB memory , and nvidia graphic card.
Any help will be highly appreciated.
Thanks
Alon.

---

### Post by Partyboi2 on 2009-09-08
Try installing in safe graphics mode, F4 at the main menu of the live cd. 
If that does not work, then you could try installing using the alternate cd.

---

### Post by alon2 on 2009-09-08
thanks for your answer but I have 3 questions:
1)if I'll install in the safe graphics mode - would the installation be the same?
2)how do I install using the alternate CD?
3)why do you think this is happening?any way to check it?

---

### Post by Partyboi2 on 2009-09-08
>  1)if I'll install in the safe graphics mode - would the installation be the same? Yes it would be the same.
>  2)how do I install using the alternate CD? The alternate cd is a text base installer but is pretty simple to follow. You can download the alternate cd via torrent from [[COLOR=Blue]here[/COLOR]]("http://www.kubuntu.org/getkubuntu/download"). Then burn the iso to disk and boot it then follow the steps through.
>  3)why do you think this is happening?any way to check it? 	
When you get to the Main menu of the live cd press F6 and remove the word splash from the line then press enter. Hopefully this might yield some further infomation.

---

### Post by alon2 on 2009-09-08
Again thanks for the reply

> **Partyboi2 said:**
> 
When you get to the Main menu of the live cd press F6 and remove the word splash from the line then press enter. Hopefully this might yield some further information.

what does F6 does? what should I get?
P.S sorry for noob questions...

---

### Post by Partyboi2 on 2009-09-08
F6 allows you to add or take away boot parameters, by removing splash from it, means you will boot without a splash screen (progress bar)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by alon2 on 2009-09-08
OK I will give both options a try...

Do you think my problem has anything to do with what I said in my original question(about already having ubuntu 9.04 installed in the past)?

---

### Post by Partyboi2 on 2009-09-08
> **alon2 said:**
> OK I will give both options a try...

Do you think my problem has anything to do with what I said in my original question(about already having ubuntu 9.04 installed in the past)?I don't think so.

---

### Post by alon2 on 2009-09-08
very weird...
b.t.w I also tried to boot with the ubuntu 9/04 disk(that I know is working cause I used it to install the ubuntu 9/04 in the past) and it gives the same result... meaning some thing is screwed with my pc rather than the CD

---

### Post by alon2 on 2009-09-09
I tried (with out install) the safe graphic mode and it worked.
The question is: if I now install it - will I need to enter using the safe mode all the time?

Again thanks for your help

---

### Post by Bartender on 2009-09-09
In my limited experience, no.  Safe Mode during install just gets you past the roadblock so that Ubuntu can install all the video drivers that are stashed on the install disc.

Once you've got it installed, go to System>Administration and open the Hardware Drivers utility.  Ubuntu *should* recognize your card and suggest hardware drivers.  In your case these will be nVidia proprietary drivers.  Not the best solution in the world.  It would be better if nVidia made their drivers open-source.  But it's working pretty good for most users.

This doesn't always work!  I have an ASUS card running nVidia 8400GS chipset.  In Intrepid, Ubuntu recognized the necessary drivers.  I just updated the PC to Jaunty yesterday, and Jaunty says no drivers are needed.  I might downgrade back to Intrepid.

---

