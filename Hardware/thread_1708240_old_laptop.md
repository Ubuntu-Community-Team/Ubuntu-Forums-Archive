---
title: "old laptop"
date: 2011-03-16
forum: Hardware
---

### Post by mindheist11 on 2011-03-16
Hello. I just installed Ubuntu 10.10 on a old laptop (Compaq Evo N1015v) and it won't login to the normal gnome desktop. It only works if I select SafeMode. Could anyone please help?

---

### Post by JRV on 2011-03-16
What graphics hardware does it have?

---

### Post by kev77 on 2011-03-16
Found this relating to suse, may help...


[I][B]If you replace the XFree86 radeon drivers with these binaries, you\'ll get 2D-accelerated X /no 3D acceleration :-(/ and support for Xv -> decent DVD playback. Best wishes, Martin

It works fine with the VESA frame buffer device driver from Xfree86 4.3. Suse takes care of all this normally, however you can always set the resolution by passing vga=791 to the kernel. i.e put this in the bootloader config:
>run yast (commandline or X)
>goto system
>goto bootloader config
>edit configuration
>add vga=791 to the end of the default option[/B][/I]

[http://www.chriskirkland.net/news/50.html]("http://www.chriskirkland.net/news/50.html")

---

### Post by mindheist11 on 2011-03-16
> **JRV said:**
> What graphics hardware does it have?
It's an onboard graphics card. The laptop is rather old. Do you know what I might be able to do?

---

### Post by mindheist11 on 2011-03-16
Oh and I wouldn't mind staying in safe mode but the network driver doesn't appear to be working either. Please don't make me go back to windows.

---

### Post by IcarusR on 2011-03-17
You could try adding vga=791 as a kernel boot option & see if it will then boot. Instructions here...

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation]("https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation")

---

### Post by KegHead on 2011-03-17
Hi!

I have a old Compaq v5000 w/amd chip running 9.04.

You could try 9.04!

KegHead

---

### Post by cr8ai7g6 on 2011-03-17
I just went through solving video problems on my Dell Latitude c400.
Try this - type "xrandr" (sans quotes) and you should get a listing
that tells your graphics device. 
That info might tell you which driver is needed.

                                      hope this helps
                                              cr8ai7g6

---

