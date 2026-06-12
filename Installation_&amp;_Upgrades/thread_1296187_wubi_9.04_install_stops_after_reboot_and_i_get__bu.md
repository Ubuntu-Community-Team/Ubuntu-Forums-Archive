---
title: "wubi 9.04 install stops after reboot and i get  busybox prompt"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by el_mekawy on 2009-10-20
hi ubuntuforums,

I'm totally new to ubuntu & Linux.I have tried the Ubuntu live CD which worked perfectly & I liked it so much so I decided to take one more step & install it on windows using Wubi 9.04 so I can get to know better before I decide what to do with windows.

the installation goes very normal & it asks me to reboot so I reboot cleanly & choose ubuntu at the start but then all i get is busybox commend prompt

I have tried many solutions I did chkdsk & rebooted cleanly.I tried it with a bittorrent downloaded iso & with wubi downloaded iso but I got the same result.I even tried bittorrent downloaded iso of kubuntu but it failed too

I tried installing on a different partition after scanning it for errors

I modified menu.lst (replacing quiet splash with all_generic_ide & it also failed)

finally i replaced quiet splash in menu.lst with debug but when I tried the command ```
cat /tmp/initramfs.debug
```I got an error.
here's a photo of the error
[IMG]http://farm3.static.flickr.com/2701/4029686494_3e1b1401b8_b.jpg[/IMG]
My labtop is Acer Aspire 6920g running windows vista SP2.here's all the specifications of the labtop is here [http://www.acerdirect.co.uk/Acer_Aspire_6920G_Gemstone_Blue_Laptop_-_Built-in_TV_Tuner_LX.AP40X.121/version.asp#specs](http://www.acerdirect.co.uk/Acer_Aspire_6920G_Gemstone_Blue_Laptop_-_Built-in_TV_Tuner_LX.AP40X.121/version.asp#specs)
just click on tech spec if it doesn't appear

---

### Post by sushemsu on 2009-10-20
I'm not sure if it would help you at this point, but i made sure
the Cd was out and just typed exit like 10 times (more with kubuntu) until it loaded.

I've been told on other forums it's in a leading process but when I just waited for it to continue **** didn't happen : / had to exit lots.
but that was with wubi - inside windows.

as for the tmp part i'm = too much of noob to beat that one

---

### Post by el_mekawy on 2009-10-20
thx sushemsu.It worked :guitar:

I removed wubi & installed a fresh copy.I got the prompt like every time I tried to install wubi 9.04

I used the command exit 3 times after the 1st 2 times I got nothing but it worked after the 3rd :)

I tried google & searched ubuntuforums but no one this way to solve it

---

