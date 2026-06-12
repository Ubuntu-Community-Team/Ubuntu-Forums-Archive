---
title: "Laptop Power Management"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by popkid on 2006-06-05
I have a Dell Inspiron 7500 (PIII, 700Mhz)

Neither Suspend or Hibernate works for me in Dapper, both send the laptop to 'sleep' but neither resumes properly (about 50% of the time I don't get working X back, the other 50% of the time wireless doesn't work on resume, graphics card 3D acceleration doesn't work on resume, with hibernate I come back to the gdm login rather than the session, hibernate doesn't work at all from the gdm, giving a message about an incorrect command)

I could live without these, but I have a problem where if I leave the machine running for a couple of hours to the point where the screen has shutdown it won't wake back up again, the lights on my pcmcia wireless are out and the machine doesn't respond to clicks or key presses, I can't get to a text login and the only option is to power off, this forces an fsck at bootup next time round and it finds errors on the root filesystem due to not being umounted cleanly.

Obviously this is not a happy state of affairs that I need to sort out.

Ideally I would like to have the machine suspend itself after 30 mins or so of inactivity (and be able to resume it with no loss of wireless or other modules), if I could get the fn-suspend key working that would be a bonus....

I am confused by the numerous acpi options available, i.e. setting suspend/hibernate options, I have heard about suspend2 being a good option? But also read somewhere that is not supported by default in the dapper release (requires self built kernel? I wouldn't feel confident to tackle this, I'm a relative newb...)

I  apologise if the answer to my problem is already out there on the forums, I have searched and found lots of references to similar problems but the solutions often seem to be very machine specific

Any help or guidance on what to try would be much appreciated,

pK

---

### Post by arthur on 2006-06-05
Same here! :( 
My Pavilion ZT3000 hibernated (suspension was not available) perfectly with 5.10. Now, suspension is available under 6.06, but nothing can bring it back to life. 
And what is even funnier: hibernation has become power down now! 
Only solution: power button.
Anybody else?

---

### Post by citronelu on 2006-06-05
My laptop is an Acer Aspire 1362WLMi (Nvidia FX Go 5200) and I had the same problem as Arthur (no resume). I found this page - [http://en.opensuse.org/NVidia_Suspend_HOWTO](http://en.opensuse.org/NVidia_Suspend_HOWTO) - and it worked. Now I have a different problem - the sound stops working after resume.

---

### Post by popkid on 2006-06-05
I've managed to fix my suspend issue....

Apparently acpi is disabled in the 2.6.15 kernel if the BIOS on your machine is older than 2000, (mine is!)

I have overriden this by adding the option acpi=force to the end of the kernel line in /boot/grub/menu.lst

Now my machine suspends in about 3 seconds and wakes again in about 15, and my wirleless and mach64 are working... cool.

Hope this helps someone else out there...

pK

---

### Post by arthur on 2006-06-08
Thanks a lot, Citronelu. I am not lucky, though, my card is from ATI :(

---

