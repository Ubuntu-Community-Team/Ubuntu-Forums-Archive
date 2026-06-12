---
title: "ACER Aspire 5730z - Ubuntu 8.10 Intrepid Ibex"
date: 2008-12-31
forum: Hardware
---

### Post by manolomanolo on 2008-12-31
Hi to all.

I suppose I have some compatibility issues, maybe not with Ubuntu kernel itself but with the sound system and with the graphic system.

It happens that the ubuntu startup music doesn't play correctly sometimes (but it also happened on some other kinds of laptop) and the speakers seems to emit very low sound even if Volume Control slide bars are on top levels.

Moreover sometimes Ubuntu is not able to complete the loading of the desktop environement, giving me no chance to see what the problem is: nothing happens pressing ALT-F2 or any oter ALT-Fnumber key. Nothing happens pressing CTRL+ALT+BackSpace.

[COLOR="Red"]**EDIT**.
VIDEO: sometime I'm unable to get back from suspend/hybernate.

AUDIO: sound levels are all high, but integrated speaker volume is very low. Windows XP on the same machine hasn't got this kind of problem. No problems even when using headphones or external speakers. Also, when starting gnome, the initial ubuntu music is not played perfectly (it "jumps"). I have never had this problem when restarting gdm through ALT+BACKSPACE or after a correct resuming after suspending/hybernating.[/COLOR]

Thanks for your time.
Regards.


> manolo@manolo-acer:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
manolo@manolo-acer:~$ 


I'm attaching my dmesg, I'm unable to copy/paste it here getting the following error:
> 
The following errors occurred with your submission:

   1. You have included 18 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

      Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

[DMESG.TXT]("http://files.meetup.com/224547/dmesg.txt")

---

### Post by manolomanolo on 2008-12-31
Also I'm unable to wake the system up from Suspend.

---

### Post by manolomanolo on 2009-01-01
Do you need any other info?

---

### Post by manolomanolo on 2009-03-19
Still no answers?

---

### Post by augh on 2009-03-24
I see nobody answered :( Unfortunately I haven't got the solution but can only add my problem:
my sister's aspire 5720 doesn't record sounds from the internal mic nor from any external one.
No other problems with sound.

Tell me two things:
1. how can I help you? (I'll post the lspci later)
2. does your microphone work? did you try skype?

bye,
augh

---

### Post by manolomanolo on 2009-04-05
I don't know how you colud help me.

I still have got those problems. Actually my situation got better trying different devices with Volume Control applet.

---

### Post by tripundra on 2009-04-13
Hey!

I have installed 8.10 in a Aspire 5720z and have numerous problems....I convinced a frind not ot use the original Vista, he was happy... but wants it working.:mad:

The wireless doesn't work, the webcam and the sound only works sometimes...
It also has problems returning from hibernation/sleep.

Do you know the way to put them to work?


I heard that Mandriva works with no problems on these laptops.
But I'm used to Ubuntu!!!

thanks

P.S:
I have a Macbook and the good thing is the thread that tells you to put everything to work perfectly. there should be one for this laptop!!

---

### Post by manolomanolo on 2009-04-13
Hola tripundra. ):P

In some days **Ubuntu 9.04** will come out. Try installing it and see if something changes. I do hope so.

In the meanwhile, you could try to update your system through
 **System** -> **Administration** -> **Update Managers** and see if something changes.
Then, as for wireless, please try **WICD**. The official website is unavailable at this moment, so please try downloading WICD from:
[http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=659059](http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=659059)

the official website is:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

The installation is very very simple, here there's a link in Italian language:
[http://www.italianbloggers.it/linux-installare-wicd-con-e-senza-connessione-ad-internet/](http://www.italianbloggers.it/linux-installare-wicd-con-e-senza-connessione-ad-internet/)

maybe you want to find some similar link in Spanish language.

As for webcam install **CHEESE** from repository. **CAMORAMA** should not work, as fas as I can remember, but you could try this too.

As for audio, you could try killing PULSEAUDIO process or even uninstalling PULSEAUDIO package. Also you can try having a chat with someone helping you on some ALSA irc channel. To do that I use CHATZILLA firefox add-on, connect to freenode server. Please take a look at this paga and to comments too:
[http://onlyubuntu.blogspot.com/2008/11/fix-for-no-sound-issue-in-ubuntu-810.html](http://onlyubuntu.blogspot.com/2008/11/fix-for-no-sound-issue-in-ubuntu-810.html)

As for hybernate/suspend somethimes I have this problem too.

Hope it helps, please make us know!

---

