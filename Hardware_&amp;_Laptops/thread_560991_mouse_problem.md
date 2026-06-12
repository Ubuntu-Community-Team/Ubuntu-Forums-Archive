---
title: "mouse problem"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by ppchun on 2007-09-27
Hi 

I've installed ubuntu 7.0.4 on my laptop (toshiba a100(cell stuff))
everything is ok .. 
but only mouse is issued now..

mouse(generic usb) is going down within 5-10 min...
and stuck...
swithching usb port and unplug/pug mouse didn't work 


but my synoptics touch pad is working good ..
I don't have any ideas "how can i fix this.."

please help..!!

---

### Post by lisati on 2007-09-27
Note: this thread isn't really for the Apple PPC forum

I have a Toshiba A100 and had the exact same problem, which also affects a usb keyboard. The solution that worked for me was as follows:

1. From the terminal (on Applications->accesories) type in:
```

sudo gedit /boot/grub/menu.lst

```
and then type in your password (don't worry if it doesn't show - it's still getting registerd) and press "enter" - an editor window should now open

2. Scroll down to the line which reads
> 
# defoptions=quiet splash

3. Change it to read
```

# defoptions=quiet splash acpi=force irqpoll

```
4 Save the file and exit the editor
5. back from the command line, type in
```

sudo update-grub

```
6. Reboot the system

No problems since.

---

### Post by Perfect Storm on 2007-09-27
Thread moved

---

### Post by ppchun on 2007-09-27
lisati..
  Thanks a lot..

 your reply was right information for me ^^..

uhm can I ask something? what is irqpoll? 

ps: Thanks to move my post tp right position.. ^

---

### Post by geraldm on 2007-09-27
There are two types in interrupt service, hardware sending a signal when ready, the hardware
interrupt, and a polling of the hardware.  When polling is used, there is no hardware signal
sent when the device is ready; it waits for the driver to poll the hardware, and then responds.
irqpoll directs that poll be used, and an interrupt request line and hardware interrupt is not 
to be used.  

Gerald

---

### Post by Leviel on 2007-10-19
Thanks, I'll also try this one.  I've noticed that the main culprits for this USB-disconnecting [bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/84762") seem to be Dells and Toshiba A100's.  I myself am one of the Toshibas.  Wonder why?  Does it perhaps indicate generic BIOS-problems for those two?

---

