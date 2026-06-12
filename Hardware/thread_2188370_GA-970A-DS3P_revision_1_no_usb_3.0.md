---
title: "GA-970A-DS3P revision 1 no usb 3.0"
date: 2013-11-16
forum: Hardware
---

### Post by ozcyto on 2013-11-16
Enabling iommu in the bios will fix the Ethernet issue and make the usb 2.0 ports work for Gigabyte 970 chipset board GA-970A-DS3P rev 1.0, but usb 3.0 ports will no longer work on the back of the motherboard or from the internal 20 pin connector for the front panel.  I have tried Ubuntu 12.04 LTS and 14.04 with the same result.  If there is anyone else in the same boat please post up.

---

### Post by ozcyto on 2013-11-18
Here is my updated fix

First enable iommu in the uefi by restarting your computer and pressing delete to enter the uefi

plug your usb mouse, keyboard and thumbdrive in usb 2 ports.

save and exit the uefi

Then In Ubuntu:

press Ctrl+Alt+T to open up a terminal 

run the following command: sudo gedit /etc/default/grub

Only edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"

save changes to grub and exit gedit and the terminal

Open up a new terminal with ctrl+alt+t 

run the following command: sudo update-grub

then exit the terminal using this command: exit

Restart your computer press delete to get back into the uefi

Disable iommu in bios, load optimized defaults and restart.

usb, 2.0 usb 3.0 and networking all work now in Ubuntu, and disabling iommu in bios may also help improve your boot times. 

If the above post helps anyone I am happy.

---

### Post by beaucoder2 on 2014-04-21
Hey Ozcyto!!!

It also works on the Gigabyte 970A-UD3P motherboard. Fixed both USB 2.0 adn 3.0. 

How did you discover this??  I spent three days trying to figure out what was wrong.

Thanks a bunch,

Ken Wagner
Sugar Creek, Missoui
Where life is sweet, mostly.

---

