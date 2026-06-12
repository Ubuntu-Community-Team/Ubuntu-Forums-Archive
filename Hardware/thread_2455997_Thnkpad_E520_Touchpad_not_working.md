---
title: "Thnkpad E520 Touchpad not working"
date: 2021-01-01
forum: Hardware
---

### Post by veloo on 2021-01-01
Just installed Ubuntu LTS and everything seems to be working apart from the touchpad. I can't move the mouse or tap. Left button does not work, but right button seems to work. I haven't changed any configs anywhere.

I would like to enable this touchpad, and keep it enabled permanently.

---

### Post by bigmeme2 on 2021-01-01
I am assuming the touchpad was working while you were installing Ubuntu. Did you make sure to tick the "install proprietary software/download 3rd party software" option when installing? If you did do those things, you may have a corrupted install. You should then reformat your boot device and re-download the Ubuntu ISO. Make sure to run a checksum on the ISO before actually using it to install Ubuntu.

---

### Post by veloo on 2021-01-01
> **bigmeme2 said:**
> I am assuming the touchpad was working while you were installing Ubuntu.
Touchpad was not working while installing Ubuntu.

This laptop has a trackpoint between the keyboard which is working but I find it hard to use.

> **bigmeme2 said:**
> Did you make sure to tick the "install proprietary software/download 3rd party software" option when installing?
Yes, I believe I did. I also checked for any new drivers post-install.

I have now done a full update and upgrade. No joy :(

Searching on the web, I have seen some random posts saying install windows to enable/configure touchpad using thinkpad tools or some such thing I wiped this disk and now only Ubuntu is installed here. Can ubuntu do this, or do I have to go back to Windows which I don't really want to.

---

### Post by bigmeme2 on 2021-01-01
> **veloo said:**
> Touchpad was not working while installing Ubuntu.

This laptop has a trackpoint between the keyboard which is working but I find it hard to use.


Yes, I believe I did. I also checked for any new drivers post-install.

I have now done a full update and upgrade. No joy :(

Searching on the web, I have seen some random posts saying install windows to enable/configure touchpad using thinkpad tools or some such thing I wiped this disk and now only Ubuntu is installed here. Can ubuntu do this, or do I have to go back to Windows which I don't really want to.

Hmm, I think your ISO file is corrupted, or it is a hardware issue. I would run a checksum on your ISO. I think it was a bad idea to install Ubuntu since the live boot did not work with the mouse. If you wiped windows, you are stuck, unless you can get a new ISO file on a new machine. Just for a check, press the keys, [CTRL]+[ALT]+[T]. A terminal should come up. Type: "sudo dmesg". Once you enter your password, look at the output of dmesg. Is there any red text or any error flags? If there are, post them here and I will look at it.

---

### Post by veloo on 2021-01-01
iso is not corrupted. sha256 tests ok.

Yes I can see some red text and error messages in dmesg: pastebin below link
[https://termbin.com/wp4y]("https://termbin.com/wp4y")

I also see some rfkill input handler enabled/disabled messages.

Sometimes mouse pointer seems to move on it's own. That stops after a while.

---

