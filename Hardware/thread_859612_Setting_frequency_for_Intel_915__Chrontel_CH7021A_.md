---
title: "Setting frequency for Intel 915 / Chrontel CH7021A (50Hz PAL)"
date: 2008-07-14
forum: Hardware
---

### Post by javine on 2008-07-14
Hi,

I'm trying to get Mythbuntu up and running on a media centre machine, driving a UK TV. I'm pretty sure that the problems I'm having are down to getting the video card to drive it at 50Hz.

Symptoms:

The problem presents itself like this - Mythfrontend works fine. If I close Mythfrontend to get to the desktop then that works fine too. But as soon as I click on MythTV's "Watch TV" button the screen starts to roll, and the only way to get it back is to restart X (Ctrl-Alt-Bksp).

The setup within MythTV and the Mythbuntu Xorg Config app both only allow 640x480 @ 60Hz, but as I'm in the UK my TV should be PAL at 50Hz.

Someone on the MythTV IRC channel suggested that this sounds like an issue that I need to get setup in the OS rather than with MythTV. He suggested that the TV is just about able to sync to 60Hz for fairly stable pictures like Myth Frontend and the desktop, but falls over on the moving pictures that "Watch TV" throws at it.

System:

The system is a Media Centre box called "Scaleo E", with a built in SCART output. The chipset is Intel 915 with Chrontel CH7021A as the TV encoder. (The TV encoder board also hasa Chrontel CH7312 chip on it, if that's any hint. I'm pretty sure that the 915 is the right chip - the board has "915" in big screen printing on it. I'm certain about the Chrontel chips as I read their numbers right off the chips themselves.)

I bought the box as a barebones system, hoping to get it running Linux instead of Win MCE. I've not used Linux before at all, but I'm happy to try messing around with xorg.conf if that'll work - especially now I've worked how to get GRUB to drop me to a text prompt so I can put it back to rights with VIM if I break something!

It's a recent download of Mythbuntu, which I think is just Ubuntu with XFCE window manager plus MythTV and some MythTV customisation.

The TV is just a standard def PAL TV in the UK.

Let me know if there's any more information I can provide that would help. Any pointers are very gratefully received. Apologies if I've missed any help files or pages I should have read about this - I've done the usual Googling to no avail, but I'm very happy to follow instructions off a web page if they're out there.

Thanks,
Jim

---

### Post by adonet on 2008-07-15
Hi Jim

I have some suggestions:
did you try to watch some mpg file with this system? Does that work?
Did you activate the proprietary driver for your videocard? It can be done from the mythbuntu control centre.
Did you try to install ubuntu 8.04 instead and then install mythbuntu on top of it?
Dont make  any other direcory for the live TV files in your backend setup. If it has problems with writing permissions things may go wrong too.

success

Jeroen

---

### Post by javine on 2008-07-16
Thanks for the suggestions Jeroen. I've tried some of the things you've suggested, and could use a feew more pointers.

I grabbed a .avi file from my Windows box. Ubuntu correctly recognised it as a media file and associated it with MPlayer. As soon as I opened it the screen rolled - same result as 'Watch TV' in Myth, so I think that confirms it as an OS issue rather than a MythTV issue. (I tried playing the same file in VLC to double check - same result.)

I used the 'Launch Restricted Drivers Manager' button in Mythbuntu Control Centre - it says 'No proprietary drivers are in use on this system.' I can't see any buttons to use proprietary drivers. I have checked the Software Sources and it does have 'Proprietary drivers for devices (restricted)' checked.

I'd rather not reinstall if I can avoid it, because it took ages to get the tuner card recognised. I'm very happy to add any other packages etc if anyone can point me in the direction of ones that might help.

I've not made any changes to the MythTV directory structures or anything like that.

Thanks again for helpful tips. Do let me know if I can provide any information that might be helpful.

---

### Post by percivjr on 2009-05-16
I have a Fujitsu-Siemens Scaleo E (Intel 915 chipset) with a CH7312 (ADD2) adaptor.

I cannot get TV Out to work.

If I connect a TV to either the SCART or S-VIDEO outputs and re-boot, I see a picture until the Mythbuntu loading screen has finished, then the screen goes black.

I am in the UK, so using the PAL-I system.

Does anybody have this configuration working, please? Any tips would be appreciated, especially a sample xorg.conf file.

Thanks.

---

### Post by Vitani on 2009-08-08
Don't suppose anyone has gotten this working have they? I'm doing my best to get a working xorg.conf on my SCALEO box, but so far it's been fruitless.

Any advise would be appreciated!

---

### Post by tuppe666 on 2009-08-27
I am using a ScaleoE with the scart adapters but am only getting 480i currently so no 576i goodness. I am using Karmic. You need to use nomodeset but otherwise its great. The latest update with pulseaudio breaks sound so hold off any updates post alpha4.

#edit/etc/default/grub
#add nomodeset to it
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
#execute
update-grub2

Everything works including the TV card.. If you need any help with the scaleo do not hesitate to post me a nudge and I will add it to this forum thread

---

