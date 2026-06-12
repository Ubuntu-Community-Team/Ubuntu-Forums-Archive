---
title: "[Solved] Toshiba Satellite L30-11D Gutsy No Sound &amp; Slow Boot Issues"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by Frankie6502 on 2008-02-24
I am the owner of a Toshiba Satellite L30-11D who recently installed Gust, after which I had a couple of problems.

[LIST=1]
[*]**Very slow boot with no output or text**
[*]**No sound what so ever**
[/LIST] 

After many hours of trying to fix these problems I finally cracked it (with the help of the Ubuntu forums). 

To save others time and effort I have detailed the solution as follows: -

**1) Fix the slow boot & output issue**

Type the following in the terminal:

```
sudo gedit /boot/grub/menu.lst
```

Go right to the bottom after the line "## ## End Default Options ##" you should see the following line or very similar: 

> kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5339ddcc-77f6-4786-b9ee-f2322219432e ro quiet splash

now add " vga=791" to the end so you get this: 

> kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5339ddcc-77f6-4786-b9ee-f2322219432e ro quiet splash vga=791

Save and exit.

Now run these two lines:

```
sudo gedit /etc/usplash.conf
sudo update-initramfs -u -k `uname -r`
```

Then reboot and that should be it fixed.
Credit for this fix go's to [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen")


**2) Fix the no sound problem**

This was a real pain to find the solution for this problem that works for the L30-11D model, anyway here we go.

```
sudo gedit /etc/modprobe.d/alsa-base
```

Then add this line to the very end of the file:

> options snd-hda-intel model=lenovo

I had to try quite a few options posted on the forums before I found this one to work, thanks has got to go to all those who have posted fixes for other laptops.

I hope this post is of use to someone. :)

---

### Post by bertbiker on 2008-03-23
Thanks Frankie! 
You helped me fix the sound problem I encountered after installing ubuntu. Your solution also works  for the toshiba satellite L30-10T.
Cheers.

---

### Post by bertbiker on 2008-03-24
I discovered that adding "model=lenovo" at the end of the file did solve the problem with the laptop speakers but that headphones did not work properly. Adding "model=toshiba" instead works for the headphones but now the laptop speakers are muted...

---

