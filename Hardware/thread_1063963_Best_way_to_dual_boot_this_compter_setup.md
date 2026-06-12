---
title: "Best way to dual boot this compter setup?"
date: 2009-02-08
forum: Hardware
---

### Post by GARoss on 2009-02-08
Is there a best way to dual boot when Ubuntu 8.10-64bit is on new HD (up & working) & XP Home (32bit) is on another HD, old c: - currently unplugged?

Would it simplify things if Ubuntu was installed on same HD? I did it this way because I was afraid of loosing XP.

All suggestions are appreciated.
George

---

### Post by lha on 2009-02-08
Add the following lines to the very end of /boot/grub/menu.lst:
```

title		Windows
root		(hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

Plug in your hd with Windows and set bios to boot from Ubuntu drive.

---

### Post by GARoss on 2009-02-08
Sorry, deleted
See below

---

### Post by GARoss on 2009-02-08
OK. I'm in the /boot/grub/menu.lst menu & made the changes you suggested. I have not turned the computer yet to try. Before I save & plug in the old c: with XP I have one more question:
My MB has 4 HD connectors. (hd0) was where the old c: was. I unpluged this & plugged it into the new HD where Ubuntu is now. I think XP needs to be (hd0) so do I plug (hd0) back into XP, then (hd1) into Ubuntu? Does it matter in your script?

[I]title		Windows
root		(hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1[/I]

If there's a 3rd HD that doesn't boot, does it matter how this is written?
Thanks
George

---

### Post by lha on 2009-02-08
Ubuntu drive should be (hd0). Otherwise, Grub won't be started, but Windows. So you can just plug the drive with XP to a free connector and restart. You will see either Grub or Windows. If you see Windows, you'll have to switch the places of your drives (or alter boot settings).

If you have a third drive, and your menu.lst entry for Windows doesn't work, change all occurences of 'hd1' to 'hd2'. (Also hd1,0 to hd2,0.)

---

### Post by GARoss on 2009-02-08
> **lha said:**
> Ubuntu drive should be (hd0). Otherwise, Grub won't be started, but Windows. So you can just plug the drive with XP to a free connector and restart. You will see either Grub or Windows. If you see Windows, you'll have to switch the places of your drives (or alter boot settings).

If you have a third drive, and your menu.lst entry for Windows doesn't work, change all occurences of 'hd1' to 'hd2'. (Also hd1,0 to hd2,0.)

Thanks,
I'll give it a go!
George

---

### Post by GARoss on 2009-02-08
Ok. It booted to Ubuntu & I do see the c: identified as *74.3 GB Media*.
Do I need to run a terminal to setup dual boot or should it have done so now?
George

---

### Post by lha on 2009-02-08
You are (or at least should be) able to dual boot now. It is possible that Grub menu is not shown when you boot. You can remove the '#' sign from line '#hiddenmenu' in menu.lst to make Grub always show the option to boot Windows. You might also want to change the number after 'timeout' to choose how long Grub will wait before starting Ubuntu.

---

### Post by GARoss on 2009-02-08
New problem. The terminal says Permission Denied. It doesn't prompt for password.
How to correct that?
George

---

### Post by lha on 2009-02-08
Write 'sudo ' in front of the command you are trying to run. For example, 'sudo nano /boot/grub/menu.lst'.

---

### Post by GARoss on 2009-02-08
Password working now.
It never got to the boot/grub menu text. Everything was in the terminal &
I made the changes but don't see how to save form the terminal.
I'll see if I can get the original to open.

---

### Post by GARoss on 2009-02-08
We have dual boot working! :D Thank you for your patience, lha! 
This is very new to me & believe it or not; it's getting a little easier.
Here's were a newbe gets confused; all the terminal lingo.
*sudo nano /boot/grub/menu.lst* does get me into the menu, but, in the terminal window. I didn't know how to save from there. Still don't.
Earlier today, when you said open,* /boot/grub/menu.lst* I got errors in the terminal. I did a search how to navigate in the terminal in the Ubuntu help & found this; 
[I]cd /boot/grub
sudo cp menu.lst menu_backup.lst
sudo gedit menu.lst[/I]

What it opened was the actual /boot/grub menu that I could edit & save.
Later when the dual boot didn't work & you said add sudo nano to */boot/grub/menu.lst*. The terminal opened & I didn't know how to save.
When I remembered how I got to the other list earlier, I was able to make & save the changes.
The trials & tribulations of a newbe!
Thanks again
George

---

### Post by lha on 2009-02-08
> **GARoss said:**
> We have dual boot working! :D Thank you for your patience, lha!

You're welcome. I'm glad to hear you got it working.

---

### Post by GARoss on 2009-02-09
And, one final note. 
Now when I boot XP, Windows asks to investigate (j:) or hit Esc or Enter to Skip. (j:) is the drive I partitioned for 50% Ubuntu & 50% NTFC for XP. Not a big deal but interesting how intutive OS can be!
Thanks again,
George

---

