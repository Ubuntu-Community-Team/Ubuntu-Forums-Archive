---
title: "boot problem on asus p5q3"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by fajarhp on 2008-12-31
please help me!
on live cd I have problem with booting, but I can solve this. I try to type command

[I]boot: live generic.all_generic_ide=1
[/I]
it can boot on live cd succesful.
but when after i have tried to install on hardisk. ubuntu failed to boot.on monitor only showed freezing splash screen.

note: my ubuntu is ubuntu 7.10 gutsy gibbon.
      mb asus p5q3 deluxe wifi
      sata western digital wd5000 series.
      2x2 gb ddr3 1066hz corsair
      cpu intel q9400
      vga ati radeon hd 4670

---

### Post by decoherence on 2008-12-31
get in to grub by pressing escape early in the boot process (watch for it... it'll prompt you for a second or two)

press 'e' then highlight the line that starts with 'kernel' and press 'e' again. remove the words 'quiet' and 'splash' press return then press 'b'

you should get some (hopefully useful) information when it cacks out.

---

### Post by fajarhp on 2008-12-31
i have already tried it. as you said

[I][I]get in to grub by pressing escape early in the boot process (watch for it... it'll prompt you for a second or two)

press 'e' then highlight the line that starts with 'kernel' and press 'e' again. remove the words 'quiet' and 'splash' press return then press 'b'[/I][/I]

and on screen displayed full of text,and it hadn't worked. 


still "freeze"

---

### Post by decoherence on 2008-12-31
Yes, I wasn't expecting it to work. I would like to know what it says on the screen. There is no way to copy/paste it here, though, so you'll have to copy it by hand. If you have a digital camera, you can take pictures of the screen and post them here. Sorry there isn't an easier way.

I'm going to make a wild suggestion that you can try in the mean time. Do the same thing I asked you to do above, but after you remove the words "quiet" and "splash" go to the end of the line, type a space, then

generic.all_generic_ide=1

press enter and 'b'

this is what you'd call a 'shot in the dark'. here's hoping!

---

### Post by fajarhp on 2008-12-31
thanks for your suggestion. i will try it next.

---

