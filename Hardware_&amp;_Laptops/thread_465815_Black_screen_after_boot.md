---
title: "Black screen after boot"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by stigert on 2007-06-06
Hello,

I installed Ubuntu 7.04 today. I followed all the steps, and the installation went great, untill i rebooted my computer. The loading/boot screen came, but when that is done, the screen stays black. Ubuntu dosen't starting. 

What can i have done wrong? I have tryed with my own burned ISO file, and with the CD's i ordered for this site.. I use 32bit verison. (on a 64bit amd hp laptop)

---

### Post by renzokuken on 2007-06-06
sounds like maybe a grafix driver / xorg.conf issue.

what grafix chipset/card do you have?

---

### Post by stigert on 2007-06-06
It's a NVIDIA card. But i havent installed somthing, because i can't logon. It's only a black screen after the boot.
How can i fix the xorg.conf? :-o

---

### Post by stigert on 2007-06-06
Bump?

I get this error on startup

[http://bildr.no/view/73107](http://bildr.no/view/73107)

---

### Post by renzokuken on 2007-06-06
if thats as far you can get you cant, but that error suggests its not an xorg.conf error anyway. more like a hardware error.

is all your ram and nvidia card plugged into the mobo securely?

---

### Post by stigert on 2007-06-06
I had Ubuntu on this machine before.

is all your ram and nvidia card plugged into the mobo securely? - what do you meen?

---

### Post by renzokuken on 2007-06-06
ok, its a laptop, i'm being an idiot !!! hehe

at what point does this error come up? after the bios splash? does the ubuntu boot loader logo come up at all? do you get past grub?

also, do you have a CardBus inserterd (PCMIA or something like that)?

---

### Post by stigert on 2007-06-06
The error comes at the beginning at the startup. I can the se ubuntu logo and loading.
the screen is turning black when the loading is done.
it comes something like grub15 ore somthing, cant remember.
if i click ESC there i can choose if i want to strart in recovery mode or normal

---

### Post by renzokuken on 2007-06-06
so its a kernel issue by the sounds of it. kernel is having a problem with some of your hardware.

do you have any peripheral devices plugged in? wireless cards/mice/hubs etc?

---

### Post by stigert on 2007-06-06
Only the power supply.. I have a wireless network card in it. But the card is integrated..
But i have disabled it by turn the button off..

---

### Post by renzokuken on 2007-06-06
have you tried it with it enabled?

---

### Post by renzokuken on 2007-06-06
sadly you are not alone, i've found quite a few reports for it but no real solution.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/54294](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/54294)

 may be worth downgrading to Edgy. what model is your laptop?

---

### Post by stigert on 2007-06-06
What is Edgy? Im very new at linux..
I have a HP Pavilion dv6128eu.. 
It's strange, because u have had Ubuntu on it before :S

---

### Post by renzokuken on 2007-06-06
after some reading around it appears to almost definately be the grafix chipset causing it. not sure what to about it though. not like you can change the grafix card in a laptop.

---

### Post by renzokuken on 2007-06-06
edgy is the release before the current feisty release

ubuntu feisty fawn 7.04
ubuntu edgy eft 6.10
ubuntu dapper drake 6.06
ubuntu breezy badger 5.10

......etc etc

you can get it from [http://releases.ubuntu.com](http://releases.ubuntu.com)

---

### Post by stigert on 2007-06-06
allright.. i'll just wait until ubuntu come with a version that will fix this problem. hehe
but what is the difference in this two versions?
do they look the same?

---

### Post by Crafty Kisses on 2007-06-06
> **stigert said:**
> It's a NVIDIA card. But i havent installed somthing, because i can't logon. It's only a black screen after the boot.
How can i fix the xorg.conf? :-o
You can try to reconfigure your xorg.conf file, try this:
```
sudo dpkg-reconfigure xserver-xorg
```
Hope this helps. :)

---

### Post by stigert on 2007-06-06
renzokuken: i installed the 6.10 now. the error is gone, but i get black screen after slapsh screen

---

### Post by bcollignon on 2007-06-06
just for the fun of it, when grub loads try editing in progress, which grub allows.  Get rid of the line which says" ro quiet splash" if it exists.  If you're editing in progress, the edits are not saved beyond one boot.  The menu.lst file must be edited manually to get rid of the line.

---

### Post by renzokuken on 2007-06-07
> **stigert said:**
> renzokuken: i installed the 6.10 now. the error is gone, but i get black screen after slapsh screen


then its definately a grafix issue i guess.

when it boots and the falls to the black screen, press Ctrl+Alt+F1 to get to a TTY terminal.

log in and type the following command

```
sudo dpkg-reconfigure xserver-xorg
```

a wizard will pop up that allows you to change xorg settings. leave everything as it is until you get to the DRIVER section. select the "VESA" driver. you could also try the "NV" driver too. continue on leaving everything else as it is. finish the wizard then reboot

```
sudo reboot
```

see if that helps

EDIT, as for the difference between 6.10 and 7.04, theres isnt much noticeable difference at all no. just some newer software. apart from that it looks and works exactly the same as 7.04.

---

### Post by El Mono on 2007-11-02
Hello!

I am quite new to linux too and i have the same laptop and same problem. I am trying to start ubuntu with the latest live cd downloaded. (7.10). I tried to do as renzokuken said on his post. CTRL+ALT+F1 to get the terminal open and then write "sudo dpkg...." Well the problem for me is that the black screen still remains as i press CTRL+ALT+F1.

So, what to do?

Thank you.

---

