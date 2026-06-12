---
title: "Live/Install CD Problems"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by fflarex on 2007-05-31
So I've been looking into Ubuntu for *long* time, always holding back because of an incompatible wifi driver (intel 4965agn, which now seems to be working with ndiswrapper). However, now that I'm trying to actually install it on my system I'm afraid that may not have been the only incompatible hardware I have. When I try to run the live cd, I get the following message: "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" I wouldn't mind installing Ubuntu with the alternate text install cd, but I want to make sure it will work before I go and do that. I'm also afraid b/c my bios is made by Phoenix and I've heard they've been bragging about making their firmware compatible only with Vista. Help anyone?

Laptop model is Gateway NX570XL, and I can provide more hardware details if you need it. I really want to make the full switch to open source, but if I have to buy new hardware to make it work, it's probably not happening.

---

### Post by frozinfire on 2007-05-31
Have you tried changing the video driver it uses? Run "sudo dpkg-reconfigure xserver-xorg" and manually set it to "Vesa." When you finish, save the changes and run "sudo killall -9 Xorg" to restart the X server.

That fixed the problem for me, so hopefully it'll work for you.

---

### Post by fflarex on 2007-06-01
> **frozinfire said:**
> Have you tried changing the video driver it uses? Run "sudo dpkg-reconfigure xserver-xorg" and manually set it to "Vesa." When you finish, save the changes and run "sudo killall -9 Xorg" to restart the X server.

That fixed the problem for me, so hopefully it'll work for you.

Didn't work for me. As far as I can tell (and admittedly, I can't tell very far), it was already set to vesa. However, I still followed your instructions as closely as possible and it didn't help any either. :(

---

### Post by fflarex on 2007-06-02
Anyone? I know you guys probably don't have enough info from me to answer, but I don't even know what info to provide.

---

### Post by ugm6hr on 2007-06-02
> **fflarex said:**
> So I've been looking into Ubuntu for *long* time, always holding back because of an incompatible wifi driver (intel 4965agn, which now seems to be working with ndiswrapper). However, now that I'm trying to actually install it on my system I'm afraid that may not have been the only incompatible hardware I have. When I try to run the live cd, I get the following message: "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" I wouldn't mind installing Ubuntu with the alternate text install cd, but I want to make sure it will work before I go and do that. I'm also afraid b/c my bios is made by Phoenix and I've heard they've been bragging about making their firmware compatible only with Vista. Help anyone?

Laptop model is Gateway NX570XL, and I can provide more hardware details if you need it. I really want to make the full switch to open source, but if I have to buy new hardware to make it work, it's probably not happening.

Most likely problem is that you have an ATI graphics card.  There will probably be a stickeron the front that tells you that.  If so - this might help:
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

Unfortunately, the only way to check if it will work before installing is to ask someone with the same laptop (or possibly just the same graphics card).

---

### Post by fflarex on 2007-06-02
Thanks, I think it may have been the graphics card. I ran a search for the ATI Mobility X1400 and found out that the problem was with the Feisty Fawn live CD. I tested out Dapper Drake (b/c I couldn't find Edgy anywhere... hmm...) and found that it worked fine. So now my plan is to install Drake or Edgy and then upgrade from there, but I have two final questions before I dive right in.

Will it be a pain to resize my partitions if I don't get them right the first time? (I'm dual booting Vista)
How can the instructions/help [here]("http://ubuntuforums.org/showthread.php?t=458035&highlight=intel+4965agn") be adapted to install ndiswrapper and the appropriate driver(s) from a keydrive? If I absolutely have to, I can find a way to get wired internet, but believe me it will be a pain in my particular situation.

---

### Post by Makilaz on 2007-06-02
I have this exact problem, except I have an nvidia card. Now, I installed a PCI nvidia card because Intel makes crappy cards, but if I revert back to the integrated card, it works fine. Only in 640x480 resolution, but I don't get any X server errors. This wouldn't be a problem if not for the fact that I'm getting a laptop with an nvidia graphics card and I'm worried about having the same problem. Any suggestions?

---

