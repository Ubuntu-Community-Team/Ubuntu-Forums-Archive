---
title: "Toshiba Satellite C655 - Lucid 10.04 &quot;WIFI PROBLEMS?&quot;"
date: 2010-08-07
forum: Hardware
---

### Post by itsjoshgrant on 2010-08-07
yesterday i bought a toshiba satellite c655 laptop
i installed ubuntu 10.04 on it and it seems that the wifi card is not compatible(mind you im a noob...it might be)i go to the network manager applet and it says im disconnected 

BUT heres the thing that makes me think maybe its just not the card's compatibility...even when i have a direct line with an ethernet cable it still says its not connected

has these problems happened before?
or do you guys have any advice?

any help would be GREATLY appreciated!
ps:im installed using wubi (if that matters?)

---

### Post by ridge on 2010-08-13
Any resolution to this issue? I too have the satellite c655-s5409 and managed to get 10.04 installed but there's no wired or wireless network connection. The Network Tools and the network icon indicated disconnected -- and I have found no way to change things using these controls. It feels like a driver issue but as I am a new linux/ubuntu user (and as such a total lame *** wrt fixing things in linux)  I would appreciate any information or guidance on how to resolve this. Thanks.

---

### Post by Abyssal187 on 2010-09-02
I'm having the same problem (Both wireless and wired networking are not working) with my Satellite C655. I am also using wubi like the OP.

---

### Post by tallinspanish on 2010-09-19
I also just installed 10.04 on a Toshiba satellite C655, and the wireless started working after I followed some of the directions found here: [http://ubuntuforums.org/showthread.php?t=1554604](http://ubuntuforums.org/showthread.php?t=1554604) . They are reproduced below for convenience:

--------------

when you reboot at the grub menu press 'e' on the first item of the list this will bring you to a bunch of commands.
Move to the line:
> linux /vmlinuz... ro quiet splash
add options to the end of the line; for example:
> linux /vmlinuz... ro quiet splash apci=off

Type <Ctrl>-x <Enter>                                 
this should get you into ubuntu
after you boot in do this:
 
 open your terminal
and type:  
$ cd /etc/default
$ sudo gedit grub

Change the line:
> GRUB_CMDLINE_LINUX=""
to:
> GRUB_CMDLINE_LINUX="acpi=ht"
quotes required.

save as "/etc/default/grub"

Update the GRUB2 bootloader:
$ sudo update-grub                                 
reboot

------------

I am pretty new to Linux myself, but I did this to fix some problems I was having with shutting down and restarting, and after doing this, the wireless started working. Rebooting now works too, although shutting down is still not working perfectly.

---

### Post by itsjoshgrant on 2010-09-19
op here

no longer dual booting decided to go 100% ubuntu 
and still not working :P

---

### Post by cnu1 on 2010-10-10
> **tallinspanish said:**
> I also just installed 10.04 on a Toshiba satellite C655, and the wireless started working after I followed some of the directions found here: [http://ubuntuforums.org/showthread.php?t=1554604](http://ubuntuforums.org/showthread.php?t=1554604) . They are reproduced below for convenience:

--------------

when you reboot at the grub menu press 'e' on the first item of the list this will bring you to a bunch of commands.
Move to the line:
> linux /vmlinuz... ro quiet splash
add options to the end of the line; for example:
> linux /vmlinuz... ro quiet splash apci=off

Type <Ctrl>-x <Enter>                                 
this should get you into ubuntu
after you boot in do this:
 
 open your terminal
and type:  
$ cd /etc/default
$ sudo gedit grub

Change the line:
> GRUB_CMDLINE_LINUX=""
to:
> GRUB_CMDLINE_LINUX="acpi=ht"
quotes required.

save as "/etc/default/grub"

Update the GRUB2 bootloader:
$ sudo update-grub                                 
reboot

------------

I am pretty new to Linux myself, but I did this to fix some problems I was having with shutting down and restarting, and after doing this, the wireless started working. Rebooting now works too, although shutting down is still not working perfectly.



Thank you.  This just worked like a charm for me, I appreciate your post and will look forward for more from you.  Good work and thanks once again!

---

