---
title: "Bluetooth keyboard contested by Gatsy &amp; Windows"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by arigram on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: /etc/default/bluetooth [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The three variables:

- Ubuntu 7.10 Gutsy Gibbon
- Windows XP Pro SP2
- Logitech diNovo Laser bluetooth keyboard

I have my computer set up for dual booting.
The keyboard works fine in Windows but also in Gutsy after having to remove the Gnome Bluetooth manager
 and set it up via the terminal (with another cheap wired keyboard).

The problem is that Gutsy and Windows contest the keyboard:
if I boot with one OS and reboot in the same there are no problems, but if I reboot in
the other one, the keyboard needs to be reconnected (either via SetPoint or sudo hidd -search).

This is my third reinstall of Gutsy (yes, third) and it worked fine the other times.
I am not sure what I have done wrong.
I followed the instructions of this thread:
[http://ubuntuforums.org/showthread.php?t=594624&highlight=logitech+bluetooth](http://ubuntuforums.org/showthread.php?t=594624&highlight=logitech+bluetooth)
with the necessary changes to /etc/bluetooth/hcid.conf and /etc/default/bluetooth.

Can somebody work it out with me please?

---

### Post by arigram on 2007-11-15
Ha, I thought that it would be easy to solve.

Some more information:

- Often, but not always, if I have the keyboard setup in Ubuntu, when I boot Windows, Logitech SetPoint will come up and ask me to reconnect the diNovo.
- When I connect the keyboard in Windows, it will work fine in GRUB, but not later in Ubuntu.
- When the keyboard is connect in Ubuntu, in GRUB it will only accept a few keystrokes and then nothing else.

So, there seems to be an Ubuntu configuration problem.
I still haven't got any Bluetooth GUI tools installed, should I try reinstalling them?
With a USB keyboard I use the
```
sudo hidd -search
```
command to connect the bluetooth keyboard but I have to do it every time I dual boot.

What am I doing wrong?

---

