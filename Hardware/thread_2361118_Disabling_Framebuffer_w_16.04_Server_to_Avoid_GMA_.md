---
title: "Disabling Framebuffer w/ 16.04 Server to Avoid GMA 3600 Incompability"
date: 2017-05-12
forum: Hardware
---

### Post by rafterrattler on 2017-05-12
Wondering if anyone has any thoughts here.   I have an old Foxconn nt-i1500 nano PC (Atom n2700, GMA 3600) that I've was using as a VPN server running 12.04 LTS until it expired.  I was using the desktop version because I used it for other minor graphical tasks.  The thing is in great shape, and I'd like to continue using it.  Unfortunatley, support for the GMA 3600 GPU was abandoned, and later versions of Linux don't support it.   I had this brilliant idea of just loading the server version of xenial, and giving up on the graphical front end....and I did.  Unfortunately, it still apparently uses a framebuffer, and half way through the boot text, the screen goes black and the only way I can get to it is via ssh.   I have tried EVERY trick on the web I could find to disable the framebuffer usage, to no avail.  The tricks worked on my netbook (my 'sandbox'), but not on this darned thing.  Even booting in recovery mode results in a black screen...and in that case no ssh server.   I KNOW the thing can output to my monitor because I got all the installation menus, I get the grub menu, and I see half of the boot log flying by before the screen switches off.   All I want is a simple CLI after boot.  


I've tried messing with:
1. The BIOS
2. GRUB kernel command line options like vga=normal, nomodeset, i915.modset=0, nofb, fb=false, video=vesafb: off, etc.
3. Various GRUB GFXMODE, GFXPAYLOAD options like text, or specifying resolutions
4. Uncommenting GRUB_TERMINAL=console 
5. Blacklisting vesafb, vga16fb in the blacklist-framebuffer.conf
6. Recovery mode


VBEINFO at grub does give me various modes that are supported, but not sure what to do with them beyond specifying resolution in the GFXMODE grub config. (I've attached a shot of the screen)


Would anyone have any other ideas on what I can try?  FWIW, my gut tells me there should be a clue in that even recovery mode results in a black screen, as supposedly recovery mode doesn't load any graphics drivers.  Unfortunately, it also doesn't load the ssh server, so I don't even get access to look around after it finishes booting.


Thanks for any help,
RR

---

