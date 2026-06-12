---
title: "Ubuntu New installation help"
date: 2008-08-26
forum: General Help
---

### Post by ^^rac on 2008-08-26
Hi guys!

Sorry to bother yous. I want to start using Ubuntu, and want to check it out....

After i completed the installation, it booted (I could see the boot screen)
But when it snaps to the login, the screen is all messed up, i cant read anything.....

I rebooted and went to reconfigure the screen trough some commands some guys give me....

Im using res 1440 * 900 on a 7300GT Geforce, with an Acer 19 inch wide screen.

It does not give me any Gforce card options when i want to select the display drivers....

Is there any default settings i can use to make this work?

Or how do i work around this......

I tried twice, it boots into a blue screen, telling me about the screen config not being correct.

Thanks for the help guys! I am a total N00b to Ubuntu etc's!

---

### Post by Dojan5 on 2008-08-26
Boot into a safe terminal and start XVesa.
The safe booting should be in the GRUB boot options.

---

### Post by ^^rac on 2008-08-26
> **Dojan5 said:**
> Boot into a safe terminal and start XVesa.
The safe booting should be in the GRUB boot options.

Hi!!

Thanks for your quick response.....

After i do ctrl-alt-f1, where do i go?

Thanks a mil!

Ps: After i boot into safe booting, where do i fix the problem?
(Do one have to get drivers for 7300GT or can i use generic stuff on Ubuntu?
:)

---

### Post by Ryadt on 2008-08-26
> **^^rac said:**
> Hi!!

Thanks for your quick response.....

After i do ctrl-alt-f1, where do i go?

Thanks a mil!

Ps: After i boot into safe booting, where do i fix the problem?
(Do one have to get drivers for 7300GT or can i use generic stuff on Ubuntu?
:)

Try```
startx
```

---

### Post by ^^rac on 2008-08-26
> **Ryadt said:**
> Try```
startx
```

Hi,

i did that, but gives me some fatal error.

This is what i did:


CTRL-ALT-F1, log into the text terminal, then:
Code:
sudo dpkg-reconfigure xserver-xorg
and go through the whole process.

Once finished test with:
Code:
startx
and then if it is ok, log out of the graphics screen and:
Code:
sudo reboot


But not sure wich screen drivers etc i must use?

---

### Post by Crafty Kisses on 2008-08-26
What are your system specs?

---

### Post by ^^rac on 2008-08-26
> **Codename said:**
> What are your system specs?

Hi

AMD Sempron 3000+
1.5GB RAM
Inno3d 7300GT

I dont think i have the correct drivers.....not sure what to use, thx for the help!

---

### Post by ^^rac on 2008-08-26
Anyone?

I appreciate....

---

