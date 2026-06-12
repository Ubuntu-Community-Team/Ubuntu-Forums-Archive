---
title: "Wireless networking"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by ALumsden on 2005-10-23
I have the intel IPW2200 wireless card on my laptop.  The card is configured and active in the network settings but in reality it doesn't work.  Iwconfig says radio is off and the kernel message say:
IPW2200: radio frequency kill switch is on

How do I turn the kill swith off??

---

### Post by precinto on 2006-04-09
Hi, I have the same problem here. I found it may be solved by intalling acer-hk... but i'm so newbie that i don't even know how to install it... i read the install file in the acer-hk tgz, but didn't figured it out... besides it constantly give me messages saying i aint got permission for doing whatever operation i'm trying to do and it's hard for me to discover the correct shell commands. someone could give me a hand?
thanks.

---

### Post by macca87 on 2006-07-29
Hi,
if you are getting the error that you do not have permission to perform certain commands you need to place "sudo" in front of that command. It means super user do, and gives you admin like privileges.

As with radio kill switches fixed by acerhk:
In the acerhk install you will need to run a command called "make install", type "sudo make install" and this will run the command with admin privileges. Also after installing acerhk by running "./configure" << i think, cant remmeber if you need this step (see the install readme) then "make" then "sudo make install" you will need to run "sudo modprobe acerk" this will load the driver into the kernel.

Now that it is loaded you should be able to write commands directly to the device that acerhk controlls. eg "echo 1 > /proc/driver/acerhk/wirelessled" will turn on your wireless ipw card.
"echo 0 > /proc/driver/acerhk/wirelessled" will turn it off.

'echo 1' just means send the character 1 to output, but since i redirected the output by using ">" it redirects the 1 to the file 'wirelessled'. This is in fact telling the device to turn on.
I'm a newbie too stick at it man!!

Hope this helps

---

