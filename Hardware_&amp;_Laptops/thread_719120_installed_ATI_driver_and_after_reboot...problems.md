---
title: "installed ATI driver and after reboot...problems"
date: 2008-03-08
forum: Hardware &amp; Laptops
---

### Post by Kevin Jones on 2008-03-08
Hello all,
This is my problem:
 have downloaded Ubuntu 7.10 Easy download, easy install. Everything worked well.
I have an ATI radeon X1300 video card.
A prompt at the top of the screen showed that there were downloads for restricted drivers, and the screen showed that a Radeon driver was available. I ticked it, and it was 'enabled'
Nice and smooth so far.
on reboot I get half the screen black. Very poor resolution and what appears five log in screens side by side but barely legible. (horizontal lines obscure everything)
ctrl alt F1
does not seem to do anything,
Can anyone help?

Kevin

---

### Post by overdrank on 2008-03-08
> **Kevin Jones said:**
> Hello all,
This is my problem:
 have downloaded Ubuntu 7.10 Easy download, easy install. Everything worked well.
I have an ATI radeon X1300 video card.
A prompt at the top of the screen showed that there were downloads for restricted drivers, and the screen showed that a Radeon driver was available. I ticked it, and it was 'enabled'
Nice and smooth so far.
on reboot I get half the screen black. Very poor resolution and what appears five log in screens side by side but barely legible. (horizontal lines obscure everything)
ctrl alt F1
does not seem to do anything,
Can anyone help?

Kevin

HI and you can try and boot into recovery mode which is usually the second choice in the grub. Then reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then use the command ```
reboot
``` hopefully this will get you to a GUI, Desktop. Then you may look at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
 Good luck.

---

### Post by Kevin Jones on 2008-03-08
Thanks,
safe mode got me into a command line
I am running the set  up now
Is there any way I can access the default settings for this set up?
It seems that with every choice i make I get booted back to the command line:
"xserver-xorg postinst warning: overwriting possibly customised configuration file; back in /etc/x11xorg.conf.20080308214922

If I entered this command: /etc/x11xorg.conf.20080308214922
would I be able to see my default settings?

thanks

Kevin

---

### Post by Kevin Jones on 2008-03-08
Hi overdrank, and all

would:
 sudo dpkg-reconfigure xserver-xorg
instead of:
sudo dpkg-reconfigure -phigh xserver-xorg

work better? Or will I end up in the same state?

thanks 
Kevin

---

### Post by overdrank on 2008-03-08
> **Kevin Jones said:**
> Hi overdrank, and all

would:
 sudo dpkg-reconfigure xserver-xorg
instead of:
sudo dpkg-reconfigure -phigh xserver-xorg

work better? Or will I end up in the same state?

thanks 
Kevin

Hi and if you use the first command without the tag -phigh then you will be able to choose the driver like vesa and other options. The -phigh tag is like automatic.

---

### Post by Yellow Pasque on 2008-03-08
Kevin, the best thing to do right now would be to remove the Proprietary driver and reconfigure X so you have a clean xorg.conf. Also, make sure XGL (xserver-xgl) is not installed. Then try the latest Catalyst 8-3 drivers using this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

So,at the terminal, run the following to remove fglrx and download the latest ATI Catalyst:
```
sudo apt-get remove xorg-driver-fglrx
sudo dpkg-reconfigure -phigh xserver-xorg
sudo wget --no-check-certificate https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-3-x86.x86_64.run

```

Note: -phigh will get you a clean xorg.conf faster IIRC

---

### Post by BooBooNTZU on 2008-03-09
You can keep the restricted drivers just fine , but you have to reconfigure X or edit the xorg.conf

Take 1.

sudo  Xorg -reconfigure
sudo cp xorg.conf.new /etc/X11/xorg.conf
sudo  aticonfig --initial -f

Take 2.

sudo dpkg-reconfigure xserver-xorg
sudo aticonfig --initial -f

Take 3. 

sudo dpkg-reconfigure xserver-xorg             and select FGLRX instead of ATI

Take 4.

sudo nano /etc/X11/xorg.conf         and change everything you want

---

