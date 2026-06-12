---
title: "Has anyone Succesfully Replaced the HP MINI MIE OS w/ uBuntu???"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by Geister on 2009-06-21
I have the HP MINI running their version of Linux which is a "bastardized" version of uBuntu. Has anyone succesfully replace their version of linux with uBuntu 9.04??? Is so,  is there a "How to" or can you please post how you did it (assuming you made it work) so I can duplicate your efforts.

Thanks in advance for you help

---

### Post by jpaulb on 2009-06-22
I bought one today, would be happy for not to find out how to add apps of my choice

---

### Post by Geister on 2009-06-22
I believe your question belongs in another thread this thread is SPECIFICALLY for replacing the HP Mini MIE OS with uBuntu.

> **jpaulb said:**
> I bought one today, would be happy for not to find out how to add apps of my choice

---

### Post by jnorman000 on 2009-06-26
I would be interested in this and a simple search didn't seem to turn up much.

I think I just fried my little new MIE because at 1st I was going to try a Win7 beta install for a few days to see what it would look like for our user base.... then next week try a ubuntu.

turns out the win7 fried it so all i get on startup now is "Error 17" and so I tried burning the netbook ready .img to a 4gb cruzer micro and all it does is flash on and off when i boot the MIE and nothing comes up but a cursor...

so i may be completely SOL for the moment, but would like to help out if I can to make this a success.

thanks.  -jn

---

### Post by Geister on 2009-06-28
Okay,

Here is an update

I was able to install UNR on the HP MINI 1000 and everything works EXCEPT sound!
The Network issue that is reported as a bug seems to be fixed. But the sound is still a big issue.

First, I notice you can't compile ALSA source code, you can run ./configure no problem, but always die when you type sudo make. (AND YES I HAVE ALL DEPENDENCIES).

I have tried all the posted fixes so far as well as the alsa-assistance module download someone posted, still no sound from speak or head phones....

Another problem I found on the boards the most of the HP MINI fixes are for the PPA model, but the HP MINI uses a LPIA cpu so I would greatly appreciate if anyone has a fixed for the sound.

Also as another note, don't use the 2.6.24-19-lpia kernel on the HP MINI 1000 the video and network does not work.

---

### Post by aysiu on 2009-06-28
I created a special remix of Ubuntu (with sound fixes):
[http://www.psychocats.net/hpminiremix](http://www.psychocats.net/hpminiremix)

---

### Post by Geister on 2009-06-28
I Have an HP Mini 1000 your download page says 1120nr model? Will this be safe on my model?


> **aysiu said:**
> I created a special remix of Ubuntu (with sound fixes):
[http://www.psychocats.net/hpminiremix](http://www.psychocats.net/hpminiremix)

---

### Post by aysiu on 2009-06-28
> **Geister said:**
> I Have an HP Mini 1000 your download page says 1120nr model? Will this be safe on my model?
I don't know.

I've tested it only on the 1120nr.

Since it is a live/installer "CD," you can test it by "burning" it to a USB stick with [UNetBootIn](http://lubi.sourceforge.net/unetbootin.html) and rebooting with the stick still in (you may have to hit F9 at bootup).

If the sound works, it may be worth installing.

---

### Post by Geister on 2009-06-30
Everything works EXCEPT the Bluetooth on the my WiFi Controller, I have tried to install the bluetooh drivers /o any success....

So right now it is choose between no sound or give up all my ability to print to my BT printer and use of onther BT peripherals....

Do you have the fix to get the BT/WiFi combo card working on the HP Mini??

> **aysiu said:**
> I don't know.

I've tested it only on the 1120nr.

Since it is a live/installer "CD," you can test it by "burning" it to a USB stick with [UNetBootIn]("http://lubi.sourceforge.net/unetbootin.html") and rebooting with the stick still in (you may have to hit F9 at bootup).

If the sound works, it may be worth installing.

---

### Post by zaak on 2009-08-08
My mini1017TU is initial with XP OS. I installed ubuntu 9.04 netbook remix on an external 16G usb stick following [remix install intro]("https://help.ubuntu.com/community/Installation/FromImgFiles"). Maybe it will helpful. 

Yesterday, I transfered to MIE on SSD (XP was erased). It's lpia kernel ubuntu 8.04. It works nice for me. apt-get, pdkg and gcc compiler will give more customs optimization. So I wondered why to move to ubuntu 9.04 remix again?

---

