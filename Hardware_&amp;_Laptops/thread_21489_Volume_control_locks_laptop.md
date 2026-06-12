---
title: "Volume control locks laptop"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by bnutting on 2005-03-22
I am running Hoary 5.04 preview release on a Dell Inspiron 5000 Laptop with 384MB RAM and whenever I touch my harware volume control the system locks up tighter than a drum. I have tried acpi=off as a boot-up parameter and still the same thing. As long as I do not touch the hardware volume button I'm fine, but I would like to have this fixed.

Any ideas?

Thanks,
Bryan

---

### Post by wernst on 2005-03-22
Speak of the Devil! I was JUST going to report this today too.

I have a Compaq Armada E500, and there are two buttons on the front for volume control.

On Warty (which I just upgraded from) these buttons work as expected: the volume raises and lowers.

On Hoary, the whole system freezes up solid. No mouse movement. No keyboard input accepted. I have to shut the machine off with the power button.

I expect that this is a SOUND DRIVER issue. Why?

The volume buttons are hardwired into the sound card. In Windows, for example, the buttons don't do anything UNLESS you upgrade the sound driver from the generic one to the one that Compaq has to download. Then they work.

I assume that the Warty driver had the stuff needed to make these buttons work from the get-go, or at least not crash. I am assuming this is a bug, but I don't know where to report it...

The sound driver, BTW, is for the ESS 1978 Maestro 2E, in my case. I bet it is the same for you too.

For the timebeing, the only thing I know to report it...

-Warr

---

### Post by bnutting on 2005-03-22
Maybe I should put some tape over the buttons to make sure I don't hit them on accident  ;-)

It took me a couple of reboots to figure it out, at first I thought the system had just shut down due to heat.

I hope this gets fixed because I like having the buttons.

Bryan

---

### Post by wernst on 2005-03-22
I officially added this as bug #8081 to the Bugzilla.

Let's cross our fingers on this...

-Warr

---

### Post by wernst on 2005-03-22
OK, it looks like someone is already on this one. Check out bug #7651. Apparently it is resolved and scheduled for upload for the next release.

Cool.

-Warr

---

### Post by jsgotangco on 2005-03-23
This happens to me on certain buttons but you can assign some of the buttons as GNOME keyboard shortcuts to and match with the appropriate feature/command. My laptop completely freezes when I switch on the display toggle (LCD->CRT, etc.).

---

