---
title: "ATI 5750 Drivers (Black Screen)"
date: 2010-03-26
forum: Hardware
---

### Post by kru83 on 2010-03-26
Hi.  i just installed Ubuntu 9.10.  I have ATI 5750HD Video card.  I used envyng to install the recommended ATI driver which is 8.660.  Once i rebooted the computer after the ubuntu splash screen the monitor goes black (but i can hear the sound in the background, i can even log in the system by click on left mouse and typing in the password and hit enter)  for now i booted up in the console and removed the ati driver using Envyng.  Whats the solution to this problem.

I was gone try using the open source drivers, but the to see if my card is compidibale with it. i had to type in {lspci -nn | grep vga} but i get no reply back on the terminal.

Thanks for your help in advance.

Edit: i have also tried using the proprietary driver FGLRX from the hardware drivers menu, but i get the same black screen.

I HAVE hannspree HF237 model monitor. its hooked up with VGA port via DVI Adapter.. (does this have anything to do with it ?

---

### Post by kru83 on 2010-03-26
Problem solved.

i downloaded the ATI Driver from its web site,  i had the same problem but after reading some docs on the site, i found out that X server had fail to start. so i had to go in the console and type in aticonfig --initial -f.  after the restart it worked.

---

### Post by Bernardobr on 2010-05-01
Hi guys, I have almost the same card (HD5650) and I have the same problem. Except that I can never get through the black screen. Everytime I turn it on, it shows the ubuntu splash screen and then goes black. I press shutdown and I can see the splash screen again, this time shutting down. I have tried booting from the recovery mode but I get the same results.

Any ideas? Thank you very much!

---

### Post by DaPale on 2010-05-02
Hi,

I also have this problem, but only when I logoff to the logon screen or perform a Fast User Switch.
Then the screen goes black. I have a ATI 4500 series card.

---

