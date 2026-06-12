---
title: "boot resolution"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by Bigmack on 2007-01-05
Hello all ! I've sucessfully installed kubuntu edgy6.10 on my dell inspiron laptop dual booting xp.
What a sweet OS!!! The only problem I have is immediately after grub and before the kubuntu log in screen, my display is filled with large vertical bars flashing randomly somewhat arranged in columbs. I assume it is something to do with the resolution. This was not happening with dapper. I am still a noob, so please be gentle:???: :confused:

---

### Post by meng on 2007-01-05
I wonder if this would work:
choose to Edit the default option (it's a one-off change, but you can make it permanent later if it works) and add to the end of the booting kernel line (after quiet splash) this:
vga=791
See how it goes.

---

### Post by Bigmack on 2007-01-05
I've tried that with several different selections and an error message pops up "you have passed an undefined mode number Press <return> to see vidio modes available........"

---

### Post by meng on 2007-01-05
Oh, what options does it give you? BTW
[http://www.damnsmalllinux.org/wiki/index.php/Vga%3Dxxx](http://www.damnsmalllinux.org/wiki/index.php/Vga%3Dxxx)

---

### Post by Bigmack on 2007-01-05
Vidio adapter : VESA VGA
Mode:       COLSxROWS:
0 0F00      80x25
1 0F01      80x50
2 0F02      80x43
3 0F03      80x28
4 0F05      80x30
5 0F06      80x34
6 0F07      80x60

Enter mode number or 'scan':

---

### Post by meng on 2007-01-05
Sorry, I'm not sure what to make of that!

---

### Post by Bigmack on 2007-01-05
The screen dose the same thing when kubuntu shuts down as well. Kubuntu looks and runs great, Bios screen works, I can read the entire grub menu with no problem. It just goes crazy between grub and the login screen.:confused: ](*,)

---

### Post by Bigmack on 2007-01-05
Thanks for your help meng,,,,my brain hurts now,,,,,must sleep,,,,,,,,,,I shall return tomorrow,,,,,,#-o

---

### Post by Buck2348 on 2007-01-05
Try vga=771 or 769.  Below is the table for the vga code.  The Edgy usplash doesn't like resolutions greater than 800x600.  That's what is working for me.  You should also check /etc/usplash.conf and make sure the resolution there is the same you're using in menu.lst.  You might want to try installing sum (startup manager) (you might have to enable all the repositories in System > Software Sources > Ubuntu 6.10 tab)--to install open System > Synaptic Package Manager and search on sum.  You can open sum with System > Startup Manager.  In sum if you make any changes to the Display Resolution or Depth, check your menu.lst to see that it didn't garble the Kernel line for the kernel to which you boot (same line with the vga setting in it.)  If none of this works you might have to start searching the Forums for usplash problems.  I just finished that process.  Once you get this fixed you should see a usplash screen with a progress bar and (if you remove the word "quiet" from the "quiet splash" in menu.lst) scrolling text telling what the system is doing, which you also should have seen when booting up the live CD.
 ```
                     640x480  800x600 1024x768 1280x1024 1600x1200
-----------------+---+--------+----------+-----*----+----------+---------
256 (8 bit)       |   769        771        773          775          796
32,768 (15 bit) |  784        787        790          793          797
65,536 (16 bit) |  785        788        791          794          798
16.8M (24 bit)  |  786        789        792          795          799
```

Buck

---

### Post by Jimmy_r on 2007-01-06
Just a minor correction, sum can be found from the link in my signature.

---

### Post by Bigmack on 2007-01-06
Jimmy_r You Rock!!!!!:mrgreen: :mrgreen: :mrgreen:  Many thanks to all that responded!!!!:D  I now have the splash screen and text and,,,,,,Still have a display mode error but I'll get that sorted out too!! Thanks again all!!

---