### Post by ozcyto on 2014-05-02
[**[COLOR=#000000]beaucoder2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1844801") im glad it worked for you.  

I recently started using the same motherboard gigabyte ud3p and the fix worked for me as well.  I figured Iommu was correcting the same problem with uefi and other board brands so i figured i would try using a software iommu instead of hardware iommu and it worked.

---

### Post by john254 on 2014-08-05
Wow ozcyto, your a genius!!!
I've been trying and trying to get usb 3 and my Ethernet connection to play nicely together and your solution is so easy and.. just works.
Thanks a lot!

---

### Post by lma-gru on 2014-08-13
> **ozcyto said:**
> Here is my updated fix...
....
usb, 2.0 usb 3.0 and networking all work now in Ubuntu, and disabling iommu in bios helps prevent windows freezes that was occurring if you are running a dual boot environment. 
If the above post helps anyone I am happy.


**GA-970A-UD3P revision 1 no usb 3.0, or no USB 2.0.**
Solve my problem with you post. Thank you you very much!

---

### Post by mickhogan on 2014-08-21
Thanks [COLOR=#DD4814][COLOR=#000000][ozcyto]("http://ubuntuforums.org/member.php?u=1881925")!!  Fixed the board, just like you said.  I'm Happy!![/COLOR][/COLOR]

---

### Post by Jens_Schwarz on 2014-11-21
THANK YOU VERY MUCH !!!!
things can be so easy.

---

### Post by cybertrail on 2014-12-27
> **ozcyto said:**
> 
If the above post helps anyone I am happy.

This was an awesome and quick fix to something that has been an issue for me for some time.  THANKS!  Be happy!

(I used your method to fixed my Gigabyte 970A-UD3P running Xubuntu)

---

### Post by spieleraaron on 2014-12-28
OMFG !

Thank you sooo so much, i mean, i spent sooo much time on figuring out what the problem was with my system. First the LAN was not working, so after a bit of research i turned on the IOMMU-controller and then the usb3-ports weren't working. And then i found your post. OMG thank you soo much, you made my day. BTW how the f... did you figure this out, i mean really, how?

THX Aaron

---

### Post by cbarsoum on 2014-12-31
Thank you so much, without your suggestion I would have been still digging, thank you

---

### Post by abitwise on 2015-03-18
Hello, I have AMD motherboard Gigabyte 970A-UD3P (AMD 970) with FX 8320 processor. I also had problem where depending on BIOS settings I could enable/disable USB 3.0 and USB 2.0 with onboard networking, but could not get USB 3.0 to work in Linux (Ubuntu 14.04 LTS).

I have complete working solution for you (with Grub):
Edit Grub config:
> sudo nano /etc/default/grub
Edit the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash libdata.force=noncq"
Add "amd_iommu=on iommu=pt" to the end of it, line now looks like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash libdata.force=noncq amd_iommu=on iommu=pt"
Update grub:
> sudo update-grub
And now, reboot the system
Go to the BIOS and make sure you have IOMMU=Enabled, Also make sure USB and USB3 controllers are enabled, EHCI and XHCI handoffs are enabled and USB Legacy support is Auto. Also I enabled USB ports 60/64 emulation, not sure if it affects anything, did not try to turn it off.
And now system starts up, no more 10-15 second lag, USB 3.0 works like a charm, USB 2 keyboard, mouse, webcam also work nicely. I hope this helps anyone. iommu=pt means kernel uses the hardware solution, soft is not the "real thing".

---

### Post by allartk2 on 2015-04-30
Thanks a lot!!!

---

### Post by am. on 2015-05-31
So I have spent a week trying to get my wifi to work on a new ubuntu setup. 
Assuming it was the wifi driver (rt2x00) I have been trying out loads of different things, like using different drivers (that would not compile as they where written in 2010 and are now just bundled in with rt2800pci/rt2x00) At least I think that's why they didn't compile (something about CFLAGS). 
Checking dmesg got a lot of 
'ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush'

The wifi (which detected networks ) would attempt to connect but just never did.

So took the computer to the router to use an ethernet connection so I could work out the problem some more and found my onboard ethernet port wasn't working.
After a week it took me till today to realise that it might be the motherboard and this post fixed that. 
I just wanted to add that extra information as it seems other people had a similar problem to me and also were going through hoops thinking there was a fault with their wireless drivers when it seems to be at least in my case something to do with the motherboard.

Thank you so much !

---

### Post by marco68 on 2016-04-14
Thank you **ozcyto! ** You are my hero! :P

---

### Post by fziegenf on 2016-04-21
> **ozcyto said:**
> Here is my updated fix

First enable iommu in the uefi by restarting your computer and pressing delete to enter the uefi

plug your usb mouse, keyboard and thumbdrive in usb 2 ports.

save and exit the uefi

Then In Ubuntu:

press Ctrl+Alt+T to open up a terminal 

run the following command: sudo gedit /etc/default/grub

Only edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"

save changes to grub and exit gedit and the terminal

Open up a new terminal with ctrl+alt+t 

run the following command: sudo update-grub

then exit the terminal using this command: exit

Restart your computer press delete to get back into the uefi

Disable iommu in bios, load optimized defaults and restart.

usb, 2.0 usb 3.0 and networking all work now in Ubuntu, and disabling iommu in bios may also help improve your boot times. 

If the above post helps anyone I am happy.

Thank you for this very helpful fix for usb 3.0 on my gigabyte mb. What a relief to finally have hi speed transfers. Perfect!

---

### Post by dtr2 on 2016-06-04
Thanks, that fixed it for me!

---

### Post by steingrimurs on 2016-06-28
Did purhase a GA-970A-DS3P rev 2 a week ago and have been struggeling to get it working with USB2 and USB3.   Now after trial end error it is working, though I have not testet the actual speed of the USB3 ports.
-------------------------
Did shange /etc/default/grub > GRUB_CMDLINE_LINUX="iommu=pt" > grub-mkconfig ..
==========
Then the bios .. Did flash the bios with the newest 2016 from gigabyte website.
----------------------
Bios settings ..
         ========  Bios features ========
Os type  ........                                  Other Os
Boot mod edition ........                  Legasy only
Storage boot conrole ..                 Legasy first
Other Pci Devices Rom Priority    Legasy OpRom

         ======== Periperals  =========
On ship Sata controllers ....          Enabled
On ship Sata type  ..........               Ahci
On ship Sata Port 4/5 type ..         As Sata
Hd Audio Azalia device ....            enabled
On board usb device .....               enabled
On board lan ....                              disabled
Legasy support .............                 enabled
Xhci Hands-off .....                          enabled
Ehci Hands-off ...                           enabled
Port 60/64 emulation                    disabled
Iommu Controller ...                      disalbed

Seems to work .. finger krossed ..

---

### Post by sasha-weijand on 2016-08-09
should all the usb2-ports be occupied? I had two of them occupied (one with a flash drive),
and afterwards all the usb2-ports stopped working, and also my ethernet port stoppped working. The front usb3-port seemed to work though.
The funny thing was that the front usb2-port still recognized my flash drive, but not when I connected a mouse to it instead. 
I read in some threads that it works better with 32bit ubuntu and that it has to do with some problem with linux 64 bit kernels not being compatible.

---

### Post by sasha-weijand on 2016-08-10
steingrimurs: I did everything you said except flash the bios (wasn't sure which revision I had so I didn't dare) and disable on board lan controller (my internet connection disappeared when I tried), and now both usb3 and usb2 works! Thanks :)

---

### Post by concil on 2016-11-30
Works for Gigabyte 990x Gaming Sli Motherboard.
Thanks you!

---

### Post by 2e0pgs on 2017-03-14
[SIZE=3]**Ok so for anyone with "GIGABYTE GA-970A-DS3" I have done alot of testing and research. The best config I found to get USB3 working is this:**[/SIZE]
Edit Grub config:
`[COLOR=#000000]*sudo nano /etc/default/grub`*[/COLOR]
Edit the line that looks like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Add "amd_iommu=on iommu=pt" to the end of it so now the line now looks like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amd_iommu=on iommu=pt"
Update grub:
`[COLOR=#000000]*sudo update-grub`*[/COLOR]
once you have done that reboot the system and hit DEL / Delete key to enter BIOS/EUFI setup:
Ensure IOMMU is enabled,  XHCI handoff is enabled, EHCI handoff is disabled, USB Legacy support is enabled. OS type I have set to Windows8 but I have CSM enabled "Compatibility Support Module" so Linux will boot via BIOS emulation instead of UEFI.

This fix allowed my USB3 to work properly and fixed a few audio issues.

For bonus fix if your running a x64 bit Ubuntu and find USB transfers hang at the end apply this fix:
[https://unix.stackexchange.com/questions/107703/why-is-my-pc-freezing-while-im-copying-a-file-to-a-pendrive/107722#107722](https://unix.stackexchange.com/questions/107703/why-is-my-pc-freezing-while-im-copying-a-file-to-a-pendrive/107722#107722)

This is working on Ubuntu 16.04.2, Kernel: x86_64 Linux 4.4.0-66-generic

---

### Post by sorgud on 2017-04-23
Thank you, ozcyto !!
It works for me... I spent 2 days looking for an answer why the wired connection with a fixed IP wasn't working. I've already had other computer working (same distro (Kubuntu 16.10), same router... The dhcp was working, but when I put to static IP didn't work. I changed cables... everything... after I read this whole thread I focus on the router... I had forgotten that, two years ago, I select, in the router, the fixed IP to the MAC addresses. Thus as I had changed MO (and processor) it was a different MAC address and the router didn't allow the connection!
Finally I run in the problem that I had no USB 3 ports working... and I followed your instructions and work like a charm! with the grub line (=soft)
(previously, at the beginning I couldn't install Kubuntu from a usb-stick, I had to enable IOMMU  to be able to install from a USB-stick

Everything is working now! 
Now I can start working!!!!
**Thank you again, ozcyto**!!!

---

### Post by nsby7c on 2017-08-14
> **ozcyto said:**
> Here is my updated fix

First enable iommu in the uefi by restarting your computer and pressing delete to enter the uefi

plug your usb mouse, keyboard and thumbdrive in usb 2 ports.

save and exit the uefi

Then In Ubuntu:

press Ctrl+Alt+T to open up a terminal 

run the following command: sudo gedit /etc/default/grub

Only edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"

save changes to grub and exit gedit and the terminal

Open up a new terminal with ctrl+alt+t 

run the following command: sudo update-grub

then exit the terminal using this command: exit

Restart your computer press delete to get back into the uefi

Disable iommu in bios, load optimized defaults and restart.

usb, 2.0 usb 3.0 and networking all work now in Ubuntu, and disabling iommu in bios may also help improve your boot times. 

If the above post helps anyone I am happy.


I just want to give you a kiss! I've been messing with this off and on for months, and this finally worked like a charm!

---

### Post by Lambertus on 2018-06-30
ozctyo.

You saved me so much time and headache. Thank you very very much. It worked with the new GA-970A-DS3P board to get the USB2 ports working with Ubuntu 18.04. The USB3 ports worked with install.

Bert
Vancouver, BC

---

### Post by negro9719 on 2018-10-09
Thank you so much guys. It is working for me with the Rev 1.0 mb, and the F2j BIOS using abitwise's method. Thank you!!

---

