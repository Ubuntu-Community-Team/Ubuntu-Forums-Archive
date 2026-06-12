---
title: "Asus A8N-VM CSM video and networking issues"
date: 2006-04-29
forum: Hardware &amp; Laptops
---

### Post by J0ris on 2006-04-29
Hey everybody,

I have some issues with an Asus A8N-VM CSM board. It has an Gforce 1650/ nForce 430 chipset. I also have a Compro Videomate DVB-T300 video capture card.
The issue is the following. I made a clean install of  Dapper Drake Beta. All went well except, I didn't have any networking nor was my dvb-t card recognised properly (I did  a dmesg and the relevant lines outputted a "unknown device" although it did recognise the Philips saa7134 chip)
I did a couple of cold restarts which, as expected, didn't make any difference. So I read up a bit on these forums and was about to try the sticky thread "Wired Ethernet Troubleshooting Process", only, when I just booted the system up, all of a sudden, everything was recognised. I got both networking and my DVB-t card was recognised correctly in dmesg.
Does anybody have any such experience with this board or the nForce chipset or does anybody know what is going on here? I had simular experiences with 5.10 and with Dapper testing versions, both with the dbd-t card installed and without. Unfortunately, once everything is recognised it doesn't necessarily stay in that state. Networking still went on and of although not within the same session and whether the dbd-t card was recognised or not I couldn't get it to output anything (tried Xawtv).
I have a clean install of Dapper Beta running now, didn't alter a single thing. Anybody any ideas about what may cause these instability issues?

cheers,
Joris

---

### Post by Junglizt1210 on 2006-04-29
I bascially have this motherboard, and as far as I know, the motherboard ships with the drivers on the disc.... however the drivers for the nforce 4 chipset (i.e what we need for network (therefore, internet!!)) is in a .bin format (i think, the PC is off right now)..... I tried following the instructions, but it requires the binutils (it needs this thing called "ld". So i googled it and downloaded the binutils tarball, and im trying to do the "configure" thing, but it's telling I need "cc" and won't let me proceed,

I installed Ubuntu on a test machine (the one i am posting from now) two days ago and am very impressed, but have a few issues with it on my new machine (the first being the open source nv thingy messing up and giving me gibberish, i fixed that with the help of this forum by changing it to the Vesa thingy and it worked! Thanks guys!

I want to know if I can do the "sudo apt-get install xxxxxxxxxxxx" thingy for binutils etc.

Any help would be much appreciated! This site/forum is SOOOOO helpful!!!! I've fixed several problems here!

Thank You.
Dan

---

### Post by runes on 2006-05-23
I have the exact same motherboard and have problems with the nic, audio and video.  There are at least five different "solutions" psoted but I am not sure whic one works best. If you get a solution that works for you can you email me   [email]runes@sympatico.ca[/email].  I'll keep trying till I get it to work and post the results.  Keep in mind that this is day two of my migration from windows server 2003.

---

### Post by brimbleshoes on 2006-06-14
I have this board--

for LAN
use ndiswrapper (on the CD if its not installed) and the ndis driver for the 6100 (it works, I'm using it now to post here)  Can't remember where I found it, but just search for the ndis driver for the 6150 or 6100.  Using on ubuntu -- started with kubuntu.  let me know if you can't find the driver -- I still have it...somewhere....

---

### Post by warriorx99 on 2006-07-04
I tried doing like it was suggested to do the ndiswrapper.  I installed the ndiswrapper from the Ubuntu desktop CD and downloaded this driver:

[http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/fattach_get.php?p_sid=ic5tNX1i&p_tbl=9&p_id=25&p_created=1141061119&p_olh=0](http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/fattach_get.php?p_sid=ic5tNX1i&p_tbl=9&p_id=25&p_created=1141061119&p_olh=0)

That was the only driver I could find.  I ran the following as root:

# ndiswrapper -i /home/me/ndis/oemsetup.inf
Installing oemsetup
# ndiswrapper -l
Installed ndis drivers:
oemsetup     invalid driver!

Even if it worked, I don't know if I would know the proper steps to take after that?  Could you please elaborate on what solution actually resolved this?  I'm eager to get internet access on what is my first install of ubuntu!

Thank you!

-Shane

---

### Post by brimbleshoes on 2006-12-12
be sure and include the .inf file that you have for the driver as the arguement to install it.

BTW -- this same board works great on Edgy, with no need for NDIS wrapper.  Just be sure and check for IPv6 settings and DNS.  If you use a cheaper router (like I have) these will give you problems.  Scour the forums for these issues, thats how  I found the solution.

---

