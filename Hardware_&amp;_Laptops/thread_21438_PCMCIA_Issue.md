---
title: "PCMCIA Issue"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by Romu on 2005-03-22
Hi all,
I'm completely newbie to Linux, coming from the MS world, but I've successfully installed Warty and now Hoary on my DELL Inspiron 8600c with ATI Radeon 9600 Pro.

All seems to perfectly works expect I can't use the CF card of my digital camera. When I plug it into the PCMCIA to CF adapter, I can hear 2 beeps, and nothing more happens. This problem occurs with Warty and Hoary.

Any solution ?

Thanks.

---

### Post by Romu on 2005-03-23
Nobody can help me to solve the problem ??

Thanks.

---

### Post by Polymira on 2005-03-24
what SHOULD happen, is it should be mounted as a USB Mass Storage Device, and automagically and icon should appear on your desktop, as which happens when i plug in my ipod ....

But since it's pcmcia ... i'd like to see a dmesg....

Go ahead and boot up your linux box without the card plugged in, then plug it in, open a terminal, and type in "dmesg" without quotes ... and copy / paste the last 10 lines into a reply.

---

### Post by Romu on 2005-03-29
Done, here is the output of the dmesg command and I understand quitre ...nothing.

I've also tried the command (found on the net):
/dev/hde1 /cflash vfat defaults,user,noauto 0 0

But the output is "no such file or directory".

Any help would be greatly appreciated.

---

### Post by Whiffle on 2005-03-29
[QUOTE=Romu]Done, here is the output of the dmesg command and I understand quitre ...nothing.

I've also tried the command (found on the net):
/dev/hde1 /cflash vfat defaults,user,noauto 0 0

But the output is "no such file or directory".

Any help would be greatly appreciated.[/QUOTE]

From the looks of that dmesg its not seeing the pcmcia card.  What kind of card is it?  and do you have any other ways to plug the compactflash card in? 

 When I plug my Nikon in it pops right up on the desktop and works as a flash drive.

---

### Post by Romu on 2005-03-29
This is an anonymous (no brand) CF to PCMCIA adapter.

For me, the automouting works well for CD, DVD and USB keys, but not for CF card. I've tried to boot with the card plugged, to hotplug it...with all my cards (Sandisk Ultra 256 MB, Ultra II 1 GB and standard 48 MB) and I always get the 2 bips (sounds like a system error) and nothing more.

Is there any adapter Linux compatible ?

---

### Post by sMell on 2005-03-29
[QUOTE=Romu]Is there any adapter Linux compatible ?[/QUOTE]

The PC card adapter doesn't do anything but connect the CF pins to the PC-card pins (no chips), so it's your CF card that's the issue.

Assuming your pcmcia bridge is working, which it may not be.  Wha'ts the output of "cardctl status" and "cardctl ident"?

