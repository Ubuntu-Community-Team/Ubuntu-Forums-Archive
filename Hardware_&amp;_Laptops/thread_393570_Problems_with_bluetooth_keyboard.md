---
title: "Problems with bluetooth keyboard"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by LanceUppercut on 2007-03-25
Hi everybody

I'm having problems using my Microsoft blue tooth keyboard. The blue tooth dongle works fine, and so does my blue tooth mouse, however, whenever I try to connect to my keyboard, everything starts to get screwy. ill use

sudo hidd scan

and it will find and connect to it ok, but then i am unable to interact with anything except the terminal. If I close the terminal then I'm only able to interact with the next window i bring up, and eventually i have to restart. It's very strange, because it is only the keyboard that does this. Anyone have any ideas about whats going on?

my hcid.conf is this:

options {
      autoinit yes;
      security auto;
      pairing multi;
      passkey "1234";
}
device {
	name "%h-%d";
	class 0x3e0100;
	iscan enable; pscan enable;
	discovto 0;
	lm accept;
	lp rswitch,hold,sniff,park;
}

thanks for your help!

---

