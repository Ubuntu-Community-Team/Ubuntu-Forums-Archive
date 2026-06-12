---
title: "1st Post Please HELP: Want to Install Ubuntu 7.10 (Gutsy) on my DELL Inspiron 1720"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by Chrisoldinho on 2008-01-04
Hello everyone! I've heard such good things about Linux I thought it was about time I ditched MS and gave it a go! :)

Some of these questions may be specific to owners who have this laptop already but I would also appreciate help from any 1520 owners or infact any Ubuntu user who can help me get this setup.

As a linux newbie I have some very Windows'y questions before I begin mainly in relation to driver installation.

AHCI - The HDD is set to use this in the BIOS, does Ubuntu need any special drivers to use this facility or should I just use ATA?

Graphics Card - Can I just download this from the NVIDIA web site after the install is complete?

Intel Turbo Memory - Is this completely redundant on a Linux laptop?

Card Reader - I needed card reader drivers to get my laptop working in x64 Vista Ultimate, will I need drivers for Linux for these, or again is all of this stuff automatically installed with Ubuntu?

And finally, should I opt for x86 or x64 - From the Ubuntu site: Choose X64 this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead.

Does this mean it doesn't currently support x64 on Intel Dual Core CPU's????

Thanks for any assistance, Chris.

---

### Post by njparton on 2008-01-04
Here are some initial responses to get you started, starting with your AHCI question:

No, just go for it.

Linux will use the generic VESA driver to start with. Ubuntu will then give you the option after first boot to install proper nvidia drivers.

Not sure about that one - no big deal though I'm betting. Ignore.

Search the manufacturers website or just plug it in and see. You *may* be pleasantly surprised.

X64 if you have a modern Athlon or Core 2 Duo/quad processor (or any of the mobile equivalents).  The AMD64 name is a bit confusing - it actually supports Intel processors too.

---

### Post by Chrisoldinho on 2008-01-04
Thanks for the reply njparton. The processor is a T7500 2.2 Dual Core - I don't know what the model name for it is (i.e. Barton, Athlon or whatever) but it is in laptop terms very modern.

I'll attempt to download the ISO tonight, back up my Vista documents then go for it tomorrow.

One other thing. My computer has Dell Media Direct installed which basically is basically on it's own partition and runs off Windows XP Embedded. I can boot straight into that instead of loading Windows which is a nice touch for playing music etc. Does anyone know if this will this still work if I format Vista (you think it would given that it's on it's own logical partition away from the primary one but for some reason you install it through Vista instead of it's own installer).

Chris.

---

### Post by njparton on 2008-01-04
Go for the AMD64 distro for that CPU.

As for the Dell question, maybe a dell owner here will pick this up or maybe you should post that question specifically under the windows section.

---

### Post by Chrisoldinho on 2008-01-04
Thanks will do, consider yourself "thanked" you for your help :popcorn:

As a final question, I understand Ubuntu comes with lots of applications shipped as standard. I assume it can read PDF's, view Flash/Shockwave material and has Firefox installed (Thunderbird it's called on Linux right??).

Chris.

---

### Post by njparton on 2008-01-04
Thunderbird is an email app for both linux and windows.

Firefox is Firefox everywhere :)

Everything you want to do can be done.  Some may need some tweaks to get working. Search for help here for specific issues as you come across them.

---

### Post by mmslayer on 2008-01-04
If you want to use MediaDirect, you will have to keep a Vista partition. I found this guide which worked great (I used option 2, and did a fresh Vista install). I also have a 1720 with T7500 processor.

[http://ubuntuforums.org/showthread.php?t=577469&highlight=1520&page=9](http://ubuntuforums.org/showthread.php?t=577469&highlight=1520&page=9)

I had to play around w/ Firefox to get Flash working, it was not installing correcting from Synaptic (there was a problem w/ the md5sum on the file).
 
- Install nspluginwrapper via Synaptic
- Get Flash 9 from [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
- Copy “libflashplayer.so” from that folder into the /usr/lib/mozilla/plugins
- Run "sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so"

Full instructions are here:
[http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)

Alot of info for the 1520 also applies to the 1720 (particularly to get sound working) so this entire thread is helpful:
[http://ubuntuforums.org/showthread.php?t=577469&highlight=1520](http://ubuntuforums.org/showthread.php?t=577469&highlight=1520)

You may also want to look at [http://linux.dell.com](http://linux.dell.com)

Hope my ramblings help.

---

### Post by linux22 on 2008-01-04
I still recommend that you try the normall ubuntu flash install first, it makes it cleaner when you upgrade and stuff. 

This link details the normal way to install flash...

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

If it doesnt work, simply use the above posts instructions.

Hope this helps, I am on a Dell Inspiration 7500 which was factory installed with windows 98, so there really is no comparison.

---

