---
title: "No DMA, no DVD?"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by Sp@z on 2005-12-12
Hi all, Just got the dvd player to work through ubuntu 5.10. My specs are listed in my siggy. The movies are VERY choppy and not at all a joy to watch. I know I need to enable DMA to get this to stop, but my dvd rom does not support DMA. IT plays perfectly when I boot into Win98SE, I have tried to force DMA on, but it just doesn't work. ANy other suggestions to this matter? The only reason I am still running win98SE on this laptop is because it will play DVDs flawlessly, but slowly I am starting to prefer linux and after I get all the lil kinks worked out hope to delete Win98SE :)

Thanx.

---

### Post by earobinson on 2005-12-12
[https://wiki.ubuntu.com/DMA?highlight=%28dma%29](https://wiki.ubuntu.com/DMA?highlight=%28dma%29)

---

### Post by Sp@z on 2005-12-12
Thank you for the quick reply, however this is what happens when I run those commands. 

root@Ubuntu:/home/bill # sudo hdparm /dev/hdc
/dev/hdc: No such file or directory
\root@Ubuntu:/home/bill # sudo hdparm -d1 /dev/hdc
/dev/hdc: No such file or directory
root@Ubuntu:/home/bill #


I think to maunally setup by adding the lines is definatly an option I want to try, but phsyically taking my case apart is out of the question. :(

Can you help me through this part first then we go from there?

THanx

---

### Post by earobinson on 2005-12-12
can you post your fstab?

```
cat /etc/fstab
```

---

### Post by Sp@z on 2005-12-12
hehe he he Now you got me! LOL I was like Fstab? HUH LMAO then I read the rest..here it is and thank you in advance.............

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext2    defaults,errors=remount-ro 0       1
/dev/hde        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
root@Ubuntu:/home/bill #

---

### Post by tokyovigilante on 2005-12-19
You need to change all /dev/hdc references to dev/hde in the above commands, since this is where your DVD drive is mounted. (it's like typing C: instead of E: if that helps) :)

---

### Post by Sp@z on 2005-12-19
wow thanx for the input Tokyo. This has made video playback SMOOTH. (in mplayer)However I get an error message "Too many packets in video buffer" I am sure this is my hardware though. Before the message comes up the sound is there but it is not in synch with the video, then the message comes up and the sound quits.

---

### Post by tokyovigilante on 2005-12-20
Glad that worked. Hmm, it should be as good as in Windows though, I note your signature and system config, I don't have a lot of experience with PC card IDE and Linux, but google it up, you may need to install specific drivers for your card to enable faster transfer, as I would suspect this is where the bottleneck is.

---

### Post by Angry penguin on 2006-02-28
I am having the same problem with "too many video packets in the buffer" does anyone know how to fix this? The video and audio is fine until the buffer overflows, then the sound dies, this usually takes about 10 seconds of dvd playback.:cry:

---

### Post by rohan! on 2006-03-02
same problem with the buffer overload in mplayer. ... other players are now working like beasts though so i ain't too fussed by it. xine has become my fave.

i had the same problems with dma, only managed to sort out last night ... i hate it when you find a thread that would have been really helpful 24hours ago!! lol

---

