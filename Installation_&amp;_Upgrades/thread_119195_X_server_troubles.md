---
title: "X server troubles"
date: 2006-01-18
forum: Installation &amp; Upgrades
---

### Post by Heretic Monkey on 2006-01-18
Ok, been having some trouble even running the live disc.  I have to use the boot params "live noapic nolapic" to get past some IRQ controller problem.

Then, it runs through a checklist and initiates a bunch of stuff.  I get to a BSOD that reads **"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly"**.  I have a chance to view some in-depth details (nothing really tells me much regarding the X-server.  The next screen says **"The X server is now disabled.  Restart GDM when it is configured correctly."**

What's going on?  Why can't i boot the live disc?  I'm not going to install 5.10 without trying it first.....

If it matters, i have an eMachines 64 3000+ (using the 64-bit 5.10), 1gb Ram, 128 mb Radeon, 150gb HD.

---

### Post by Qrk on 2006-01-19
Just run the command:

sudo dpkg-reconfigure xserver-xorg

Chances are you need to select a different driver (in the second dialog). I would try vga or vesa.

---

### Post by Heretic Monkey on 2006-01-19
i'm guessing i type that in in the boot parameters?  That's pretty much the only console-like thing i have access to between popping the disc in and getting an error.....

After the bsod pops up, i don't have the ability to type anything else in.

I've already tried the vga, and it failed miserably.....

I know you hear this all the time, but i'm a n00b.

---

### Post by Qrk on 2006-01-19
I'll try to explain it a little better.

Just boot the CD like you normally do.

When it gets to where it tries to start X server, wait for it to fail. Once you get your error message you should be given a command prompt. That is where you type in the command. It brings up a utility that can configure X.org with only a little help from you. The second step of that program is to set your driver... which is where the automatic configuration probably failed.

For drivers, I recommend Vesa. If that works, you should be fine. When you install Ubuntu on the harddrive (if you like it), you'll likely have to repeat the same process on your first boot. Once in the graphical environment, people here can help you install the correct drivers from ATI. This should be faster than vesa.

---

### Post by Heretic Monkey on 2006-01-19
[QUOTE=Qrk]I'll try to explain it a little better.

Just boot the CD like you normally do.

When it gets to where it tries to start X server, wait for it to fail. Once you get your error message you should be given a command prompt. 
[/QUOTE]

That's the problem.  After i get the X-server error message, it doesn't give me a prompt.  It goes back to a black screen with the last action as "Checking battery state..."  I don't have the ability to type anymore, and must do a hard reboot to get out of it.

However, i do get a prompt if i do NOT boot with the "live **noapic nolapic**" params.  But this usually freezes after something about an IRQ problem.  It states that the "Controller is probably using the wrong IRQ".  If i do boot with the noapic nolapic, i get the X-server error.

---

### Post by tseliot on 2006-01-19
[QUOTE=Heretic Monkey]That's the problem.  After i get the X-server error message, it doesn't give me a prompt.  It goes back to a black screen with the last action as "Checking battery state..."  I don't have the ability to type anymore, and must do a hard reboot to get out of it.

However, i do get a prompt if i do NOT boot with the "live **noapic nolapic**" params.  But this usually freezes after something about an IRQ problem.  It states that the "Controller is probably using the wrong IRQ".  If i do boot with the noapic nolapic, i get the X-server error.[/QUOTE]
You can try to boot with:
```
live noapic acpi=noirq
```

and if you get the get the X-server error:
press CTRL+ALT+F1
then login (if asked) and then type: 
sudo /etc/init.d/gdm stop  (if you use Ubuntu)
OR
sudo /etc/init.d/kdm stop  (if you use Kubuntu)

then:
sudo nano /etc/X11/xorg.conf

Scroll the file, get to the 'Section "Device" ' and change the driver from whatever it is (nv, ati, etc.) to "vesa"

CTRL+O to save
CTRL+X to exit

Then type:
startx

---

### Post by Heretic Monkey on 2006-01-20
Thanx guys.  With a combination of the commands you suggested, i was able to correctly boot and run the Ubuntu Live cd.

Thanx for the help.

---

