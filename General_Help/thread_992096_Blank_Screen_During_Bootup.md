---
title: "Blank Screen During Bootup"
date: 2008-11-24
forum: General Help
---

### Post by iheartubuntu on 2008-11-24
One of my computers does not show the Ubuntu boot up screen becuase of my monitor. Is there any way to change the boot resolution so I can see it booting up? Every so often when it runs the diagnostic, my wife thinks the computer died becuase of Ubuntu :) She now knows to press ESC to bypass the check, but Id rather see the bootup process. Thanks for any help on this! Ive been looking all around and cant seem to find the answer I need.

---

### Post by marshall.robert on 2008-11-24
One of my families computers is also affected by this. The monitor just sits there and says "Out Of Range". its a 1280x1024x75.

---

### Post by jerrykenny on 2008-11-24
Its best to just remove the splash facility, try this

sudo gedit /boot/grub/menu.lst

find the entry which pertains to your current kernel, and delete the word "splash" from the end of the command.

I really find the splashscreen most irritating anyway, and it hides the otherwise usefull info which should be scrolling down your screen . . 

I cant actually read that fast . . . but it does help to know if theres been an error message during boot

---

### Post by jerrykenny on 2008-11-24
And forgive me if i'm suggesting a kludge or being patronising ! lol i see now that you're both veterans,  soz:)

---

### Post by iheartubuntu on 2008-11-24
> **marshall.robert said:**
> One of my families computers is also affected by this. The monitor just sits there and says "Out Of Range". its a 1280x1024x75.

Yah, thats exactly what I get too.

---

### Post by iheartubuntu on 2008-11-24
> **jerrykenny said:**
> Its best to just remove the splash facility, try this

sudo gedit /boot/grub/menu.lst

find the entry which pertains to your current kernel, and delete the word "splash" from the end of the command.

I really find the splashscreen most irritating anyway, and it hides the otherwise usefull info which should be scrolling down your screen . . 

I cant actually read that fast . . . but it does help to know if theres been an error message during boot

OK, that worked, thanks. It is nice to have the splash though. Maybe if I change my VGA # to something else it will come in at the right resolution?

I also notice that if you have a newer LCD monitor with digital HDMI plug and a video card that has HDMI input, the problem gets solved. Maybe becuase the monitor adjusts to the resolution automatically? With an analog cable you dont get that.

---

