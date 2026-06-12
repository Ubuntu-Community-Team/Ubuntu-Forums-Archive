---
title: "Blank Screen after installing ubuntu."
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by `Spencer on 2009-01-07
Well, I just installed Ubuntu on my girlfriends laptop. I go through the installation and it goes normally, no errors, no nothing. I take the disc I used to install out (original Ubuntu disks not copies) run the computer and it loads the grub menu ( where it counts down from 3 to let you hit the esc button to get to some options) then makes an attempt to load and i get 2 lines of messages, (error message has a bunch of zeros and a 5 (both lines i believe) the messages flash really quickly. 

I tried re-installing it to no avail.

Thanks for the help if anyone can.

`Spencer

---

### Post by Zeroberry on 2009-01-07
I don't know exactly what happened to you but you could do some simple troubleshooting. Load the install cd and check for faults in it. If there are, just burn a new one. You could also try burning the alternate install.

If you want to know exactly what's wrong just be patient and a linux master should come along ;)

---

### Post by Therion on 2009-01-07
What version of Ubuntu did you install on this notebook?

Could you rattle off the basic hardware specs the notebook in question?

You might try using F6 from the splash-screen and edit out the "quiet" & "splash" bits from the kernel line so you can get an idea what's happening when the boot process goes awry.  Do you know how to do that?

You could also try booting up using the Safe Graphics option.

---

### Post by `Spencer on 2009-01-07
using version 7.10

Im very new to linux at all so if you want to walk me though this thatwould be nice. i am on my desktop right now so i can follow you;re directions while still reading this.

`Spencer

---

### Post by `Spencer on 2009-01-07
any help?

---

### Post by Therion on 2009-01-07
> **`Spencer said:**
> using version 7.10
Any particular reason you want or need to use version 7.10?  It's an older release.  I'd suggest trying 8.04 or 8.10 instead.  That alone could solve your problem.

Also, some basic specs on the computer you're trying to install on would be good.

---

### Post by `Spencer on 2009-01-07
its a compaq laptop.  i dont know any specs on it off hand and i dont know how to check them when i cant load the OS.

I was using that version because its the CD's i was given. just downloaded the ISO of the newest version and tried installing it and it freezes when i select install or even load with the CD.

---

### Post by `Spencer on 2009-01-10
when i start ubuntu. the computer loads. it starts to boot the grub menu.

Stage 1.5. boots that then goes to startup. I then get these 2 lines.

>  8.463178 PCI Cannot allocate rescources region 7 0000:00:5.0 
8.463178 PCI Cannot allocate rescources region 8 0000:00:5.0

I tried downloading the most recent version of Ubuntu from the website and making and ISO disc. I did it and it gets to the menu when you have to install it or start. and any option i click on it doesnt load. it just freezes at that menu and stays.

`Spencer

---

### Post by `Spencer on 2009-01-10
anyone have any ideas?

---

### Post by chex_m8 on 2009-01-10
One issue you may have is not enough RAM. Linux live cds run completely in RAM so you need to have the minimum amount 256MB. Live CD freezing during boot is a common symptom.

---

### Post by chex_m8 on 2009-01-10
After you click the option to run the live cd or install does the screen go blank or does it just freeze right there and you can still see the options.
you might try hitting F4 boot to safe mode.

---

