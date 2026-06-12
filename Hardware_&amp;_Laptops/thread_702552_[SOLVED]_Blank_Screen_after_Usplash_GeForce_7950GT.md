---
title: "[SOLVED] Blank Screen after Usplash GeForce 7950GT"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by philidox on 2008-02-20
If you want the the specifications for my video card follow the url:
[http://www.newegg.com/product/product.aspx?Item=N82E16814143090](http://www.newegg.com/product/product.aspx?Item=N82E16814143090)

I am running Ubuntu Gutsy

Ubuntu was running fine until I install a different nvidia driver I ran this command specifically
1.sudo apt-get install nvidia-glx-legacy
2.sudo apt-get install nvidia-legacy-kernel-source

It change my xorg.conf and I did not back em before hand.  I had the same blank screen issue before but I was able to fix it with editing the xorg.conf file and putting something special after the "DRI" section but I cant find that fix on the net like I did before(shoulda bookmarked it!!!)

I've been googling for hours someone please help me fix my xorg.conf settings

Like I said its was something after the DRI that I had to edit in like hwcursor or something like that, if you can help find a fix that would be great.

---

### Post by Yellow Pasque on 2008-02-20
Why were you trying to install the legacy driver for such new hardware?

Try booting with the nosplash option. You may need to press 'Esc' to get to the boot menu when your PC starts. You can then edit the options after the root= option (sorry, that's a bit of a half-assed description, but I think you'll see what I mean).

AFter it boots, hopefully you can press Ctrl+Alt+F1 to get to a terminal and uninstall the legacy packages. Then, install the new ones, e.g:
```
sudo apt-get remove nvidia-glx-legacy nvidia-legacy-kernel-source
sudo apt-get install nvidia-glx-new
```

Good luck.

---

### Post by philidox on 2008-02-20
Worked like a charm! Thx

---

