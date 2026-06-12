---
title: "Have a question about &quot;trying ubuntu&quot;"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by qjmoss on 2009-05-01
Okay, so, here's a personal story. I stopped by my dads house today, he was telling me how he has this terrible virus on his dell pc, running windows xp. I was like, well duh.. your running windows, and you have kids,of course it's going to have a virus.  I said, why don't you try Ubuntu, I"ll bring my flash drive over tomorrow and i'll put it on for you.  

Now, heres my question.  When he reformats his pc, he boots into 98, and uses fdisk.

and with the grub boot loader, will he run into problems reformatting the whole pc if he doesnt end up likeing ubuntu?

Will it be an easy process formatting everything back to normal?

I don't want him to get stuck with a nousable hard drive..


Any information would be great!


Thank you for your time

---

### Post by Spaceman9 on 2009-05-01
If he's never used linux and has windows you could use the alternative install CD and Wubi. With Wubi he can install Ubuntu into a folder. That way he doesn't have to format anything or partition anything and if he doesn't like Ubuntu he can uninstall it with one click.

---

### Post by qjmoss on 2009-05-01
Well, the problem is, is that he can't access anything.. once he starts the computer, it is hijacked.

So what I was going to do, was pop my usb drive in, and install ubuntu over the old partition,and go from there..

But, I'm not really sure what would happen, because he has a floppy disk with windows 98 and he boots into dos and formats from there.


Would this still work if he has ubuntu installed?

---

### Post by ezsit on 2009-05-01
> he boots into 98

Get the specs on his computer first and verify if a current Linux will even run on his hardware. Also, if he is running Win98 on a computer built around that time, I doubt it would boot from USB, bring a liveCD instead. Win98 is ancient and his hardware might be too. Check the RAM, HD space, and processor speed. If you are planning on using an older Linux or something like Puppy, then nevermind my suggestions, Puppy should run on it. :-)

---

### Post by Mark Phelps on 2009-05-01
> **qjmoss said:**
> Now, heres my question.  When he reformats his pc, he boots into 98, and uses fdisk. 

and with the grub boot loader, will he run into problems reformatting the whole pc if he doesnt end up likeing ubuntu?

Will it be an easy process formatting everything back to normal?

I don't want him to get stuck with a nousable hard drive..
I'm concerned that you may be looking for a simple way to do the following:
1) Replace W98 with Ubuntu
2) If your dad doesn't like Ubuntu, just restore W98

The problem is that 1) is easy -- boot from a LiveCD, select the entire drive for Ubuntu, let it reformat the drive and install, reboot, and your done.

But ... 2) is very hard -- because you would have to image off the W98 installation first to external media using some MS Windows utility like Ghost or Acronis True Image (both of which cost $$), then when you went to restore the image, you would have the same infected system you have right now.

So, I'd like to suggest an alternative approach -- clean up the W98 installation first, before you image it off or replace it.

If your machine can boot from CD, you can google for Kaspersky Rescue CD or BitDefender Rescue CD, download each of them (for free!!), boot from them and run antivirus scans on your PC.

The ironic part is that these are both MS WIndows antivirus tools, but they both boot from ISOLinux CDs.

---

### Post by Hobgoblin on 2009-05-01
> **qjmoss said:**
> 

Now, heres my question.  When he reformats his pc, he boots into 98, and uses fdisk.

and with the grub boot loader, will he run into problems reformatting the whole pc if he doesnt end up likeing ubuntu?


I don't know what everyone is getting so confused about.

Simple answer is no.

Fdisk will be able to remove/replace the Linux partitions just as it does the Windows ones.

---

### Post by yoasif on 2009-05-01
Ubuntu may be a bit heavy by default for that hardware -- you may want to install debian with lxde instead. 

[http://cdimage.debian.org/debian-cd/5.0.1/i386/bt-cd/](http://cdimage.debian.org/debian-cd/5.0.1/i386/bt-cd/)

you want the debian-501-i386-xfce+lxde-CD-1.iso

---

### Post by wpshooter on 2009-05-01
qjmoss:

Get [www.killdisk.com](www.killdisk.com) and WIPE the entire hard drive clean.

Then you can put whatever O/S you want to on the system as long as you have a valid bootable copy of the O/S.

WIPE it with Killdisk, install O/S, see if he likes it, if not, use Killdisk to WIPE it again and install whatever other O/S he may want.  I would highly recommend that WIN98 be forgotten about !!!

---

### Post by Spaceman9 on 2009-05-15
I used Win 98SE until June of 2007. I've just used Linux since then. I was thinking though, for a Linux newbie I wouldn't really recommend Ubuntu or Kubuntu. I'd give them the new version of PCLOS. There's a KDE 3.5.10 version and a Gnome 2.24.3 version. It's easier to install, has a lot more multimedia stuff out of the box, can do higher screen resolutions with old vid cards then the buntus and you don't need to learn as many CLI's to use it right away.

I don't use PCLOS now because there's no KDE 4 version. I use Kubuntu 9.04 and UbuntuStudio 9.04.

---

