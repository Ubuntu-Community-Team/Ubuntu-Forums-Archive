---
title: "Wireless card needs to be turned on in Windows for it to work in Ubuntu"
date: 2008-08-19
forum: Hardware
---

### Post by Faethin on 2008-08-19
I have this issue in which, in order to use my wireless network adapter, I have to turn it on using Windows (by pressing fn+f10, f10 having a little icon on it with an antenna). If I don't turn it on in Windows, Ubuntu simply ignores it. Not even pressing fn+10 does it start the wireless adapter.

On a peculiar note, if I do turn on the adapter in Windows and then turn it off by pressing fn+10 *using Ubuntu* the adapter shuts down, but I can't turn it back on.

My wireless network card is a Realtek RTL8187 Wireless USB2.0 Network Adapter.

Thanks in advance.

---

### Post by sergiom99 on 2008-08-20
what happens if you start/restar it from command line?
In a console type:

```
 sudo /etc/init.d/network start 
```
or restart

If theres an error, please post the output.
Good luck!

---

### Post by Faethin on 2008-08-20
Thank you for your response.

I entered the command line and the output was this:

sudo: /etc/init.d/network: command not found

If the adapter is turned on in Windows, restarting Ubuntu doesn't seem to affect it; it still works after rebooting. It is only if I turn the computer off that the adapter ceases work in Ubuntu and needs to be turned on in Windows.

---

### Post by loboc on 2008-08-20
well did you look in /etc/init.d and see if network exists its s script that starts the network manager daemon and takes start stop or restart as input strings,

Anyway my advice is to go look in the bios and see if you can permanetly put the card on, i mean how often do you need to turn it off 

you fly alot using th laptop on the plane? 

Use the laptop on battery with it plugged into a ethernet jack?

Do alot of work on battery that doesnt involve the network?

Turn it on permentently in the bios if you can

---

### Post by sergiom99 on 2008-08-20
> **Faethin said:**
> 
I entered the command line and the output was this:

sudo: /etc/init.d/network: command not found


well, maybe is 
```
sudo /etc/init.d/networking start
``` (restart)
I am not on my laptop now.

---

### Post by Faethin on 2008-08-20
My computer's BIOS is a complete waste of space. I can do nearly nothing from it. There is no option to turn on permanently the USB adapter, at least not that I've found.

I tried entering that command line and I got

 Configuring network interfaces... [ok]

But still no wireless.

:(

---

### Post by Daelyn on 2008-08-21
> **Faethin said:**
> I have this issue in which, in order to use my wireless network adapter, I have to turn it on using Windows (by pressing fn+f10, f10 having a little icon on it with an antenna). If I don't turn it on in Windows, Ubuntu simply ignores it. Not even pressing fn+10 does it start the wireless adapter.

On a peculiar note, if I do turn on the adapter in Windows and then turn it off by pressing fn+10 *using Ubuntu* the adapter shuts down, but I can't turn it back on.

My wireless network card is a Realtek RTL8187 Wireless USB2.0 Network Adapter.

Thanks in advance.

There is a manufacturer specific program installed on your machine that interfaces with a Hardware switch in BIOS/USB hub.
WHen you press FN+F10 that port is activated, and vice versa.

At the moment, I don't think there is a program for linux that can do that for you. Remember, it is open source, and many manufacturer will be very resistant to releasing their code or specs to the open source market. I feel fairly certain it is a Advent laptop you have?

---

### Post by Ayuthia on 2008-08-21
You might try this:
[http://ubuntuforums.org/showthread.php?p=2901884](http://ubuntuforums.org/showthread.php?p=2901884)

It is for the pci card, but the problem is similar.

---

### Post by Faethin on 2008-08-22
Thank you all for your help!

The last post, by Ayuthia, actually made me think I had fixed the problem, but still no luck. I know the USB adapter can me permanently turned on (since a friend of mine managed to do it, by sheer luck. But she doesn't remember how >_<)). Any ideas how to do this from Windows?

---

