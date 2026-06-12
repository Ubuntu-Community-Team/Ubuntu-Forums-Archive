---
title: "Wifi on Compaq Presario R3000"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by ton.boelens on 2005-10-16
Hi,

Has anyone got the wireless LAN option on the Compaq Presario R3000 working under Ubuntu 5.10?

I would be great to hear how you did this!

Ton

---

### Post by tseliot on 2005-10-16
I think you should install the restricted modules according to your kernel and architecture in Synaptic/kynaptic.

---

### Post by ton.boelens on 2005-10-16
How?

---

### Post by fezzik on 2005-10-18
I finally did get it working. Using some help I got in some forums.
I used the disk containing the back up drivers for windows that came with my computer.  I copied the bcmwl5a.inf and the corresponding files with the a.  I have a Presario r3440US with the INtel PIV.  You can try this with the bcmwl5a.inf and with the bcmwl5.inf if the a one doesn't work.  But the one without the a didn't work for me.  The light wouldn't come on but worked like a dream with the a.  Follow the following directions and you should be good.

3. Open a terminal session and enter this code. Note that you need an active network connection for this to work; I've assumed that if you have access to a wireless LAN, you also have access to a wired network as a fallback.sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done4. Reboot your PC. On restarting, the light on your wireless card should come on. If not, try enteringsudo modprobe ndiswrapper5. Your card is now working. Open the networking configuration tool System --> Administration --> Networking

6. Select your wireless network card (probably wlan0) and hit the properties button.

---

### Post by ton.boelens on 2005-10-18
Thanks a lot for your explanation. I will try it soon.

---

### Post by ton.boelens on 2005-10-19
I still have not succeeded to get the wlan working. When I do ndiswrapper -l, the screen reads:

Installed ndis drivers:
bcmwl5a driver present, hardware present

also, the kernel module is loaded:

root@laptoptb:~# lsmod | grep ndis
ndiswrapper           148692  0

but when I try to administer the settings of the networkcard by System, Administration (I am not sure what the English term is), Network, I see only eth0 and ppp0, not wlan0...

What do I do wrong?

Thanks, 

Ton

---

### Post by fezzik on 2005-10-20
You might try using the bcmlw5 instead of a.  I will see if I can find the rest of the instructions and I will post them.  It might help you.

---

### Post by fezzik on 2005-10-20
Don't forget after you reset to go back in and type sudo modprobe ndiswrapper.

For me that was very important.  Also you want to make sure you have all the files associated with the driver before you wrap it.  Like for bcmwl5a.inf you want to get that pnk or whatever just in the same directory.  It isn't needed except I think that the inf pulls info from it.  If you try the non a version which may be the problem both drivers are on the disk.  So some have one others use the other.  I had to redo mine.  I messed something up playing with some settings and couldn't get back into the computer.  So I reinstalled and had to set up the wifi again and it worked like a charm and those that I posted here were the only instructions I had available.  

Have you gotten the touch pad working right?

---

### Post by hw-tph on 2005-10-21
You might want to head over to the [Linux R3000 wiki](http://prinsig.se/weekee) and read up on the [networking section](http://prinsig.se/weekee/index.php/Networking_%28hw%29#Wireless).


Håkan (yes, I own that site)

---

### Post by ton.boelens on 2005-10-22
That's it! Because I was using the AMD64 version of Ubuntu, I had to use the Broadcom driver. Now I've got it working. Thanks alot guys for helping me along.

Ton

---

### Post by fezzik on 2005-10-24
Glad we could help one Newbie to another.  I am glad it is working.  I have gotten to fix all kinds of things and I am loving Ubuntu so far.

---

### Post by fon on 2005-11-06
hp-tph,thanks
I have like 15 print out of wireless card ,I'm going to look for "IIRC" in the card ,I'll let you now

---

### Post by The_night on 2005-11-10
I am using kubuntu, and I cannot figure out how to do that last step that says "sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile"  It says Bash: $conffile: ambigious redirect... somone please help!

---

### Post by artan on 2005-11-16
Hi, 

I have a problem with my Presario 3000 laptop. I can actually open the advance to view the available networks, but I cannot see any (while the others next to me do).Somebody told me that I might have decreased the strength of the frequency I can reach the network to, but I cannot find anything about the wireless when going to Boot option at the beginning.

Has anybody faced a similar problem? and can anyone help?

thanx.

artan

---

### Post by nocturn on 2005-11-16
[QUOTE=ton.boelens]
but when I try to administer the settings of the networkcard by System, Administration (I am not sure what the English term is), Network, I see only eth0 and ppp0, not wlan0...

What do I do wrong?
[/QUOTE]

You need to check if ndiswrapper is loaded, but in addition, check if your antenna is turned on (there should be a hardwarebutton for that).

Can you see it with iwconfig?

---

### Post by hw-tph on 2005-11-16
[QUOTE=fon]I will thanks if some body can tell me WHICH internal mini pci card is compatible w/compaq presario r 3000 z[/QUOTE]

You cannot just replace the mini-pci card on a r3000/zv5000/nx9105 series computer from HP/Compaq because the BIOS has a whitelist of selected cards to accept. The cards accepted are, IIRC, all different Broadcom chips. This means we cannot replace the unsupported Broadcom card with one that has real drivers. Thank you HP... :mad: 


Håkan

---

### Post by fon on 2005-11-17
I write in wrong place ,just read FON post #1 again to see wat are you thing,
thank agian,

---

### Post by kozmo on 2007-12-15
> **hw-tph said:**
> You might want to head over to the [Linux R3000 wiki](http://prinsig.se/weekee) and read up on the [networking section](http://prinsig.se/weekee/index.php/Networking_%28hw%29#Wireless).

Håkan (yes, I own that site)
bogus link :-(

---

### Post by voteforpedro36 on 2007-12-15
> **kozmo said:**
> bogus link :-(


... this thread is from 2005.

---