Also, "Two high beeps indicate that a card was identified and configured successfully. A high beep followed by a low beep indicates that a card was identified, but could not be configured for some reason. One low beep indicates that a card could not be identified. " from [http://snow.nl/dist/htmlc/ch04s04.html](http://snow.nl/dist/htmlc/ch04s04.html)

---

### Post by Romu on 2005-03-30
Thanks for this iseful answer.

I've discovered some interesting things :
- if I get only one beep, nothing special happens, I can't access the card,
- if I get 2 beeps or 3 beeps (when 3, the third one happens longer after the 2 first ones), the /var/log/messages file contains :
Mar 29 21:44:07 localhost kernel: hde: SanDisk SDCFB-48, CFA DISK drive
Mar 29 21:44:07 localhost kernel: ide2 at 0x100-0x107,0x10e on irq 3
Mar 29 21:44:07 localhost kernel: hde: max request size: 128KiB
Mar 29 21:44:07 localhost kernel: hde: 93952 sectors (48 MB) w/1KiB Cache, CHS=734/4/32
Mar 29 21:44:07 localhost kernel:  /dev/ide/host2/bus0/target0/lun0: p1
Mar 29 21:44:07 localhost kernel: ide-cs: hde: Vcc = 3.3, Vpp = 0.0
Mar 29 21:44:07 localhost kernel: hde: SanDisk SDCFB-48, CFA DISK drive
Mar 29 21:44:07 localhost kernel: ide2 at 0x100-0x107,0x10e on irq 3
Mar 29 21:44:07 localhost kernel: hde: max request size: 128KiB

In that case, the card is a SanDisk 48 MB.

So I've tried to mount something ("mount /dev/hde1 /cflash vfat defaults,user,noauto 0 0"), but I get "Permission not allowed" even if I use the root terminal. But honestly I don't know what to mount. My accouny is member of the "plugdev" group and the root account too.

I've also seen all that stuff corrupts a little bit my system which can't afterwards mount a simple USB key, this things works very well normally.

Always, any help is greatly appreciated.

Tonight I'll test the pc card commands.

---

### Post by Romu on 2005-04-03
Excuse me to disturb again.

When I plug my CF Card into the PCMCIA reader (it's now better with the Hoary RC), I get the following lines into the /var/log/messages :

Apr  3 18:24:06 localhost kernel: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Apr  3 18:24:06 localhost kernel: hde: SanDisk SDCFH-1024, CFA DISK drive
Apr  3 18:24:07 localhost kernel: ide2 at 0x100-0x107,0x10e on irq 3
Apr  3 18:24:07 localhost kernel: hde: max request size: 128KiB
Apr  3 18:24:07 localhost kernel: hde: 2001888 sectors (1024 MB) w/1KiB Cache, CHS=1986/16/63
Apr  3 18:24:07 localhost kernel:  /dev/ide/host2/bus0/target0/lun0: p1
Apr  3 18:24:07 localhost kernel: ide-cs: hde: Vcc = 3.3, Vpp = 0.0
Apr  3 18:31:26 localhost kernel:  /dev/ide/host2/bus0/target0/lun0: p1

Now I don't know what is the exact mount command to type to get access to my CF card.

Thanks for your help.

---

### Post by sMell on 2005-04-03
[QUOTE=Romu]
Now I don't know what is the exact mount command to type to get access to my CF card.

Thanks for your help.[/QUOTE]

Try

mount /dev/hde1 /some-directory-that-must-exist

---

### Post by Romu on 2005-04-29
Ok it's works, I can now see the content of the card  :-P 

But 2 problems remain :  :???: 
- how can I configure Ubuntu to auto-mount the CF card when inserted ?
- I only get the read rights, how can I get the write access ?

Thanks.

---

### Post by jorns on 2005-07-24
I have the same problem with my pcmcia compact flash reader card.
During installation of Ubuntu i choose to manually partion my harddisk and the strangest thing is that my compact flash card shows up as /dev/hde, but after installation it disapear. 
When i stick it in nothing happens in /var/log/messages, and nothing happens in dmesg. 
But when i run  'cardctl status' this happens:
[B]Socket 0:
  no card
Socket 1:
  3.3V 16-bit PC Card
  function 0: [ready][/B]
And when i run 'cardctl info' this shows up:
[B]PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="SanDisk"
PRODID_2="SDP"
PRODID_3="5/3 0.6"
PRODID_4=""
MANFID=0045,0401
FUNCID=4[/B]


 How can i fix this, i know my sandisk card works under Linux, i have used it with Fedora and with Ubuntu with a kernel wich not ends with -386 or -686.

Here is also my dmesg with the card in the pcmcia slot: 


Please help.

thx in advance.
jorn

thanks in advance

---

### Post by jorns on 2005-07-24
[QUOTE=jorns]I have the same problem with my pcmcia compact flash reader card.
During installation of Ubuntu i choose to manually partion my harddisk and the strangest thing is that my compact flash card shows up as /dev/hde, but after installation it disapear. 
When i stick it in nothing happens in /var/log/messages, and nothing happens in dmesg. 
But when i run  'cardctl status' this happens:
[B]Socket 0:
  no card
Socket 1:
  3.3V 16-bit PC Card
  function 0: [ready][/B]
And when i run 'cardctl info' this shows up:
[B]PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="SanDisk"
PRODID_2="SDP"
PRODID_3="5/3 0.6"
PRODID_4=""
MANFID=0045,0401
FUNCID=4[/B]


 How can i fix this, i know my sandisk card works under Linux, i have used it with Fedora and with Ubuntu with a kernel wich not ends with -386 or -686.

Here is also my dmesg with the card in the pcmcia slot: 


Please help.

thx in advance.
jorn

thanks in advance[/QUOTE]

Ok, i fixed it. Dont need any help.
The problem was that i had a cardmgr allready running. i killed it and Jabadabadoooohh it showed up in dmesg.

Problem solved.  \\:D/

UPDATE:
Not realy, i rebooted and the same thing happend again, and now it wouldnt work again. No cardmgr process either.
This is so strange, i realy need help.

jorns

---

