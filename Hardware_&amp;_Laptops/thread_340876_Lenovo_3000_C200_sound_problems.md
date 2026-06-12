---
title: "Lenovo 3000 C200 sound problems"
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by Fred_C on 2007-01-17
I've just installed Ubuntu 6.10 on a Lenovo 3000 C200 laptop. Everything seems to be more or less working. The internal wireless is not running yet, but I'm confident that I can get that going with ndiswrapper once I find the appropriate drivers and all. 

But the sound has been a no-go from the start. I've tried just about every bit of instruction on-line - added  options snd-hda-intel model=laptop-eapd  as well as other variations, installed new alsa drivers, etc. and haven't gotten a solution. 

I do get some sound out of the headphone jack, but it is very low. 

Does anyone have any advice on this?

](*,) 

thanks!

---

### Post by Fred_C on 2007-01-18
Hello... anyone got any advice on this?

---

### Post by mavnn on 2007-01-19
I've been having exactly the same issue, but I'm afraid that I've not come up with anything yet either.

Quiet sound from the headphone jack is the best I'm getting...

As an aside, the wireless seemed to work fine with 6.10 for me, so hopefully you've not had any problems getting that sorted out.

Mavnn

---

### Post by Fred_C on 2007-01-19
Thanks for the reply. To be honest I haven't messed around much with the wireless because I had an Orinoco card from my old laptop that worked immediately. But the sound thing is driving me kind of nuts. 

Hopefully it'll get worked out soon.

---

### Post by mavnn on 2007-02-09
Fred_C, have you spotted [http://ubuntuforums.org/showthread.php?t=349231&highlight=c200](http://ubuntuforums.org/showthread.php?t=349231&highlight=c200) ?

It seems to fix the problem with the inboard speakers, although they don't stop when you plug in the headphone jack!

Michael

---

### Post by Fred_C on 2007-02-14
Thanks for the tip... I've read through the instructions / posts and came to the "set the boot options to acpi=ht " but to tell you the truth, I don't know how to do that. Any hints?

---

### Post by Fred_C on 2007-02-14
I just saw the message you sent earlier regarding changing the boot options... thanks!

---

### Post by mavnn on 2007-02-23
Wasn't me, I'm afraid! Still, good to hear that you've got it all working :)

---

### Post by Fred_C on 2007-04-27
Does anyone know if this is fixed in 7.04?

Thanks

---

### Post by shabri on 2007-04-28
> **Fred_C said:**
> Does anyone know if this is fixed in 7.04?

Thanks

Sadly not. How *do* you "set the boot options to acpi=ht " ? :(

---

### Post by Fred_C on 2007-06-29
Did you ever get an answer to this?

If not, lemme try to see if I remember....

in terminal
$ sudo nano /boot/grub/menu.lst

that should open the menu.lst file for editing, move your cursor down to:

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

At the end of that third line that starts with "kernel", add acpi=ht 

it'll then look like

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash acpi=ht
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot


Hit ctr x to get out... it'll ask if you want to save it, hit yes

and you should be good to go.

---

### Post by TopKat59 on 2007-07-03
I added your fix and it did make the sound work after rebooting.  However adjusting the volume while playing anything still causes sound failure.  And for reasons unclear there is both a crackling sound just before any sound plays as well as a presistent extremely high pitched sound when anything is playing.  I went back to nano /boot/grub/menu.lst. but could not find the code that I added to edit out.  Have any idea what I should do?  Thanks

---

### Post by NoFearDJB on 2007-07-31
still looking for a real fix on this issue

---

